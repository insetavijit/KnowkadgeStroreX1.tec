| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC1.4.8.1 Legacy Chain Syntax]]**                 | Understand older chain patterns              | Class-based chains, explicit composition, pre-LCEL patterns                     | Legacy chains use classes like LLMChain and SequentialChain.        |
| **[[LC1.4.8.2 Migration Path to LCEL]]**              | Convert legacy to modern                     | Rewriting chains, equivalent LCEL patterns, migration strategy                  | Migrate legacy chains to LCEL for modern features.                  |
| **[[LC1.4.8.3 When Legacy Chains Apply]]**            | Know when to use legacy                      | Feature support, compatibility needs, existing codebases                        | Use legacy chains when specific features require them.              |
| **[[LC1.4.8.4 Deprecation Timeline]]**                | Plan for future changes                      | Deprecation notices, version compatibility, upgrade planning                    | Plan migrations before legacy chains are deprecated.                |
| **[[LC1.4.8.5 Feature Comparison]]**                  | Compare legacy vs LCEL features              | Streaming, async, debugging, observability differences                          | LCEL offers better streaming, async, and observability.             |

# Legacy Chains vs LCEL: The Paradigm Shift

LangChain underwent a massive architectural rewrite in late 2023.
It moved from **Object-Oriented wrappers** (Legacy) to **Functional Composition** (LCEL).

Understanding this shift is critical because 80% of the tutorials on the internet still use the old syntax, which is now considered "Technical Debt."

---

## 1. The Comparison: "The Black Box" vs "The Glass Pipe"

### Legacy: Object-Oriented (The Application Framework)
The old mental model was that LangChain is a **Framework**. You instantiate classes that do magic for you.

```python
# LEGACY (Imperative)
chain = RetrievalQA.from_chain_type(
    llm=llm,
    retriever=retriever,
    chain_type="stuff"
)
result = chain.run("Query")
```

**Pros**: Easy for beginners (1 line of code).
**Cons**: Impossible to debug. What is `"stuff"`? How do I change the system prompt? How do I stream the output?

### LCEL: Functional (The Library)
The new mental model is that LangChain is a **Library** of primitives. You compose them yourself.

```python
# LCEL (Declarative)
chain = (
    {"context": retriever, "question": RunnablePassthrough()}
    | prompt 
    | model 
    | StrOutputParser()
)
result = chain.invoke("Query")
```

**Pros**: Total control. You see exactly where data flows.
**Cons**: Higher learning curve initially.

---

## 2. Why the Shift Happened (The "Why")

1.  **Streaming**: Legacy chains buffered the entire response. LCEL streams by default.
2.  **Async**: Legacy wrappers had patchy `await` support. LCEL has native `asyncio`.
3.  **Observability**: In Legacy, a chain was one giant "Trace" block. In LCEL (with LangSmith), you see every step (`Retriever -> 2s`, `LLM -> 4s`) as a separate span.

---

## 3. Migration Cheat Sheet

| Legacy Class | Modern LCEL Pattern |
| :--- | :--- |
| `LLMChain` | `prompt \| llm` |
| `SequentialChain` | `chain1 \| chain2` |
| `RouterChain` | `RunnableBranch` |
| `TransformChain` | `RunnableLambda(func)` |
| `RetrievalQA` | `retriever \| prompt \| llm` |
| `ConversationalRetrievalChain` | `history_aware_retriever \| qa_chain` |

---

## 4. When to Use Legacy?

Is there *any* reason to use `LLMChain` today?
**No.**

However, some high-level "Off-the-shelf" chains (like `create_sql_query_chain`) still use legacy code internally, but they expose an LCEL interface. You should treat them as black boxes, but write your own code using LCEL.

> **Architectural Dictum**: "If you are writing `class MyChain(Chain):`, you are doing it wrong. Implement `Runnable` or just use the `|` operator."

---

## Quick Reference

| Feature | Legacy | LCEL |
| :--- | :--- | :--- |
| **Syntax** | `Chain(llm=llm, prompt=prompt)` | `prompt \| llm` |
| **Debug** | `.verbose=True` (Print to console) | LangSmith Traces (Visual Graph) |
| **Typing** | `Dict[str, Any]` (Loose) | Pydantic Models (Strict) |
| **Future** | **Deprecated** | **Standard** |
