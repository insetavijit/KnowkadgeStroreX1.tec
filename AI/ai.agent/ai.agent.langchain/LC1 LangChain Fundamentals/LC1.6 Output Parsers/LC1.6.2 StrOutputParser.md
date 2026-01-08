| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC1.6.2.1 Basic String Parsing]]**                | Extract text from responses                  | StrOutputParser class, simple text extraction, no structure                     | StrOutputParser extracts plain text from AIMessage.                 |
| **[[LC1.6.2.2 Extracting Text from AIMessage]]**      | Handle message objects                       | AIMessage.content, string conversion, content access                            | Use StrOutputParser to get string from AIMessage.                   |
| **[[LC1.6.2.3 Simple Output Extraction]]**            | Perform basic extraction                     | Direct content access, minimal processing, straightforward use                  | StrOutputParser is the simplest output parser.                      |
| **[[LC1.6.2.4 When to Use StrOutputParser]]**         | Choose appropriate scenarios                 | Simple text tasks, no structure needed, basic Q&A                               | Use StrOutputParser when you just need text output.                 |
| **[[LC1.6.2.5 StrOutputParser in LCEL]]**             | Integrate with LCEL chains                   | Pipe after LLM, chain termination, streaming support                            | Pipe StrOutputParser after LLM for clean text output.               |

# StrOutputParser: The Normalizer

When you call an LLM (e.g., `ChatOpenAI`), it does NOT return a string.
It returns an `AIMessage` object: `AIMessage(content="Hello world", response_metadata={'token_usage': ...})`.

If you try to concatenate this with another string (`"User said: " + response`), your code breaks.
`StrOutputParser` is the standard tool to unwrap the content.

---

## 1. The Token Pipeline (Streaming)

The most robust feature of `StrOutputParser` is that it **streams by default**.
It doesn't wait for the `AIMessage` to be complete. It intercepts chunks from the LLM, extracts the `.content` field from the Chunk, and yields the string.

```python
# Streaming WITHOUT Parser
for chunk in model.stream("Hi"):
    print(chunk) 
    # Output: AIMessageChunk(content='H'), AIMessageChunk(content='i')...

# Streaming WITH Parser
chain = model | StrOutputParser()
for token in chain.stream("Hi"):
    print(token)
    # Output: 'H', 'i'...
```

**Architectural Rule**: Always attach this parser at the end of a chain if the output is meant for a user interface. It simplifies the frontend logic significantly.

---

## 2. Unifying ChatModels and LLMs

Historically, LangChain had two model types:
*   `LLM` (Legacy): Returned logical strings.
*   `ChatModel` (Modern): Returned Message objects.

`StrOutputParser` acts as a **Polymorphic Adapter**.
*   If input is `str`, it passes it through.
*   If input is `AIMessage`, it extracts `.content`.

This allows your chain to be model-agnostic. You can swap `OpenAI` (Chat) for `LLamaCpp` (Text) without changing the rest of the pipeline.

---

## 3. Usage in RAG

In Retrieval Augmented Generation, the context is often a string.
If you use a "Stuff Documents" chain, you need the *text* of the answer, not the metadata.

```python
rag_chain = (
    {"context": retriever, "question": RunnablePassthrough()}
    | prompt
    | model
    | StrOutputParser() # <--- Essential for clean output
)
```

---

## Quick Reference

| Method | Input | Output |
| :--- | :--- | :--- |
| **invoke** | `AIMessage(content="Hi")` | `"Hi"` |
| **stream** | `Iterator[AIMessageChunk]` | `Iterator[str]` |
| **batch** | `List[AIMessage]` | `List[str]` |
