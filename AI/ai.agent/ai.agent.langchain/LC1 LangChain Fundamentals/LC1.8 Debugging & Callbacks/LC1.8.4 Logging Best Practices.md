| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC1.8.4.1 Python Logging Integration]]**          | Use standard logging                         | logging module, logger configuration, handler setup                             | Integrate LangChain with Python's logging module.                   |
| **[[LC1.8.4.2 Log Levels]]**                          | Set appropriate log levels                   | DEBUG, INFO, WARNING, ERROR, level selection                                    | Set log levels to control verbosity of output.                      |
| **[[LC1.8.4.3 Structured Logging]]**                  | Log structured data                          | JSON logs, key-value pairs, searchable logs                                     | Use structured logging for machine-readable logs.                   |
| **[[LC1.8.4.4 Log Formatting]]**                      | Format log messages                          | Formatters, timestamps, context inclusion                                       | Format logs with timestamps and context for readability.            |
| **[[LC1.8.4.5 Production Logging]]**                  | Log in production environments               | Log aggregation, external services, alerting                                    | Configure production logging with aggregation services.             |

# Logging Best Practices: Beyond console.log

In production (Kubernetes/Lambda), nobody looks at `stdout` manually. Use **Python's Logging Module**.

---

## 1. Capturing Internal Logs

LangChain uses the standard `logging` library under the namespace `"langchain"`.
You can capture these logs without setting `verbose=True`.

```python
import logging
import sys

# Configure standard logger
logging.basicConfig(
    stream=sys.stdout, 
    level=logging.INFO
)

# Capture ONLY LangChain warnings/errors
logging.getLogger("langchain").setLevel(logging.WARNING)
```

**Why this matters**:
`verbose=True` is noisy. It prints *everything* at the INFO level.
By configuring the logger, you can say:
*   "Show me my app's INFO logs."
*   "Show me LangChain's ERROR logs only."

---

## 2. Structured Logging (The Professional Way)

Text logs ("User X did Y") are hard to query.
**Structured Logs** are JSON objects.

```python
import structlog  # or python-json-logger

logger = structlog.get_logger()

# In your custom callback:
def on_chain_end(self, outputs, **kwargs):
    logger.info(
        "chain_finished", 
        latency_ms=400, 
        token_usage=150, 
        model="gpt-4"
    )
```

**Outcome**:
You can now query your logs in Datadog/Splunk:
`service:langchain AND latency_ms > 1000`

---

## 3. Correlation IDs

When you have 50 requests happening at once, a log saying "LLM Error" is useless. Who did it fail for?

**Pattern**:
Pass the `session_id` or `trace_id` in the `config`.

```python
trace_id = "req_12345"

chain.invoke(
    "Hello", 
    config={
        "tags": [trace_id],  # Tag the trace (LangSmith)
        "metadata": {"user_id": "alice"}  # Metadata for callbacks
    }
)
```

Your custom logging callback can then read `run_manager.metadata` and attach it to the log entry.

---

## Quick Reference

| Level | When to use |
| :--- | :--- |
| **FATAL** | The application crashed. |
| **ERROR** | An LLM call failed (API Down), but retrying. |
| **WARNING** | Token limit approaching (90% full). |
| **INFO** | "Chain Started", "Chain Finished". |
| **DEBUG** | Full Prompt text, exact variable state. |
