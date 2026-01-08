| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC1.7.8.1 Comparison of Memory Types]]**          | Compare available options                    | Buffer vs Window vs Summary, feature matrix, capability comparison              | Compare memory types by features and capabilities.                  |
| **[[LC1.7.8.2 Use Case Matching]]**                   | Match memory to application                  | Short vs long conversations, detail needs, use case fit                         | Match memory type to conversation length and detail needs.          |
| **[[LC1.7.8.3 Token Considerations]]**                | Factor in token costs                        | Token limits, cost estimation, budget constraints                               | Consider token costs when choosing memory type.                     |
| **[[LC1.7.8.4 Performance Trade-offs]]**              | Evaluate performance impacts                 | Latency, API calls, computational overhead                                      | Evaluate latency and API cost trade-offs.                           |
| **[[LC1.7.8.5 Decision Framework]]**                  | Apply structured selection                   | Decision tree, selection criteria, recommendation pattern                       | Follow a decision framework to select memory type.                  |

# Choosing Memory Type: The Trade-off Matrix

There is no "Best" memory. There is only the one that fits your **Budget** and **Latency** requirements.

---

## 1. The Decision Matrix

| Strategy | Cost (Tokens) | Latency (Speed) | Recall (Accuracy) | Logic |
| :--- | :--- | :--- | :--- | :--- |
| **Buffer** | 📈 Exponential | ⚡ Fast (1x) | 🧠 Perfect | `List.append()` |
| **Window** | ➖ Constant | ⚡ Fast (1x) | 📉 Poor (Forgetful) | `List[-k:]` |
| **Summary** | ➖ Constant | 🐌 Slow (2x) | 〰️ Fuzzy (Gist) | `LLM.summarize` |
| **SummaryBuffer** | ➖ Constant | ⚠️ Variable | 🧠 Good (Hybrid) | `TokenCount > Limit` |

---

## 2. Scenario Mapping

### Case A: Customer Support Chatbot
*   **Need**: Must remember user's name (long term), but only needs strict details of the last 3 messages to solve the current issue.
*   **Choice**: **ConversationSummaryBufferMemory**.
*   *Why*: Keeps the exact error code you just pasted (Buffer), but remembers you are a Premium User from 20 turns ago (Summary).

### Case B: Roleplay / NPC
*   **Need**: Infinite conversation, low cost per turn. Precision doesn't matter much (vibes > facts).
*   **Choice**: **ConversationSummaryMemory**.
*   *Why*: Keeps the "story arc" alive without crashing the context window.

### Case C: Code Assistant (Coding Agent)
*   **Need**: Perfect precision. If you forget variable `x`, code breaks.
*   **Choice**: **ConversationBufferMemory** (with a massive context window model like Gemini-1.5-Pro).
*   *Why*: You cannot "summarize" code. You need the raw syntax.

---

## 3. The "Vector Store" Memory (The Long Term)

For **Long-Term Memory** (days/weeks), none of the above work.
You need **Vector Memory** (RAG).

*   **Strategy**: Store every message in a Vector DB.
*   **Retrieval**: Fetch top-k messages similar to the *current* query.
*   **Use Case**: "What did we talk about last Tuesday?"

This is covered in **Section LC3 (RAG)**, but conceptually, it is just another form of "Memory Injection".

---

## Quick Reference

| If you care about... | Choose... |
| :--- | :--- |
| **Cost Control** | Window (`k=5`) |
| **Perfect Accuracy** | Buffer (Standard) |
| **Long Running Sessions** | SummaryBuffer |
| **Weeks/Months History** | Vector Store (RAG) |
