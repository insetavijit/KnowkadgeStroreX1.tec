| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC2.4.2.1 Subclassing Runnable]]**                | Extend base class                            | class MyRunnable(Runnable), inheritance patterns                                | Subclass Runnable to create custom runnables.                       |
| **[[LC2.4.2.2 Implementing Required Methods]]**       | Fulfill interface contract                   | Required vs optional methods, abstract methods                                  | Implement required methods to fulfill contract.                     |
| **[[LC2.4.2.3 Custom Runnable Structure]]**           | Design runnable internals                    | __init__, instance variables, configuration                                     | Structure custom runnables with clear initialization.               |
| **[[LC2.4.2.4 RunnableLambda Alternative]]**          | Use functions instead of classes             | RunnableLambda, function wrapping, simpler approach                             | Use RunnableLambda for simple custom logic.                         |
| **[[LC2.4.2.5 @chain Decorator]]**                    | Decorate functions as runnables              | @chain decorator, decorated functions, convenience                              | Use @chain decorator for function-based runnables.                  |

# Creating Custom Runnables: Lambda vs Class

Most of the time, `RunnableLambda` is enough.
You only need to subclass `Runnable` for complex logic with state or specialized methods.

---

## 1. The `RunnableLambda` Shortcut

For simple transformations, wrap a function:

```python
from langchain_core.runnables import RunnableLambda

def add_prefix(text: str) -> str:
    return f"[PREFIX]: {text}"

as_runnable = RunnableLambda(add_prefix)

# Usage in chain:
chain = prompt | llm | as_runnable | parser
```

**Best For**: One-liners, stateless transforms, glue code.

---

## 2. The `@chain` Decorator

Even simpler:

```python
from langchain_core.runnables import chain

@chain
def add_prefix(text: str) -> str:
    return f"[PREFIX]: {text}"

# `add_prefix` is now a Runnable!
chain = prompt | llm | add_prefix | parser
```

---

## 3. When to Subclass `Runnable`

If you need:
*   **Instance State** (e.g., a database connection).
*   **Custom `batch` or `stream` logic**.
*   **Pydantic Config / Serialization**.

```python
from langchain_core.runnables import Runnable

class DatabaseLookup(Runnable[str, dict]):
    def __init__(self, db_connection):
        self.db = db_connection
    
    def invoke(self, input: str, config=None) -> dict:
        return self.db.query(input)
    
    def batch(self, inputs: list[str], config=None) -> list[dict]:
        # Optimized: Single DB round-trip
        return self.db.bulk_query(inputs)
```

**Key Detail**: The `batch` method here is smarter than the default (which just loops `invoke`). This is the power of subclassing.

---

## Quick Reference

| Approach | Complexity | Best For |
| :--- | :--- | :--- |
| `RunnableLambda(fn)` | Low | Quick transforms. |
| `@chain` decorator | Low | Function-based chains. |
| `class X(Runnable)` | High | Stateful / Optimized. |
