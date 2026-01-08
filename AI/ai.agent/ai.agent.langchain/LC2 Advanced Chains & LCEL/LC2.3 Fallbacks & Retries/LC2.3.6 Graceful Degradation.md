| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC2.3.6.1 Reduced Functionality]]**               | Operate with limitations                     | Feature degradation, core vs optional, priority features                        | Continue with reduced features when components fail.                |
| **[[LC2.3.6.2 Degraded Responses]]**                  | Provide partial answers                      | Best-effort responses, with caveats, transparency                               | Return degraded responses with clear disclaimers.                   |
| **[[LC2.3.6.3 User Communication]]**                  | Inform about degradation                     | Error messages, status indicators, expectation setting                          | Communicate degraded status clearly to users.                       |
| **[[LC2.3.6.4 Maintaining Availability]]**            | Keep service running                         | Core functionality, service continuity, uptime priority                         | Maintain availability with graceful degradation.                    |
| **[[LC2.3.6.5 Recovery Notifications]]**              | Alert when normal resumes                    | Service restoration, status updates, health checks                              | Notify when service recovers from degraded state.                   |

# Graceful Degradation: The User Experience Layer

Technical resiliency is about *keeping the code running*.
Graceful Degradation is about *keeping the user happy*.

---

## 1. The "We're Working On It" Response

A stack trace is a bad user experience. Even "Error 500" is bad.
A degraded response should be helpful.

```python
def degraded_fallback(x):
    return {
        "answer": "I'm currently experiencing high demand and cannot perform a full search. Based on my training data, I can share that...",
        "sources": [],
        "degraded": True  # UI can show a warning banner
    }
```

**Architecture**: The `degraded: True` flag allows the UI to render a yellow warning bar: "This answer may be less accurate."

---

## 2. Feature Toggling (Shedding Load)

Under heavy load, you might need to disable non-essential features.

**Example**: A chatbot with 3 features:
1.  **Core**: Answer questions.
2.  **Optional A**: Also generate a summary.
3.  **Optional B**: Also play audio.

Under stress, you can "shed" Optional A and B.

```python
if system_under_stress():
    chain = core_chain
else:
    chain = RunnableParallel(core=core, summary=summary, audio=audio)
```

---

## 3. Transparency: Telling the User

Users are more forgiving when you are honest.

*   **Bad**: "The answer is X."  (LLM hallucinated because RAG failed).
*   **Good**: "My document search is temporarily unavailable. Here's a general answer: X. Please verify this."

This is a **Trust Preserving** pattern. The user might be frustrated, but they don't lose faith in your system.

---

## Quick Reference

| Strategy | User Impact | Transparency Level |
| :--- | :--- | :--- |
| **Silent Degradation** | User notices lower quality. | Low (Bad). |
| **Flagged Degradation** | UI shows "Limited Mode". | Medium. |
| **Explicit Apology** | Message explains the issue. | High (Best). |
