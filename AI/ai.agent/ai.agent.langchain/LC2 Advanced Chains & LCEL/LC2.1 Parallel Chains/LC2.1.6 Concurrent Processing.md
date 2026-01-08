| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC2.1.6.1 Async Execution Under the Hood]]**      | Understand parallel mechanics                | asyncio, event loop, concurrent tasks, execution model                          | RunnableParallel uses asyncio for concurrent execution.             |
| **[[LC2.1.6.2 Thread Pools]]**                        | Manage concurrent workers                    | ThreadPoolExecutor, worker threads, pool configuration                          | Thread pools manage concurrent execution of branches.               |
| **[[LC2.1.6.3 Concurrency Limits]]**                  | Control parallelism                          | max_concurrency, resource limits, backpressure                                  | Set concurrency limits to prevent resource exhaustion.              |
| **[[LC2.1.6.4 Parallel Execution Model]]**            | Grasp execution flow                         | Task scheduling, completion waiting, result gathering                           | Branches execute as concurrent tasks in event loop.                 |
| **[[LC2.1.6.5 Synchronization Points]]**              | Understand waiting behavior                  | All-complete waiting, barrier synchronization, continuation                     | Parallel chains wait for all branches before continuing.            |

# Concurrent Processing: Threads vs AsyncIO

How does `RunnableParallel` actually run things at the same time?
It depends on how you call it: `.invoke()` or `.ainvoke()`.

---

## 1. The Synchronous Path (`invoke`)

If you are running a standard Python script (blocking):
`RunnableParallel` uses a **ThreadPool**.

```python
# Sync Call
chain.invoke("input") 
```

1.  LangChain spins up `ThreadPoolExecutor`.
2.  Branch A runs in Thread 1.
3.  Branch B runs in Thread 2.
4.  Main Thread waits for both.

**Pros**: Easy debugging.
**Cons**: Python Threads have overhead (GIL), though I/O bound tasks (API calls) release the GIL.

---

## 2. The Asynchronous Path (`ainvoke`)

If you are running in FastAPI or Jupyter:
`RunnableParallel` uses **AsyncIO**.

```python
# Async Call
await chain.ainvoke("input")
```

1.  LangChain wraps branches in `asyncio.create_task()`.
2.  Branch A and B run on the **Event Loop**.
3.  Zero OS threads are created.

**Architectural Benefit**:
You can run 10,000 concurrent LLM calls on a single CPU core because they are just "awaiting" network packets.

---

## 3. Controlling Concurrency

If you fan-out to 100 documents, you might hit OpenAI's Rate Limit.
You need a semaphore.

```python
# Set max concurrency via config
chain = RunnableParallel({...}).with_config(
    {"max_concurrency": 5}
)
```

This ensures that even if you submit 100 tasks, only 5 run at a time. The rest queue up.

---

## Quick Reference

| Method | Mechanism | Scalability | Use Case |
| :--- | :--- | :--- | :--- |
| `.invoke()` | Threads | Medium (100s) | Scripts, CLI tools. |
| `.ainvoke()` | Coroutines | High (10,000s) | Web Servers (FastAPI). |
| `.batch()` | ThreadPool | Optimizes API | Processing datasets. |
