| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC1.5.8.1 Side by Side Comparison]]**             | Compare syntax directly                      | LLMChain vs LCEL equivalent, code examples, readability                         | LCEL syntax is more concise than legacy chain classes.              |
| **[[LC1.5.8.2 Migration Examples]]**                  | Convert legacy to LCEL                       | Before/after examples, step-by-step migration, patterns                         | Migrate legacy chains to LCEL with equivalent patterns.             |
| **[[LC1.5.8.3 Feature Parity]]**                      | Compare available features                   | Streaming, async, callbacks, observability support                              | LCEL matches or exceeds legacy features.                            |
| **[[LC1.5.8.4 Performance Differences]]**             | Compare execution characteristics            | Overhead, streaming efficiency, memory usage                                    | LCEL generally performs better due to streaming.                    |
| **[[LC1.5.8.5 When to Use Which]]**                   | Make informed choices                        | New projects, existing code, feature requirements, team familiarity             | Use LCEL for new code; migrate legacy as needed.                    |

# LCEL vs Legacy: The Migration Matrix

This is your Reference guide for porting "v1 code" (from StackOverflow/Medium/ChatGPT) to "v2 Architecture".

---

## 1. The Core Syntax Shift

### Legacy (The "Wrapper" Era)
You instantiated a Class that *hid* the logic. You had to memorize the arguments for 50 different classes.

```python
# OLD: Opaque
chain = LLMChain(
    llm=ChatOpenAI(), 
    prompt=prompt,
    output_key="text" 
)
chain.run("input")
```

### LCEL (The "Pipe" Era)
You compose the logic yourself. You only need to know 3 primitives.

```python
# NEW: Transparent
chain = prompt | ChatOpenAI() | StrOutputParser()
chain.invoke("input")
```

---

## 2. Memory Management (The Biggest Change)

This is where 90% of developers get stuck.

*   **Legacy**: `ConversationChain(memory=BufferMemory())`. The chain held the state internally. This made it impossible to deploy serverless (Lambda/Cloud Run) because the state died with the process.
*   **LCEL**: **Stateless**. The state is passed in as an argument (`history`).

```python
# NEW Pattern: RunnableWithMessageHistory
final_chain = RunnableWithMessageHistory(
    runnable=chain,
    get_session_history=get_redis_history # External State Store
)
```

**Architecture**: Separation of Compute (Chain) and State (Redis/SQL).

---

## 3. Retrieval QA

*   **Legacy**: `RetrievalQA.from_chain_type(..., chain_type="stuff")`.
    *   *Problem*: "Stuff" documents was hardcoded. You couldn't easily modify how documents were formatted.
*   **LCEL**: You build the "Stuff" logic explicitly.

```python
stuff_chain = (
    {"context": retriever, "question": RunnablePassthrough()}
    | prompt
    | model
)
```

---

## 4. Off-the-Shelf Constructors

LangChain still provides helpers, but they now return **Runnables**, not Chains.

| Legacy Constructor | Modern Constructor (Returns Runnable) |
| :--- | :--- |
| `load_qa_chain` | `create_stuff_documents_chain` |
| `SQLDatabaseChain` | `create_sql_query_chain` |
| `create_extraction_chain` | `.with_structured_output()` (Model Method) |
| `RouterChain` | `RunnableBranch` |

---

## Quick Reference

| Feature | Legacy Approach | LCEL Approach |
| :--- | :--- | :--- |
| **Streaming** | `CallbackHandler` (Complex) | `.stream()` (Native) |
| **Async** | `arun` (Often emulated) | `.ainvoke` (Native AsyncIO) |
| **Tracing** | Console Logs | LangSmith (Visual Spans) |
| **Typing** | `Dict` (Unsafe) | `Pydantic` (Validated) |
