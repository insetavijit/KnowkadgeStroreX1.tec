| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC2.4.1.1 Runnable Protocol Methods]]**           | Know all Runnable methods                    | invoke, batch, stream, ainvoke, abatch, astream, method contracts               | Runnable defines invoke, batch, stream and their async variants.    |
| **[[LC2.4.1.2 Invoke Method]]**                       | Understand core invocation                   | Single input, single output, synchronous execution                              | invoke() processes single input synchronously.                      |
| **[[LC2.4.1.3 Batch Method]]**                        | Understand bulk processing                   | List input, list output, concurrent processing                                  | batch() processes multiple inputs concurrently.                     |
| **[[LC2.4.1.4 Stream Method]]**                       | Understand streaming                         | Generator output, incremental results, real-time                                | stream() yields outputs incrementally.                              |
| **[[LC2.4.1.5 Async Variants]]**                      | Know async methods                           | ainvoke, abatch, astream, async/await usage                                     | Async variants enable non-blocking execution.                       |

# Runnable Interface: The Core Protocol

Every component in LCEL—`ChatModel`, `Prompt`, `Retriever`, `Parser`—is a `Runnable`.
This is what makes the `|` operator work.

---

## 1. The Six Methods

The `Runnable` abstract base class defines a standard interface:

| Method | Input | Output | Mode |
| :--- | :--- | :--- | :--- |
| `invoke(x)` | Single | Single | Sync |
| `batch([x])` | List | List | Sync |
| `stream(x)` | Single | Generator | Sync |
| `ainvoke(x)` | Single | Single | Async |
| `abatch([x])` | List | List | Async |
| `astream(x)` | Single | AsyncGen | Async |

**Architectural Insight**:
`invoke` is the primitive. `batch` is `invoke` on a ThreadPool. `stream` is `invoke` that `yield`s.

---

## 2. Signature: Input and Output Types

```python
from langchain_core.runnables import Runnable

class MyRunnable(Runnable[str, int]):
    def invoke(self, input: str, config=None) -> int:
        return len(input)
```

The generics `Runnable[Input, Output]` allow for static type checking.
Your IDE will know that `MyRunnable.invoke("hello")` returns an `int`.

---

## 3. The `config` Dictionary

Every LCEL method accepts an optional `config` dictionary.
This is how you pass:
*   `callbacks`: For tracing.
*   `max_concurrency`: For rate limiting.
*   `run_name`: For logging.
*   `configurable`: For per-request settings.

```python
response = chain.invoke(
    "Hello",
    config={
        "run_name": "ProductionRequest",
        "callbacks": [my_handler]
    }
)
```

---

## Quick Reference

| You Want To... | Use Method | Returns |
| :--- | :--- | :--- |
| Process 1 item | `.invoke()` | `Output` |
| Process 100 items | `.batch()` | `list[Output]` |
| Show live tokens | `.stream()` | `Iterator[Output]` |
