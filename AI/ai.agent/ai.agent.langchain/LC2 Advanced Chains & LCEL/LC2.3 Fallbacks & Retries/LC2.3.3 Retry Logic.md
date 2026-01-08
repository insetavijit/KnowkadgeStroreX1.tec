| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC2.3.3.1 Retry Decorators]]**                    | Apply retry with decorators                  | @retry, tenacity library, decorator patterns                                    | Use @retry decorator for automatic retry logic.                     |
| **[[LC2.3.3.2 Retry Count]]**                         | Set retry limits                             | max_retries, retry budgets, preventing infinite loops                           | Limit retries to prevent infinite loops.                            |
| **[[LC2.3.3.3 Retry Delays]]**                        | Configure wait between retries               | Fixed delay, wait_fixed, delay strategies                                       | Add delays between retries to respect rate limits.                  |
| **[[LC2.3.3.4 Exponential Backoff]]**                 | Increase delays progressively                | wait_exponential, backoff multiplier, jitter                                    | Use exponential backoff for rate-limited APIs.                      |
| **[[LC2.3.3.5 When to Retry]]**                       | Identify retryable errors                    | Transient errors, network issues, rate limits                                   | Retry transient errors; don't retry permanent failures.             |

# Retry Logic: Try Again (Smarter)

**Fallback**: "Something went wrong? Try a different thing."
**Retry**: "Something went wrong? Try the *same* thing again."

Retries are for **Transient Errors** (Network Flakes, Rate Limits). Not for logic bugs.

---

## 1. The `.with_retry()` Method

```python
from langchain_core.runnables import RunnableWithRetry

llm = ChatOpenAI().with_retry(
    stop_after_attempt=3,
    wait_exponential_jitter=True
)
```

**Parameters**:
*   `stop_after_attempt`: Try N times, then give up.
*   `wait_exponential_jitter`: Wait `2^n` seconds + random noise.

---

## 2. Retry vs Fallback (When to Use Which)

| Error Type | Example | Strategy |
| :--- | :--- | :--- |
| **Transient** | `429 Rate Limit`, `503 Service Unavailable` | **Retry**. Wait and try again. |
| **Permanent** | `401 Unauthorized`, `404 Not Found` | **Fallback** (or Crash). Invalid request; retrying won't help. |
| **Semantic** | LLM returned bad JSON | **Retry** (with correction prompt) or **Fallback** (to a stricter parser). |

---

## 3. Combining Retry + Fallback

The most robust chains layer both.

```python
resilient_llm = (
    ChatOpenAI(model="gpt-4")
    .with_retry(stop_after_attempt=3)       # Step 1: Retry GPT-4 3 times
    .with_fallbacks([                        # Step 2: If still failing
        ChatAnthropic().with_retry(),        #         Retry Claude
        simple_hardcoded_response            #         Then hardcode
    ])
)
```

**Execution Flow**:
1.  Call GPT-4. Fails (Rate Limit).
2.  Wait 2s. Call GPT-4. Fails (Rate Limit).
3.  Wait 4s. Call GPT-4. Fails (Rate Limit).
4.  Retry budget exhausted. Trigger Fallback -> Call Claude.
5.  Claude works. Return response.

---

## Quick Reference

| Parameter | Default | Description |
| :--- | :--- | :--- |
| `stop_after_attempt` | 3 | Max tries. |
| `wait_exponential_jitter` | False | Smarter backoff for rate limits. |
| `retry_if_exception_type` | `Exception` | Which errors trigger a retry. |
