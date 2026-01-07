| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC1.4.4.1 Data Transformation in Chains]]**       | Transform data mid-chain                     | Non-LLM transformations, data reformatting, type conversion                     | TransformChain applies Python functions to chain data.              |
| **[[LC1.4.4.2 Custom Transform Functions]]**          | Write transformation logic                   | Function signature, input_keys, output_keys, transform callable                 | Define transform functions with clear input/output keys.            |
| **[[LC1.4.4.3 Preprocessing]]**                       | Prepare data before LLM                      | Cleaning, formatting, validation, normalization                                 | Use TransformChain to preprocess data before LLM calls.             |
| **[[LC1.4.4.4 Postprocessing]]**                      | Process LLM output                           | Format conversion, extraction, enrichment, cleanup                              | Use TransformChain to postprocess LLM outputs.                      |
| **[[LC1.4.4.5 Non-LLM Chain Steps]]**                 | Add logic without LLM calls                  | Pure Python logic, API calls, database queries in chains                        | TransformChain enables non-LLM steps in pipelines.                  |

# TransformChain: The Logic Layer

> [!TIP]
> **Modern Equivalent**: `TransformChain` (Legacy) -> `RunnableLambda` (Modern).

In a mature AI system, 40% of the code is LLM calls. The other 60% is **Data Glue**.
*   Truncating text to fit context windows.
*   Formatting dates.
*   Enriching user objects with DB data.

Use **Transformation Layers** to keep your Prompts clean and your Models focused.

---

## 1. The Legacy Class (`TransformChain`)

In version 0.0.x, LangChain wrapped Python functions in a rigid class structure.

```python
# THE OLD WAY
def truncate_text(inputs: dict) -> dict:
    text = inputs["text"]
    return {"truncated_text": text[:100]}

transform_chain = TransformChain(
    input_variables=["text"],
    output_variables=["truncated_text"],
    transform=truncate_text
)
```

**The friction**: You had to manually declare input/output variables, doubling the boilerplate.

---

## 2. The Modern Functional Pattern (`RunnableLambda`)

In LCEL, any Python function *is* a Chain.
You wrap it in `RunnableLambda` (or let LangChain coerce it automatically).

```python
# THE PROFESSIONAL WAY
from langchain_core.runnables import RunnableLambda

def truncate(text: str) -> str:
    return text[:100]

# Usage in a pipe
chain = (
    RunnableLambda(truncate) 
    | prompt 
    | model
)
```

### Complex Input Handling (Dictionaries)
If your function needs to access multiple keys from the stream:

```python
def calculate_age(inputs: dict) -> dict:
    birth_year = inputs["dob"].year
    age = 2024 - birth_year
    return {"age": age}

chain = (
    RunnableLambda(calculate_age) # Injects 'age' into stream? NO. 
                                  # It REPLACES the stream with {'age': X}
    | prompt
)
```

**Architectural Awareness**:
`RunnableLambda` assumes **replacement** by default.
If you want to **append** to the dictionary (keep `dob` and add `age`), you must use `RunnablePassthrough.assign()` wrapping your lambda.

---

## 3. Pre-Processing Patterns

The most common use case is "Context Sanitization."
If you just shove a PDF into a prompt, you break the token limit.

```python
def sanitizer(inputs):
    # 1. Remove HTML tags
    clean = remove_html(inputs["context"])
    # 2. Hard Truncate
    clean = clean[:4000]
    return {"context": clean}

chain = RunnableLambda(sanitizer) | prompt | model
```

By isolating this check in a Transform step, you can **Unit Test** it without mocking OpenAI.

---

## 4. Post-Processing Patterns

Models output text. Systems need objects.
While `OutputParsers` handle JSON parsing, `TransformLayers` handle **Business Logic normalization**.

*   *Scenario*: Model outputs "New York".
*   *Requirement*: Database needs `state_code: "NY"`.

```python
def normalize_state(state_name: str) -> str:
    # Lookup DB or Enum
    return STATE_MAP.get(state_name, "UNKNOWN")

chain = model | StrOutputParser() | RunnableLambda(normalize_state)
```

---

## Quick Reference

| Requirement | Legacy Tool | Modern Tool |
| :--- | :--- | :--- |
| **Simple Function** | `TransformChain` | `RunnableLambda` |
| **Add Key to Dict** | `TransformChain` | `RunnablePassthrough.assign()` |
| **Filter Data** | `TransformChain` | `RunnableLambda` |
| **Async Logic** | (Complex Wrapper) | `async def` function (Native) |
