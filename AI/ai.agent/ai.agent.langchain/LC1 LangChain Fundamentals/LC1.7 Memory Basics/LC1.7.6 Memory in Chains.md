| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC1.7.6.1 Adding Memory to LLMChain]]**           | Integrate memory with chains                 | memory parameter, chain constructor, basic integration                          | Pass memory object to chain's memory parameter.                     |
| **[[LC1.7.6.2 Memory Keys]]**                         | Configure memory variable names              | memory_key, input_key, output_key, key configuration                            | Configure memory_key to match chain's expected variable.            |
| **[[LC1.7.6.3 Load Memory Variables]]**               | Retrieve stored context                      | load_memory_variables(), context loading, input preparation                     | Use load_memory_variables() to get stored context.                  |
| **[[LC1.7.6.4 Save Context]]**                        | Store new interactions                       | save_context() method, input/output saving, automatic saving                    | Use save_context() to save new interactions to memory.              |
| **[[LC1.7.6.5 Memory Lifecycle]]**                    | Understand memory flow                       | Load → Execute → Save cycle, chain execution flow                               | Memory flows: load before call, save after response.                |

# Memory in Chains: Returns of the Lifecycle

Understanding **When** memory is saved is as important as **How**.

---

## 1. The Legacy "Black Box" Lifecycle

In the old `ConversationChain`, the lifecycle was hidden.

```python
# The Hidden Loop
class Chain:
    def run(self, input):
        # 1. READ: Get history from memory
        history = self.memory.load_memory_variables({})
        
        # 2. RUN: Call LLM
        response = self.llm.generate(input, history)
        
        # 3. WRITE: Save input/response to memory
        self.memory.save_context(input, response)
        
        return response
```

**The Problem**: You couldn't modify step 1 or 3.
What if you wanted to sanitize the PII from the user input *before* saving it? You couldn't.

---

## 2. The LCEL "Explicit" Lifecycle

In LCEL, you must manage the lifecycle yourself using `RunnableWithMessageHistory`.
This is a wrapper that re-implements the Read/Write loop but keeps the "Run" logic transparent.

```python
from langchain_core.runnables.history import RunnableWithMessageHistory

# 1. Define the Core Logic (Stateless)
chain = prompt | model

# 2. Define the Wrapper (Stateful)
chain_with_history = RunnableWithMessageHistory(
    chain,
    get_session_history=get_redis_history, # The "Read" Function
    input_messages_key="question",
    history_messages_key="history"
)

# 3. Invoke
result = chain_with_history.invoke(
    {"question": "Hi"},
    config={"configurable": {"session_id": "123"}}
)
```

**Architecture**:
The `RunnableWithMessageHistory` object intercepts the `.invoke()`.
1.  Calls `get_redis_history("123")`.
2.  Injects the result into `prompt` under `history_messages_key`.
3.  Runs the chain.
4.  Takes result, appends to Redis.

---

## 3. Manual Injection (The "Do It Yourself" Pattern)

For maximum control, you don't even use the wrapper. You just pass the history as an argument.

```python
# 1. Fetch
history = redis.get("123")

# 2. Run
response = chain.invoke({"input": "Hi", "history": history})

# 3. Save
redis.append("123", "Hi", response)
```

This is the preferred pattern for **Production Microservices** because it makes the I/O side-effects explicit rather than hidden inside a library class.

---

## Quick Reference

| Method | ControlLevel | Complexity | Recommended For |
| :--- | :--- | :--- | :--- |
| **Legacy `Chain(memory=...)`** | Low | Low | Prototypes / Tutorials. |
| **`RunnableWithMessageHistory`** | Medium | Medium | Standard Chatbots. |
| **Manual Injection** | High | High | Distributed Systems. |
