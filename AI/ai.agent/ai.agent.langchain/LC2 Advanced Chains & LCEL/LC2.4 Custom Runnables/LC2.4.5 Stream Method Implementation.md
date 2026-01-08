| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC2.4.5.1 Implementing Stream]]**                 | Code stream method                           | def stream(self, input, config), generator function                             | Implement stream() as a generator yielding outputs.                 |
| **[[LC2.4.5.2 Yielding Outputs]]**                    | Emit incremental results                     | yield keyword, partial results, progressive output                              | Use yield to emit results incrementally.                            |
| **[[LC2.4.5.3 Generator Patterns]]**                  | Use generator best practices                 | Generator functions, iteration, memory efficiency                               | Use generator patterns for memory-efficient streaming.              |
| **[[LC2.4.5.4 Streaming Considerations]]**            | Handle streaming challenges                  | Buffering, ordering, completeness, cleanup                                      | Consider buffering and cleanup in streaming.                        |
| **[[LC2.4.5.5 Non-Streaming Runnables]]**             | Handle non-streamable operations             | Single-yield pattern, stream compatibility                                      | Non-streaming runnables yield single result.                        |

# Stream Method: Token-by-Token Output

Streaming is critical for UX. Nobody wants to wait 10s for a blank screen, then see the full answer.

---

## 1. The Signature

```python
def stream(
    self,
    input: Input,
    config: Optional[RunnableConfig] = None
) -> Iterator[Output]:
    ...
```

It returns an **Iterator**. The caller loops over it, receiving partial results.

---

## 2. A Simple Implementation

```python
class WordByWordSplitter(Runnable[str, str]):
    def stream(self, input, config=None):
        for word in input.split():
            yield word + " "
    
    # invoke() returns the full string
    def invoke(self, input, config=None):
        return input
```

**Usage**:
```python
for chunk in splitter.stream("Hello World"):
    print(chunk, end="")  # Prints "Hello " then "World "
```

---

## 3. Wrapping Non-Streaming APIs

Some APIs don't support streaming. You can still implement `stream`, but it's "fake streaming" (one big `yield`).

```python
class BlobFetcher(Runnable[str, bytes]):
    def stream(self, input, config=None):
        # Not real streaming, but compatible with the interface
        yield self.invoke(input, config)
```

This allows downstream consumers that *expect* a Generator to work, even if there's only one chunk.

---

## Quick Reference

| Method | Output Type | Use Case |
| :--- | :--- | :--- |
| `invoke` | `T` | Full result at once. |
| `stream` | `Iterator[T]` | Progressive UI updates. |
| `astream` | `AsyncIterator[T]` | Async progressive UI. |
