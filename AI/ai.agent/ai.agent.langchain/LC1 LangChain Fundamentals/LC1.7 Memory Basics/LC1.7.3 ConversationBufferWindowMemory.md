| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC1.7.3.1 Sliding Window Memory]]**               | Keep only recent messages                    | Window concept, moving window, recent context focus                             | Window memory keeps only the last k messages.                       |
| **[[LC1.7.3.2 K Parameter]]**                         | Configure window size                        | k value, message count, tuning considerations                                   | Set k to control how many recent messages to keep.                  |
| **[[LC1.7.3.3 Limiting Context Length]]**             | Manage token usage                           | Token conservation, context budget, overflow prevention                         | Window memory limits tokens by dropping old messages.               |
| **[[LC1.7.3.4 Memory Trimming]]**                     | Handle message removal                       | Automatic trimming, oldest first, FIFO approach                                 | Old messages are automatically trimmed as new ones arrive.          |
| **[[LC1.7.3.5 Balancing Context and Tokens]]**        | Optimize window size                         | Trade-off analysis, context needs vs costs, optimal k                           | Balance context needs against token costs when setting k.           |

# ConversationBufferWindowMemory: The Rolling Window

As conversations grow, efficiency drops. The "Rolling Window" algorithm solves this by prioritizing **Recency** over **Completeness**.

---

## 1. The Strategy: Amnesia by Design

This memory type assumes that **Ancient History doesn't matter**.
It keeps a list of size `k`. When message `k+1` arrives, message `1` is deleted.

*   `k=1`: The model only knows what you *just* said.
*   `k=5`: The model can follow a short logic chain.

**Architectural Pros**:
*   **Bounded Cost**: You will never exceed your token budget.
*   **Bounded Latency**: Processing time remains constant.

**Architectural Cons**:
*   **Total Amnesia**: "My name is Bob" (Turn 1). At Turn 10, the model asks "Who are you?".

---

## 2. The Implementation

```python
from langchain.memory import ConversationBufferWindowMemory

# k=2 means: 2 Human-AI Pairs. (Total 4 messages)
memory = ConversationBufferWindowMemory(k=2, return_messages=True)

memory.save_context({"input": "hi"}, {"output": "whats up"})
memory.save_context({"input": "not much"}, {"output": "cool"})

# Now the buffer is full (2 pairs)
memory.save_context({"input": "new thing"}, {"output": "ok"})

# "hi" / "whats up" is GONE.
```

---

## 3. The Modern Database Equivalent

In production, we don't use `ConversationBufferWindowMemory` (in-memory).
We use a **SQL Query** on the message log.

```sql
-- The "Mental Model" of Window Memory
SELECT * FROM messages 
WHERE abstract_session_id = 'session_123' 
ORDER BY created_at DESC 
LIMIT 10;
```

This is the standard pattern for high-traffic chatbots (e.g., customer support), where the relevant context is almost always the last few exchanges.

---

## Quick Reference

| Parameter | Value | Note |
| :--- | :--- | :--- |
| **k** | `int` | The number of **Interactions** (User+AI pairs) to keep. `k=2` means 4 individual messages. |
| **return_messages** | `True` | Standard for Chat Models. |
