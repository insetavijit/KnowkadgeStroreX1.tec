| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC2.4.7.1 Using Custom Runnables in Chains]]**    | Integrate with LCEL                          | Pipe operator, composition, chain building                                      | Custom runnables work with | operator in LCEL.                     |
| **[[LC2.4.7.2 Pipe Operator Compatibility]]**         | Ensure piping works                          | __or__ method, type compatibility, chain building                               | Runnables inherit pipe operator compatibility.                      |
| **[[LC2.4.7.3 Integration Patterns]]**                | Apply common patterns                        | Pre-processing, post-processing, transformation                                 | Use custom runnables as chain components.                           |
| **[[LC2.4.7.4 Mixed Chains]]**                        | Combine custom and built-in                  | Custom + ChatModel, hybrid chains, interoperability                             | Mix custom runnables with built-in components.                      |
| **[[LC2.4.7.5 Testing Composition]]**                 | Test in chain context                        | Integration tests, chain behavior, end-to-end                                   | Test custom runnables within chain compositions.                    |

# Composition: Fitting Into the LCEL Graph

The magic of the `Runnable` interface is that once you implement it, your custom component "plugs in" to **all** LCEL primitives.

---

## 1. The Pipe Operator `|`

Because `Runnable` overloads `__or__`, you can chain it:

```python
chain = my_custom_runnable | prompt | llm | parser
```

**Semantics**: `a | b` creates a `RunnableSequence([a, b])`.
Your custom runnable's `invoke` is called first, and its output is passed to `prompt.invoke`.

---

## 2. Inside a `RunnableParallel`

```python
from langchain_core.runnables import RunnableParallel

parallel = RunnableParallel({
    "sentiment": sentiment_scorer,  # Custom
    "length": RunnableLambda(len)   # Built-in wrapper
})
```

Your custom `sentiment_scorer` runs concurrently with the `len` function.

---

## 3. Inside a `RunnableBranch`

```python
branch = RunnableBranch(
    (lambda x: x["type"] == "code", code_analyzer),  # Custom
    (lambda x: x["type"] == "text", text_analyzer),  # Custom
    default_llm                                     # Built-in
)
```

Your custom analyzers are selected based on the condition.

---

## 4. Testing the Composition

When testing, you should test:
1.  **Unit**: `my_runnable.invoke(x)` in isolation.
2.  **Integration**: `full_chain.invoke(x)` end-to-end.

```python
def test_chain_with_custom():
    chain = my_runnable | llm
    result = chain.invoke("test")
    assert "expected_output" in result
```

---

## Quick Reference

| LCEL Primitive | Custom Runnable Usage |
| :--- | :--- |
| `a | b` | Chained sequentially. |
| `RunnableParallel({})` | Runs in parallel. |
| `RunnableBranch(...)` | Selected conditionally. |
| `.with_fallbacks(...)` | Used as fallback. |
