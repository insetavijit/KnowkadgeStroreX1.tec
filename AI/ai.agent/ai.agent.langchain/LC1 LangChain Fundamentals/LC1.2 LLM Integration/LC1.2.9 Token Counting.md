| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC1.2.9.1 Tiktoken Library]]**                    | Use OpenAI's token counting library          | tiktoken install, encoding selection, cl100k_base, model-specific encodings     | Use tiktoken to count tokens for OpenAI models.                     |
| **[[LC1.2.9.2 Counting Tokens Before Requests]]**     | Pre-calculate token usage                    | Prompt token count, message serialization, input validation                     | Count tokens before sending to check context limits.                |
| **[[LC1.2.9.3 Context Window Limits]]**               | Understand model context capacity            | 4K, 8K, 128K windows, context length by model, overflow handling                | Stay within context window to avoid truncation.                     |
| **[[LC1.2.9.4 Cost Estimation]]**                     | Calculate API costs                          | Pricing per 1K tokens, input vs output pricing, budget tracking                 | Estimate costs by multiplying token count by price.                 |
| **[[LC1.2.9.5 Token Budgeting Strategies]]**          | Allocate tokens effectively                  | Prompt compression, chunking, summarization, priority allocation                | Budget tokens between prompt, context, and response.                |

# Token Counting: The Economics of AI

In cloud computing, you pay for CPU-seconds.
In AI, you pay for **Tokens**.
Understanding tokens is not just about billing; it's about **Physics**. Every model has a hard limit (Context Window). If you exceed it, the request fails.

---

## 1. What is a Token?

A token is not a word. It is a chunk of characters.
*   **Rule of Thumb**: 1,000 tokens ≈ 750 words.
*   **The Abstraction Leak**: The word "Hamburger" might be 1 token. The string "x86_64" might be 3 tokens.

**The Library: Tiktoken**
OpenAI uses a specialized BPE (Byte Pair Encoding) tokenizer. LangChain exposes this via the `tiktoken` library.

```python
import tiktoken

encoding = tiktoken.encoding_for_model("gpt-4")
count = len(encoding.encode("Hello world"))
# Result: 2 tokens
```

---

## 2. Managing the Context Window (Real Estate)

Think of the Context Window as **RAM**.
*   **gpt-4-turbo**: 128,000 tokens (Approx 300 pages of text).
*   **gpt-4 (standard)**: 8,192 tokens.

You must budget this RAM between three tenants:
1.  **System Prompt**: The instructions (Fixed cost).
2.  **Context / History**: The RAG data or chat history (Variable cost).
3.  **User Query**: The new question (Variable).
4.  **Response Reserve**: Space left for the model to write the answer.

**The Crash**:
`InvalidRequestError: context_length_exceeded`.
This happens when `(System + History + Query)` uses 8,190 tokens, leaving only 2 tokens for the answer.

---

## 3. How to Count in LangChain

You don't need to manually run `tiktoken` on every string. LangChain models have a helper.

```python
chat = ChatOpenAI(model="gpt-4")

message = HumanMessage(content="Hello there")
num_tokens = chat.get_num_tokens_from_messages([message])

print(f"This payload costs {num_tokens} tokens")
```

**Why this is complex**:
Counting "Hello there" is easy.
Counting a list of messages is hard because every API format (OpenAI vs Anthropic) adds hidden "Control Tokens" (`<|im_start|>`, `role=user`, etc) that count against your bill but aren't visible in the string. `get_num_tokens_from_messages` handles this protocol overhead for you.

---

## 4. Cost Tracking (The "Meter")

To bill your own users (or just monitor burn rate), you need the **actual** usage returned by the API, not just an estimate.

LangChain provides a `get_openai_callback()` context manager to aggregate costs across multiple calls.

```python
from langchain_community.callbacks import get_openai_callback

with get_openai_callback() as cb:
    chat.invoke("Tell me a joke")
    chat.invoke("Tell me another")

print(f"Total Cost: ${cb.total_cost}")
print(f"Total Tokens: {cb.total_tokens}")
```

> **Production Note**: In a scale app, you wouldn't use this context manager. You would rely on the `response.response_metadata['token_usage']` dictionary available on every `AIMessage` and log it to DataDog or distinct analytics.

---

## 5. Trimming Strategies

What do you do when you are 'Out of RAM'?

1.  **Summarization**: Ask an LLM to condense the chat history.
2.  **Windowing**: Only keep the last $K$ messages (ConversationBufferWindowMemory).
3.  **Selection**: Use a Selector to pick only relevant examples.

---

## Quick Reference

| Concept | Rough Math | Note |
| :--- | :--- | :--- |
| **1 Token** | ~4 Characters | Use this for back-of-napkin math. |
| **Context Window** | Input + Output | You pay for empty space if you don't use it? No, you only pay for used tokens. |
| **Tiktoken** | The "Standard" | The precise counter for OpenAI models. |
| **Control Tokens** | +4 to +7 tokens | Hidden overhead per message. |
