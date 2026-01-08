| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC1.8.3.1 Enabling Verbose Output]]**             | Turn on detailed logging                     | verbose=True, enabling verbose mode, quick setup                                | Set verbose=True for detailed execution logging.                    |
| **[[LC1.8.3.2 Verbose Parameter]]**                   | Configure verbose per component              | Component-level verbose, chain verbose, LLM verbose                             | Set verbose on individual chains or LLMs.                           |
| **[[LC1.8.3.3 Chain-Level vs Global Verbose]]**       | Choose scope of verbosity                    | Local vs global, get_verbose(), set_verbose()                                   | Set verbose globally or per-chain as needed.                        |
| **[[LC1.8.3.4 Interpreting Verbose Output]]**         | Read and understand logs                     | Log format, events shown, data displayed                                        | Verbose output shows inputs, outputs, and events.                   |
| **[[LC1.8.3.5 Verbose for Quick Debugging]]**         | Debug efficiently                            | Rapid issue identification, input verification, flow tracing                    | Use verbose for quick debugging during development.                 |

# Verbose Mode: The "Print Debugging" Switch

Verbose mode is the "Easy Button" for debugging.
It simply attaches a `StdOutCallbackHandler` to your chain.

---

## 1. Global vs Local Verbosity

**The Global Switch** (Impacts EVERYTHING):
Use this when you are just playing around in a notebook.
```python
from langchain.globals import set_verbose, set_debug

# 1. Standard Verbose (Input/Output of Chains)
set_verbose(True)

# 2. Debug Mode (Input/Output of EVERYTHING, including parsers)
set_debug(True)
```

**The Local Switch** (Impacts one object):
Use this in production code to debug a specific flaky chain without spamming the logs.
```python
chain = Prompt | Model
chain.invoke("hi", config={"verbose": True})
```

---

## 2. What `set_debug(True)` actually does

`set_debug(True)` is more aggressive than `verbose=True`.
It prints **everything**:
*   The raw HTTP request to OpenAI.
*   The raw JSON response.
*   The hidden steps inside `StrOutputParser`.

**Warning**: Do not use `set_debug(True)` in production logs (it keeps *everything*).

---

## 3. The "Silent" Bug

A common confusion: "I set `verbose=True` but nothing is printing!"

**Reason**: You are likely running in a **FastAPI** or **Celery** worker.
`verbose=True` prints to `stdout`.
If your background worker captures `stdout` (or discards it), you see nothing.

**Fix**: Use `FileCallbackHandler` or **LangSmith** instead.

---

## Quick Reference

| Command | Scope | Detail Level |
| :--- | :--- | :--- |
| `config={"verbose": True}` | **Safe**. Local to request. | Inputs/Outputs. |
| `set_verbose(True)` | **Risky**. Global to process. | Inputs/Outputs. |
| `set_debug(True)` | **Debug Only**. Global. | HTTP Payloads + Internal steps. |
