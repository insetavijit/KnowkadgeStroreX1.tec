| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC1.3.7.1 Validating Prompt Inputs]]**            | Check input correctness                      | Pydantic validation, type hints, custom validators                              | Validate inputs before prompt formatting to catch errors.           |
| **[[LC1.3.7.2 Required Variables]]**                  | Ensure mandatory inputs                      | input_variables enforcement, missing variable errors                            | Prompts fail fast when required variables are missing.              |
| **[[LC1.3.7.3 Type Checking]]**                       | Enforce input types                          | Type annotations, coercion, type mismatch handling                              | Check input types match expected formats before use.                |
| **[[LC1.3.7.4 Input Preprocessing]]**                 | Transform inputs before use                  | Sanitization, normalization, encoding, length limits                            | Preprocess inputs to ensure consistency and safety.                 |
| **[[LC1.3.7.5 Error Messages for Invalid Inputs]]**   | Provide helpful error feedback               | Descriptive errors, validation context, debugging hints                         | Provide clear error messages for invalid prompt inputs.             |

# Input Validation: The "Fail Fast" Architecture

The worst time to discover a bug is **after** you've paid OpenAI $0.05 for a call.
If your input is missing, or 5MB of text accidentally paste-dumped into a 4K context model, you want your application to crash **locally** and **instantly**.

LangChain prompts are not just strings; they are **Pydantic Models** in disguise.

---

## 1. Built-in Validation: Missing Variables

The most common error in AI engineering is the "Typosphere."

`template = "Hello {name}"`
`prompt.invoke({"nmae": "Alice"})`

In raw Python string formatting, this might raise a confusing `KeyError`.
In LangChain, this raises a `ValidationError` explicitly listing:
*   What was expected (`['name']`).
*   What was provided (`['nmae']`).

**Architectural Rule**: Always explicit define `input_variables` in complex templates to strictly enforce the contract, even though LangChain can infer them.

```python
template = PromptTemplate(
    template="Hello {name}",
    input_variables=["name"] # Enforces the contract
)
```

---

## 2. Advanced Validation (Pydantic Wrappers)

What if `age` must be an integer > 18?
Prompts themselves don't validate *data types*, only *presence*.
To enforce data quality, you wrap the prompt in a **RunnableLambda** or a custom **Chain**.

```python
from langchain_core.runnables import RunnableLambda
from pydantic import BaseModel, ValidationError

class UserInput(BaseModel):
    age: int

def validate_age(inputs: dict) -> dict:
    try:
        # Enforce type safety
        user = UserInput(age=inputs['age'])
        if user.age < 18:
            raise ValueError("User too young")
        return inputs
    except Exception as e:
        raise ValueError(f"Validation Failed: {e}")

# The Safe Chain
chain = RunnableLambda(validate_age) | prompt | model
```

---

## 3. Sanitization & Truncation

Validation isn't just about schemas; it's about **Physics**.
If a user pastes a 100,000-word PDF into a chat box, your app should truncat it *before* building the prompt.

```python
def truncate_inputs(inputs: dict) -> dict:
    # Hard limit to prevent context overflow costs
    MAX_CHARS = 4000 
    if len(inputs['text']) > MAX_CHARS:
        inputs['text'] = inputs['text'][:MAX_CHARS] + "...(TRUNCATED)"
    return inputs

chain = RunnableLambda(truncate_inputs) | prompt | model
```

**Why not rely on the Model's error?**
Because the model's error ("Context Length Exceeded") comes from the API Provider. It requires a network roundtrip and potentially partial processing fees. Local validation is free and instant.

---

## Quick Reference

| Validation Type | Mechanism | Purpose |
| :--- | :--- | :--- |
| **Presence** | Native `input_variables` check | Ensures keys exist. |
| **Type** | Pydantic / Logic | Ensures `age` is int, `email` is valid. |
| **Physics** | `len()` check | Prevents context window overflows. |
| **Security** | Delimiter check | Prevents simple injection attempts. |
