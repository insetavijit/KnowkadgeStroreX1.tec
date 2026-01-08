| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC2.3.1.1 What Is RunnableWithFallbacks]]**       | Define fallback concept                      | RunnableWithFallbacks class, backup chains, error recovery                      | RunnableWithFallbacks provides backup chains on failure.            |
| **[[LC2.3.1.2 Fallback Concept]]**                    | Understand backup execution                  | Primary fails, secondary executes, cascading fallbacks                          | Fallbacks execute when primary chain fails.                         |
| **[[LC2.3.1.3 Primary vs Fallback Chains]]**          | Distinguish roles                            | Primary chain, ordered fallbacks, execution priority                            | Primary executes first; fallbacks only on failure.                  |
| **[[LC2.3.1.4 Use Cases]]**                           | Identify fallback scenarios                  | Model unavailability, rate limits, degraded service                             | Use fallbacks for model failures and rate limits.                   |
| **[[LC2.3.1.5 Fallback Benefits]]**                   | Summarize advantages                         | Reliability, availability, graceful degradation                                 | Fallbacks improve reliability and availability.                     |

# RunnableWithFallbacks: The Backup Generator

Production systems must **Never Crash**. They must degrade gracefully.
LCEL provides `.with_fallbacks()` to define what happens when the primary path **Fails**.

---

## 1. The Core Abstraction

`.with_fallbacks()` wraps any Runnable. If the wrapped runnable raises an exception, LangChain catches it and tries the next item in the list.

```python
from langchain_openai import ChatOpenAI
from langchain_anthropic import ChatAnthropic

primary = ChatOpenAI(model="gpt-4")
backup = ChatAnthropic(model="claude-3-sonnet")
emergency = ChatOpenAI(model="gpt-3.5-turbo")

resilient_llm = primary.with_fallbacks([backup, emergency])
```

**Execution Flow**:
1.  Try `gpt-4`.
2.  If `gpt-4` times out (OpenAI Down) -> Try `claude-3-sonnet`.
3.  If `claude-3-sonnet` also fails -> Try `gpt-3.5-turbo`.
4.  If all fail -> Exception propagates.

---

## 2. What Triggers a Fallback?

By default, **Any Exception** triggers a fallback.
*   `openai.RateLimitError` -> Fallback.
*   `httpx.TimeoutException` -> Fallback.
*   `pydantic.ValidationError` -> Fallback.

**Customization**:
You can filter which exceptions trigger the fallback.

```python
resilient_llm = primary.with_fallbacks(
    [backup],
    exceptions_to_handle=(openai.RateLimitError,)
)
```

This means: Only switch if it's a rate limit. For other errors (e.g., invalid API key), crash immediately and alert the developer.

---

## 3. Architectural Role: The Reliability Layer

Fallbacks should be thought of as a **Quality Spectrum**.

| Tier | Provider | Quality | Cost | Role |
| :--- | :--- | :--- | :--- | :--- |
| **Primary** | GPT-4 | Best | $$$$ | Standard Operation. |
| **Fallback 1** | Claude-3 | Good | $$$ | OpenAI down. |
| **Fallback 2** | GPT-3.5 | OK | $ | Degraded. |
| **Fallback 3** | Hardcoded | Minimal | Free | Catastrophic. |

---

## Quick Reference

| Method | Behavior |
| :--- | :--- |
| `.with_fallbacks([a, b])` | On error, try `a`. If `a` errors, try `b`. |
| `.with_retry(...)` | On error, try *the same thing* again. |
