| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC2.3.5.1 Setting Timeouts]]**                    | Configure time limits                        | timeout parameter, request_timeout, operation-level timeouts                    | Set timeouts to prevent indefinite waiting.                         |
| **[[LC2.3.5.2 Timeout Exceptions]]**                  | Handle timeout errors                        | TimeoutError, asyncio.TimeoutError, exception handling                          | Handle timeout exceptions like other failures.                      |
| **[[LC2.3.5.3 Timeout Strategies]]**                  | Choose appropriate timeouts                  | Per-operation, global, adaptive timeouts                                        | Set timeouts based on expected operation duration.                  |
| **[[LC2.3.5.4 Long-Running Protection]]**             | Guard against hangs                          | Preventing hangs, user experience, resource limits                              | Protect long-running chains with timeouts.                          |
| **[[LC2.3.5.5 Timeout with Fallback]]**               | Combine timeout and fallback                 | Timeout triggers fallback, faster alternatives, time-aware routing              | Use fallbacks when primary chain times out.                         |

# Timeout Handling: Latency Budgets

A chain that runs forever is worse than a chain that crashes.
Timeouts ensure that slow providers don't block the entire pipeline.

---

## 1. Client-Side Timeouts (LLM Wrapper)

Most LangChain LLM clients accept a `timeout` or `request_timeout` parameter.

```python
llm = ChatOpenAI(
    model="gpt-4",
    request_timeout=30  # seconds
)
```

If OpenAI takes longer than 30s to respond, an `httpx.TimeoutException` is raised.
This exception triggers `.with_fallbacks()` or `.with_retry()` if configured.

---

## 2. The "Latency Budget" Pattern

In a microservice architecture, you have an end-to-end SLA (e.g., 5 seconds).
You must allocate this budget across your steps.

**Example**:
*   Total Budget: 5s
*   Retriever: 1s Max
*   LLM: 3s Max
*   Post-Processing: 1s Max

```python
retriever = VectorRetriever.with_config({"timeout": 1})
llm = ChatOpenAI(request_timeout=3)
```

If the retriever takes 4s, it times out, allowing the fallback to kick in *before* the overall 5s budget is exceeded.

---

## 3. Server-Side Timeouts (FastAPI)

When deploying with `lc serve`, FastAPI also has a request timeout.
If your entire chain takes too long, the client gets a `504 Gateway Timeout`.

**Pattern**: Set inner timeouts *shorter* than the server timeout.

```
FastAPI Server Timeout: 60s
├─ LLM Timeout: 30s (Triggers fallback after 30s)
└─ Fallback Timeout: 20s (Hardcoded after 20s more)
```

This ensures you *always* return *something* before the 60s server timeout.

---

## Quick Reference

| Layer | Parameter | Default |
| :--- | :--- | :--- |
| `ChatOpenAI` | `request_timeout` | 60s |
| `ChatAnthropic` | `timeout` | 600s |
| FastAPI | `--timeout-keep-alive` | Varies (Uvicorn) |
