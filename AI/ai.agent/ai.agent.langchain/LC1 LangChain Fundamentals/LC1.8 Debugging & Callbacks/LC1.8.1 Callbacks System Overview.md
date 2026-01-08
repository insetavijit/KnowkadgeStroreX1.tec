| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC1.8.1.1 What Are Callbacks]]**                  | Understand callback purpose                  | Event hooks, execution monitoring, extensibility                                | Callbacks are hooks triggered during LangChain execution.           |
| **[[LC1.8.1.2 Callback Handlers]]**                   | Learn handler concept                        | BaseCallbackHandler, handler methods, event processing                          | Callback handlers implement methods for specific events.            |
| **[[LC1.8.1.3 Events in LangChain]]**                 | Know available events                        | on_llm_start, on_chain_end, on_tool_start, event types                          | Events fire at key execution points like start/end.                 |
| **[[LC1.8.1.4 Callback Lifecycle]]**                  | Understand event sequence                    | Event order, nested callbacks, hierarchy                                        | Callbacks follow predictable lifecycle during execution.            |
| **[[LC1.8.1.5 When Callbacks Fire]]**                 | Know trigger points                          | Start events, end events, error events, streaming events                        | Callbacks fire at start, end, error, and streaming points.          |

# Callbacks System: The Event Loop

Most developers interact with LangChain Synchronously (`response = chain.invoke()`).
But internally, LangChain is an **Event-Driven Engine**.

As data flows through the graph, it emits signals: "LLM Started", "Token Received", "Tool Finished".
The **Callback System** is the standard interface to subscribe to these signals.

---

## 1. The Core Architecture

Every `Runnable` accepts a `callbacks=[]` argument.
When that Runnable executes, it pushes events to all registered handlers.

**The Interface**:
`BaseCallbackHandler` defines the standard events:
*   `on_chat_model_start(serialized, messages, ...)`: LLM input is final.
*   `on_llm_new_token(token, ...)`: A chunk arrived (Streaming).
*   `on_llm_end(response, ...)`: Execution finished.
*   `on_tool_start(tool, input, ...)`: Tool is called.
*   `on_chain_error(error, ...)`: Exception raised.

---

## 2. Constructor vs Request Callbacks

This is a common source of bugs.

**Constructor Callbacks** (Global):
```python
# Attached to the object forever.
# Bad for handling User IDs or UI Sockets.
chat = ChatOpenAI(callbacks=[StdOutCallbackHandler()])
```

**Request Callbacks** (Scoped):
```python
# Attached ONLY to this specific execution.
# Perfect for passing a specialized WebSocketHandler for User A.
chat.invoke("Hi", config={"callbacks": [MyStreamHandler()]})
```

**Architectural Rule**:
Always use **Request Callbacks** (`config`) for UI/Streaming logic.
Use **Constructor Callbacks** only for global logging (e.g., logging to a file).

---

## 3. Propagation (The "Tree" Problem)

If you have a chain `A | B | C`, and you pass a callback to the invoke:

```python
chain.invoke("input", config={"callbacks": [handler]})
```

LangChain automatically **Propagates** this handler to children A, B, and C.
This is why you don't need to manually attach loggers to every sub-component. The `config` object flows down the tree.

---

## Quick Reference

| Event | Payload | Use Case |
| :--- | :--- | :--- |
| **Start** | Prompts / Inputs | Logging inputs. |
| **New Token** | String Chunk | Streaming to UI. |
| **End** | Final Output | Analytics / Cost tracking. |
| **Error** | Exception | Alerting (PagerDuty). |
