| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC1.8.2.1 StdOutCallbackHandler]]**               | Log to console                               | StdOutCallbackHandler class, console output, basic logging                      | StdOutCallbackHandler prints execution events to console.           |
| **[[LC1.8.2.2 FileCallbackHandler]]**                 | Log to files                                 | FileCallbackHandler class, file logging, log persistence                        | FileCallbackHandler writes events to log files.                     |
| **[[LC1.8.2.3 StreamingStdOutCallbackHandler]]**      | Stream tokens to console                     | StreamingStdOutCallbackHandler, token streaming, real-time output               | StreamingStdOutCallbackHandler shows tokens as they stream.         |
| **[[LC1.8.2.4 Using Built-in Handlers]]**             | Apply handlers in practice                   | Handler instantiation, passing to chains, multiple handlers                     | Instantiate handlers and pass to chain callbacks parameter.         |
| **[[LC1.8.2.5 Combining Multiple Handlers]]**         | Use handlers together                        | Handler lists, multiple outputs, complementary logging                          | Pass multiple handlers as a list for combined logging.              |

# Built-in Callback Handlers: The Standard Reporters

LangChain ships with a "StdLib" of handlers that cover 80% of debugging needs.

---

## 1. The Console Reporter (`StdOutCallbackHandler`)

This is what runs when you set `verbose=True`.
It prints the inputs and outputs of every chain step to `stdout`.

```python
from langchain_core.callbacks import StdOutCallbackHandler

handler = StdOutCallbackHandler()
chain.invoke("Hi", config={"callbacks": [handler]})
```

**Output**:
```text
> Entering new LLMChain chain...
Prompt after formatting:
"You are a helpful assistant..."

> Finished chain.
```

---

## 2. The File Reporter (`FileCallbackHandler`)

Identical to StdOut, but writes to a file.
**Use Case**: Nightly batch jobs where you need an audit trail.

```python
from langchain_community.callbacks import FileCallbackHandler
from loguru import logger

logfile = "output.log"
handler = FileCallbackHandler(logfile)

chain.invoke("Hi", config={"callbacks": [handler]})
```

---

## 3. The Streamer (`StreamingStdOutCallbackHandler`)

This is the most popular handler for **CLI Apps**.
It listens to `on_llm_new_token` and prints strings immediately without newlines.

```python
from langchain_core.callbacks import StreamingStdOutCallbackHandler

chat = ChatOpenAI(
    streaming=True, 
    callbacks=[StreamingStdOutCallbackHandler()]
)
```

**Architectural Warning**:
This only works for the **Local Console**. It cannot stream to a React frontend or a FastAPI client. For that, you need `AsyncIteratorCallbackHandler` (covered in **Custom Callbacks**).

---

## Quick Reference

| Handler | Purpose | Best For |
| :--- | :--- | :--- |
| **StdOut** | Print full steps | Local Debugging |
| **File** | Save full steps | Auditing |
| **StreamingStdOut** | Print tokens | CLI Tools |
| **OpenAICallback** | COUNT TOKENS | Cost Analysis (See LC1.8.8) |
