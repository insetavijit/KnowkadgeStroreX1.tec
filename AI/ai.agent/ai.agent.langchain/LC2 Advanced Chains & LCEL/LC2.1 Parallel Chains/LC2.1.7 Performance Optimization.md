| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC2.1.7.1 When Parallelization Helps]]**          | Identify optimization opportunities          | I/O-bound operations, independent tasks, network calls                          | Parallelize I/O-bound, independent operations for gains.            |
| **[[LC2.1.7.2 Overhead Considerations]]**             | Account for parallelization costs            | Task creation overhead, context switching, memory usage                         | Consider overhead; parallel isn't always faster.                    |
| **[[LC2.1.7.3 Optimal Branching]]**                   | Choose right number of branches              | Too few vs too many, diminishing returns, resource limits                       | Balance branch count against overhead and resources.                |
| **[[LC2.1.7.4 Benchmarking Parallel Chains]]**        | Measure performance                          | Timing comparisons, profiling, metrics collection                               | Benchmark to verify parallel chains improve performance.            |
| **[[LC2.1.7.5 Optimization Best Practices]]**         | Apply performance patterns                   | Batch similar operations, minimize branch overhead, cache results               | Apply optimization patterns for best parallel performance.          |

# Performance Optimization: Batching vs Parallelism

There are two ways to speed up LLM apps. They are orthogonal.

---

## 1. Horizontal Scaling (`RunnableParallel`)

**Use Case**: You have **1 Input**, but need to do **3 Different Things**.
*   Thing A: Summarize it.
*   Thing B: Extract Keywords.
*   Thing C: Translate it.

**Mechanism**:
Browser (1 Req) -> Server (3 Tasks) -> 3 LLM Calls.

```python
chain = RunnableParallel({
    "summary": summarize_chain,
    "keywords": keywords_chain
})
chain.invoke(doc)
```

---

## 2. Vertical Scaling (`chain.batch`)

**Use Case**: You have **100 Inputs**, and need to do **1 Thing**.
*   Process 100 User Reviews.

**Mechanism**:
Browser (1 Req) -> Server (1 Task) -> **1 API Call** (if provider supports batching) or **ThreadPool**.

```python
chain = prompt | model
chain.batch([doc1, doc2, doc3])
```

**Optimization Magic**:
If you use `chain.batch`, LangChain attempts to use the provider's Batch API (e.g., OpenAI Batch API, or multiple rows in a vector store query) to reduce network round-trips.

---

## 3. Combining Them (Matrix Processing)

The ultimate throughput comes from compositing both.
You want to process **100 Reviews**, and for *each* review, run **3 parallel analysis steps**.

```python
analysis_chain = RunnableParallel({
    "sentiment": sentiment_chain,
    "topics": topic_chain
})

# Process 10 concurrent items, and for each item, run 2 concurrent branches
# Total concurrency = 20
analysis_chain.batch(docs, config={"max_concurrency": 10})
```

---

## Quick Reference

| Pattern | Input Shape | Complexity | Best For |
| :--- | :--- | :--- | :--- |
| `RunnableParallel` | `x` | `O(1)` Latency | Complex, multi-step Reasoning. |
| `chain.batch` | `[x, y, z]` | `O(N)` Throughput | Bulk Data Processing. |
| **Both** | `[x, y]` | `High` | Enterprise ETL Pipelines. |
