| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC1.4.6.1 Defining Input Keys]]**                 | Specify chain inputs                         | input_keys property, required inputs, key validation                            | Define input_keys to specify what data the chain expects.           |
| **[[LC1.4.6.2 Defining Output Keys]]**                | Specify chain outputs                        | output_keys property, returned data, multiple outputs                           | Define output_keys to specify what data the chain returns.          |
| **[[LC1.4.6.3 Key Mapping Between Chains]]**          | Connect chain outputs to inputs              | Key renaming, mapping dictionaries, transform wrappers                          | Map output keys to input keys when chaining.                        |
| **[[LC1.4.6.4 Variable Naming Conventions]]**         | Follow consistent naming                     | Clear names, namespacing, avoiding conflicts                                    | Use clear, consistent key names across chains.                      |
| **[[LC1.4.6.5 Debugging Key Mismatches]]**            | Fix key-related errors                       | KeyError diagnosis, verbose mode, key inspection                                | Debug key mismatches using verbose output and inspection.           |

# Input/Output Keys: The Data Schema

In any distributed system, the **Schema** is the contract.
In LangChain, the Schema is defined by the keys in the state dictionary.

If Chain A outputs `text` and Chain B expects `summary`, the pipe will explode.
Understanding **Key Propagation** is the difference between "It works on my machine" and "It works in production."

---

## 1. Implicit vs Explicit Contracts

### Legacy (Implicit)
Old chains (`LLMChain`) had "Magic Keys."
*   Input default: `text` (or the single variable in prompt).
*   Output default: `text`.

This caused "Key Collisions" in sequential chains. If Chain A wrote to `text` and Chain B wrote to `text`, data was overwritten.

### Modern (Explicit)
In LCEL, you manage the keys manually using `RunnablePassthrough` and `itemgetter`.

```python
from operator import itemgetter

# Explicitly selecting 'question' from the input dict
chain = (
    {"context": retriever, "question": itemgetter("user_input")}
    | prompt
    | model
)
```

---

## 2. The `Pick` and `Assign` Pattern

In a complex flow, your dictionary grows:
`{id: 1, user: Bob, q: Hi, ...}`.

You need to perform **Key Surgery**:
1.  **Pick**: Select only what the sub-chain needs (Privacy/Validation).
2.  **Assign**: Add the result back to the stream (Enrichment).

```python
from langchain_core.runnables import RunnablePassthrough

# Scenario: Chain expects 'topic', but we have 'user_query'
chain = (
    # 1. Alias (Renaming)
    RunnablePassthrough.assign(topic=lambda x: x["user_query"])
    | prompt 
    | model
)
```

**Why `.assign()`?**
It preserves the original data! If you just used a `map`, you would lose `user_query`. `.assign()` creates a new dictionary `Original + New Keys`.

---

## 3. Handling Multi-Output Chains

Some chains (like `RunnableParallel`) output multiple keys.

```python
parallel_chain = RunnableParallel(
    summary=summary_chain,
    tags=tagging_chain
)
# Output: {'summary': '...', 'tags': ['a', 'b']}
```

If the *next* step in your pipeline expects a string, it will crash receiving this dictionary.
You must use a **Selector**.

```python
final_chain = (
    parallel_chain
    | (lambda x: f"Summary: {x['summary']}\nTags: {x['tags']}") # Formatting Step
    | email_writer_chain
)
```

---

## 4. Debugging `KeyError`

The most common error in LangChain:
`KeyError: 'text' not found in input variables`.

**The Fix Checklist**:
1.  **Check the Prompt**: Does your `{variable}` match the dictionary key exactly?
2.  **Check the Previous Step**: Did the previous runnable return a String or a Dict?
    *   *Hint*: `StrOutputParser` returns a String (No keys!).
    *   *Hint*: `JsonOutputParser` returns a Dict.
3.  **Inspect with `.input_schema`**:
    Modern Runnables have a `.input_schema` method that generates a Pydantic model description of what they expect.

```python
print(chain.input_schema.schema())
```

---

## Quick Reference

| Operation | LCEL Syntax | Purpose |
| :--- | :--- | :--- |
| **Rename** | `.assign(new_key=old_col)` | Mapping `user_q` -> `topic`. |
| **Keep All**| `RunnablePassthrough()` | Forwarding all data to next step. |
| **Select** | `itemgetter("key")` | Extracting a single value. |
| **Merge** | `RunnableParallel` | Merging concurrent outputs into one dict. |
