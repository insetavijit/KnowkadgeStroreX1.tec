| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC1.7.4.1 Summarizing Conversation History]]**    | Compress conversations via summary           | Summary creation, LLM-based compression, key points retention                   | Summary memory uses LLM to compress conversation history.           |
| **[[LC1.7.4.2 LLM-Based Summarization]]**             | Use LLM for summaries                        | Summarization prompt, model selection, summary quality                          | An LLM generates progressive summaries of the conversation.         |
| **[[LC1.7.4.3 Summary Prompts]]**                     | Configure summarization                      | Summary prompt template, customization, summary style                           | Customize prompt to control summary style and content.              |
| **[[LC1.7.4.4 Progressive Summarization]]**           | Update summaries over time                   | Incremental updates, running summary, context evolution                         | Summary updates progressively as conversation continues.            |
| **[[LC1.7.4.5 Summary Memory Trade-offs]]**           | Evaluate advantages and costs                | Token savings vs accuracy, summary latency, detail loss                         | Summary saves tokens but may lose conversation details.             |

# ConversationSummaryMemory: The Compression Algorithm

Buffer Memory is precise but expensive.
Window Memory is cheap but forgetful.
**Summary Memory** is the middle ground: It uses an LLM to "Zip" the conversation.

---

## 1. The Strategy: Semantic Compression

Instead of storing:
> User: I like apples.
> AI: noted.
> User: I also like red paint.
> AI: ok.

It stores:
> The user stated a preference for red objects (apples, paint).

**Architectural Pros**:
*   **Constant Token Usage**: No matter how long the chat is, the summary stays relatively small.
*   **Infinite Duration**: It remembers facts from Turn 1 at Turn 1000 (if important).

**Architectural Cons**:
*   **Double Latency**: Every time you save context, it calls the LLM to update the summary.
*   **Lossy Compression**: Nuance is lost. The model might forget *exactly* what you said.

---

## 2. The Implementation

You must provide an `llm` to the memory, because the memory *is* an agent itself.

```python
from langchain.memory import ConversationSummaryMemory
from langchain_openai import ChatOpenAI

llm = ChatOpenAI(model="gpt-3.5-turbo") # Use a cheap model for summarizing
memory = ConversationSummaryMemory(llm=llm)

memory.save_context({"input": "hi"}, {"output": "whats up"})
memory.save_context({"input": "im hungry"}, {"output": "eat an apple"})

print(memory.load_memory_variables({}))
# Output: {'history': 'The user greeted the AI. The user mentioned being hungry, and the AI suggested an apple.'}
```

---

## 3. Asynchronous Summarization

Because summarizing takes time, this is the #1 bottleneck in chat apps.
**Production Pattern**: Run the summarization in the background.

1.  **Main Thread**: Append message to DB. Return response to User.
2.  **Worker Queue (Celery/SQS)**: Pick up the new messages, run `summary_model.invoke()`, update the "Summary" column in the User Profile.

This decouples the "Reading" experience (Fast) from the "Remembering" experience (Slow).

---

## Quick Reference

| Feature | Buffer | Window | Summary |
| :--- | :--- | :--- | :--- |
| **Token Cost** | $$$ (High) | $ (Low) | $$ (Medium) |
| **Recall** | Perfect | Recent Only | Fuzzy / Gist |
| **Latency** | Zero | Zero | High (Requires LLM call) |
