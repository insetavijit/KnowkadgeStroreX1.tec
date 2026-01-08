| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC1.8.6.1 What Is LangSmith]]**                   | Understand LangSmith platform                | LangSmith platform, tracing service, debugging tool                             | LangSmith is LangChain's platform for tracing and debugging.        |
| **[[LC1.8.6.2 Setting Up Tracing]]**                  | Configure LangSmith tracing                  | LANGCHAIN_TRACING_V2, API key setup, environment config                         | Set LANGCHAIN_TRACING_V2=true to enable LangSmith.                  |
| **[[LC1.8.6.3 Viewing Traces]]**                      | Navigate trace UI                            | Trace explorer, run details, execution timeline                                 | View traces in LangSmith UI to see execution details.               |
| **[[LC1.8.6.4 Debugging in LangSmith]]**              | Use LangSmith for debugging                  | Error identification, root cause analysis, replay                               | Debug issues by examining traces in LangSmith.                      |
| **[[LC1.8.6.5 Production Monitoring]]**               | Monitor production systems                   | Live monitoring, alerting, performance tracking                                 | Use LangSmith for production monitoring and alerts.                 |

# LangSmith Integration: The Cloud Platform

Tracing to `stdout` is useful for development.
Tracing to a **Persistence Layer** is required for production.
**LangSmith** is LangChain's dedicated observability platform (SaaS).

---

## 1. Zero-Code Integration

Because LangChain is instrumented by default, enabling LangSmith requires **0 lines of Python code**. You only need Environment Variables.

```bash
export LANGCHAIN_TRACING_V2=true
export LANGCHAIN_API_KEY="ls__..."
export LANGCHAIN_PROJECT="My-Production-App"
```

Once set, *every* `chain.invoke()` in your application will automatically push traces to the cloud.

---

## 2. Key Features for Architects

### A. The "Replay" Button (Playground)
You see a trace where the model hallucinated.
In 1 click, you can "Open in Playground".
LangSmith loads the *exact* prompt parameters (temp, model, inputs) from that run, allowing you to edit and retry immediately.

### B. Dataset Collection
You can select 50 good runs and click "Add to Dataset".
This becomes your **Unit Test Suite** for future regressions.

### C. Cost Auditing
LangSmith aggregates token usage by **Model**, **Project**, and **Tenant**.
"Why is our bill high?" -> "Oh, the ReAct Agent is looping 15 times on query X."

---

## 3. Distributed Tracing

If your app is composed of multiple microservices (Service A calls Service B calls LLM), you can link traces using parent IDs.

```python
# Service A
parent_run_id = str(uuid.uuid4())
call_service_b(headers={"x-langchain-parent": parent_run_id})

# Service B
run_tree = RunTree(name="Service B", parent_run_id=header_id)
```

---

## Quick Reference

| Variable | Value | Purpose |
| :--- | :--- | :--- |
| `LANGCHAIN_TRACING_V2` | `true` | Turn it on. |
| `LANGCHAIN_PROJECT` | `string` | Group traces by app. |
| `LANGCHAIN_ENDPOINT` | URL | (Optional) For self-hosted instances. |
