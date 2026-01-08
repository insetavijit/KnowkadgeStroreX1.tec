| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC2.4.4.1 Implementing Batch]]**                  | Code batch method                            | def batch(self, inputs, config), list processing                                | Implement batch() for efficient bulk processing.                    |
| **[[LC2.4.4.2 Parallel Processing]]**                 | Execute items concurrently                   | Async execution, thread pools, concurrent processing                            | Process batch items in parallel for speed.                          |
| **[[LC2.4.4.3 Batch Optimization]]**                  | Optimize for efficiency                      | Vectorization, bulk operations, batched API calls                               | Optimize batch with vectorized operations.                          |
| **[[LC2.4.4.4 Handling Batch Failures]]**             | Manage partial failures                      | Exception handling, return_exceptions, result validation                        | Handle individual failures without failing entire batch.            |
| **[[LC2.4.4.5 Default Batch Implementation]]**        | Use inherited behavior                       | Default loops over invoke, override considerations                              | Default batch calls invoke; override for optimization.              |

# Batch Method: Throughput Optimization

The default `batch()` implementation just loops over `invoke()`.
Override it when you have a more efficient bulk operation.

---

## 1. Default Behavior

```python
# What the base class does:
def batch(self, inputs, config=None):
    return [self.invoke(x, config) for x in inputs]
```

This is sequential. For 100 inputs, it makes 100 API calls, one after another.

---

## 2. Optimized Override

If your backend supports bulk requests, override:

```python
class BulkEmbedder(Runnable[list[str], list[list[float]]]):
    def batch(self, inputs, config=None):
        # 1 API call for all inputs
        return embedding_api.bulk_embed(inputs)
```

**Example**: OpenAI's embedding API accepts a list of strings. Calling `embed(["a", "b", "c"])` is 3x faster than 3x `embed("a")`.

---

## 3. Concurrent Batch

If your API doesn't support bulk, but you want parallelism:

```python
import concurrent.futures

class ConcurrentFetcher(Runnable[str, dict]):
    def batch(self, inputs, config=None):
        max_workers = (config or {}).get("max_concurrency", 5)
        with concurrent.futures.ThreadPoolExecutor(max_workers) as pool:
            return list(pool.map(self.invoke, inputs))
```

This sends 5 requests in parallel, then the next 5, etc.

---

## Quick Reference

| `batch()` Strategy | Speed | When To Use |
| :--- | :--- | :--- |
| **Default** | `O(N)` | Baseline / Small N. |
| **Bulk API** | `O(1)` | Backend has batch endpoint. |
| **Concurrent** | `O(N/workers)` | I/O-bound, no bulk API. |
