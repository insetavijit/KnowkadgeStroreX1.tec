| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC1.8.7.1 Creating Custom Handlers]]**            | Build specialized handlers                   | Custom handler classes, specialized logging, domain requirements                | Create custom handlers for specialized needs.                       |
| **[[LC1.8.7.2 BaseCallbackHandler Interface]]**       | Implement the base class                     | BaseCallbackHandler, abstract methods, inheritance                              | Extend BaseCallbackHandler to create custom handlers.               |
| **[[LC1.8.7.3 Implementing Callback Methods]]**       | Code specific event handlers                 | on_llm_start, on_chain_end, method signatures                                   | Implement specific on_* methods for events you need.                |
| **[[LC1.8.7.4 Custom Logging]]**                      | Log to custom destinations                   | Custom log formats, external services, database logging                         | Use custom handlers to log to any destination.                      |
| **[[LC1.8.7.5 Metrics Collection]]**                  | Gather execution metrics                     | Timing metrics, token counts, custom metrics                                    | Collect custom metrics via callback handlers.                       |

# Custom Callback Handlers: The Integration Layer

The most common reason to write a custom handler is **Streaming to a Frontend**.
You want to push tokens to a React UI *as they arrive*, via WebSocket or Server-Sent Events (SSE).

---

## 1. The Base Interface

You should always inherit from `BaseCallbackHandler`.
This ensures forward compatibility (if LangChain adds new events, your class won't crash).

```python
from langchain_core.callbacks import BaseCallbackHandler
from uuid import UUID
from typing import Any, Dict

class MyCustomHandler(BaseCallbackHandler):
    # Only override what you need
    def on_llm_new_token(self, token: str, **kwargs) -> None:
        print(f"Token: {token}")
```

---

## 2. Pattern: The WebSocket Streamer

This is the standard pattern for building ChatGPT clones.

```python
class WebSocketStreamer(BaseCallbackHandler):
    def __init__(self, websocket):
        self.ws = websocket
        
    def on_llm_new_token(self, token: str, **kwargs):
        # Push to Queue or Socket
        self.ws.send_json({"type": "token", "content": token})
        
    def on_chain_end(self, outputs: Dict[str, Any], **kwargs):
        self.ws.send_json({"type": "end"})
```

**Usage**:
```python
@app.websocket("/chat")
async def chat_endpoint(websocket):
    streamer = WebSocketStreamer(websocket)
    # Pass specifically to this invocation
    await chain.ainvoke("Hi", config={"callbacks": [streamer]})
```

---

## 3. Async Considerations

If you are using `ainvoke` (Async), your handler methods should technically be `async def on_...`.
However, `BaseCallbackHandler` methods are synchronous by default.
LangChain provides `AsyncCallbackHandler` for purely async operations, but mixing them can be tricky.
**Best Practice**: Keep handlers fast and non-blocking. If you need to write to a slow DB, push to an async queue/channel instead of awaiting inside the handler.

---

## Quick Reference

| Method | Argument | Purpose |
| :--- | :--- | :--- |
| `on_chat_model_start` | `messages` | Capture the exact prompt stack. |
| `on_llm_new_token` | `token` | Real-time UI updates. |
| `on_tool_start` | `tool.name` | Show "Thinking..." UI states. |
| `on_chain_error` | `error` | Show "Something went wrong" toast. |
