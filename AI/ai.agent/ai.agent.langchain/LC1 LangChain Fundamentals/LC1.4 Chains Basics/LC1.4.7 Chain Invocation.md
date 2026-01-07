| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC1.4.7.1 Run vs Invoke]]**                       | Choose invocation method                     | Legacy run(), modern invoke(), method differences                               | Use invoke() for modern chains; run() is legacy.                    |
| **[[LC1.4.7.2 Passing Inputs]]**                      | Provide data to chains                       | Dict inputs, keyword arguments, input validation                                | Pass inputs as dictionaries to chain invoke().                      |
| **[[LC1.4.7.3 Getting Outputs]]**                     | Retrieve chain results                       | Output dict, accessing keys, parsing results                                    | Chain outputs are dictionaries with defined keys.                   |
| **[[LC1.4.7.4 Batch Execution]]**                     | Run chains on multiple inputs                | batch() method, parallel processing, batch limits                               | Use batch() to run chains on multiple inputs efficiently.           |
| **[[LC1.4.7.5 Async Execution]]**                     | Run chains asynchronously                    | ainvoke(), abatch(), asyncio integration                                        | Use ainvoke() for async chain execution.                            |

# Chain Invocation: The Runnable Interface

You have built the machine (The Chain). Now you need to turn it on (The Invocation).
In LangChain, "Turning it on" is standardized by the **Runnable Protocol**.

Every object in LangChain implements this standard interface, meaning a `Prompt`, a `Model`, a `Chain`, and a `Retriever` can all be executed effectively the same way.

---

## 1. The Standard Interface

| Method | Sync | Async | Description |
| :--- | :--- | :--- | :--- |
| **Invoke** | `.invoke(x)` | `.ainvoke(x)` | Single input, single output. |
| **Batch** | `.batch([x, y])` | `.abatch([x, y])` | Multiple inputs, List of outputs (Parallel). |
| **Stream** | `.stream(x)` | `.astream(x)` | Single input, Iterator of chunks. |

### Legacy Confusion (`.run`, `.apply`, `.call`)
In the old days (`LLMChain`), every class had its own method names.
*   `chain.run()`
*   `chain.apply()`
*   `chain.predict()`

> **Architectural Rule**: Do not use these methods. They are wrappers that hide the explicit Input/Output types. Use `.invoke()` everywhere.

---

## 2. Batch Execution (Parallelism for Free)

A common pattern: You have a list of documentation chunks and you want to summarize all of them.

**The Loop Way (Slow)**:
```python
results = []
for doc in docs:
    results.append(chain.invoke(doc)) # Serial execution 1-by-1
```

**The Batch Way (Fast)**:
```python
# Runs in threadpool automatically!
results = chain.batch(docs)
```

**Configuration**:
You can control the concurrency to avoid Rate Limits.

```python
chain.batch(docs, config={"max_concurrency": 5})
```

---

## 3. Streaming (The UX Necessity)

Chains are composed of parts. When you call `.stream()`, LangChain automatically finds the part of the chain that *supports* streaming (usually the LLM) and yields its tokens.

```python
# Even if the chain has a Retriever and a Prompt...
chain = retriever | prompt | model | output_parser

# ... this iterator yields tokens from the Model
for chunk in chain.stream("Explain Quantum Mechanics"):
    print(chunk, end="", flush=True)
```

**Architectural Note**:
Non-streaming steps (like Retrieval) fully complete *before* the stream starts. The stream is not "end-to-end" unless every component is a generator (which is rare).

---

## 4. Async Execution (Scalability)

In Web Apps (FastAPI, Django), you must never block the main thread.
Sync calls (`invoke`) block. Async calls (`ainvoke`) yield control.

```python
# FastAPI Endpoint
@app.post("/chat")
async def chat_endpoint(request: Request):
    # Allows server to handle other requests while waiting for OpenAI
    response = await chain.ainvoke(request.json())
    return response
```

**Warning**: Do not mix sync and async.
*   Defining `async def` and calling `chain.invoke()` (sync) inside it blocks the event loop.
*   Always use the `a-` prefix methods inside async functions.

---

## Quick Reference

| Goal | Method |
| :--- | :--- |
| **Simple Run** | `chain.invoke({"topic": "AI"})` |
| **List Processing** | `chain.batch([{"topic": "AI"}, {"topic": "ML"}])` |
| **Visual Feedback** | `chain.stream(...)` |
| **Web Server** | `await chain.ainvoke(...)` |
