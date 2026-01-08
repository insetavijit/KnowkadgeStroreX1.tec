| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC2.1.1.1 What Is RunnableParallel]]**            | Define parallel execution                    | RunnableParallel class, concurrent chains, parallel composition                 | RunnableParallel runs multiple chains concurrently.                 |
| **[[LC2.1.1.2 Concurrent Execution Concept]]**        | Understand concurrency benefits              | Parallel vs sequential, time savings, independent operations                    | Parallel execution runs chains simultaneously for speed.            |
| **[[LC2.1.1.3 Parallel vs Sequential]]**              | Compare execution modes                      | When to parallelize, dependencies, performance trade-offs                       | Use parallel when chains have no dependencies.                      |
| **[[LC2.1.1.4 Use Cases for Parallel Chains]]**       | Identify appropriate scenarios               | Multiple retrievals, parallel API calls, fan-out processing                     | Parallelize independent operations like multiple searches.          |
| **[[LC2.1.1.5 Parallel Chain Benefits]]**             | Summarize advantages                         | Reduced latency, efficiency, throughput gains                                   | Parallel chains reduce total execution time.                        |

# RunnableParallel: The Concurrency Primitive

In Python, writing parallel async code (`asyncio.gather`) is boilerplate-heavy and error-prone.
In LCEL, parallelism is a **First-Class Citizen**, represented by a dictionary.

---

## 1. The Core Abstraction

`RunnableParallel` (also aliased as `RunnableMap`) takes a single input and broadcasts it to multiple branches.
It returns a **Dictionary** where the keys match the branch names.

```python
from langchain_core.runnables import RunnableParallel

# Concept:
# Input "Topic" -> Branch A (Joke) -> "A joke about Topic"
#               -> Branch B (Poem) -> "A poem about Topic"
# Output: { "joke": "...", "poem": "..." }

map_chain = RunnableParallel({
    "joke": joke_chain,
    "poem": poem_chain
})
```

---

## 2. Architectural Role: The "Fan-Out" Layer

In a RAG system, `RunnableParallel` is typically used at the **Retrieval Step** (The Data Bus).

```python
# The "Context Gathering" Phase
retrieval_step = RunnableParallel({
    "docs": retriever,            # Fetch documents
    "question": RunnablePassthrough() # Pass the question through
})

# The "Generation" Phase
chain = retrieval_step | prompt | model
```

Why?
Because the `prompt` expects `{"context": ..., "question": ...}`.
`RunnableParallel` formats the data exactly how the prompt needs it, running the retrieval asynchronously while preserving the user input.

---

## 3. Implicit vs Explicit

You rarely need to import `RunnableParallel` directly.
LangChain checks if you are piping a **Dictionary**. If so, it auto-converts it.

```python
# Explicit
chain = RunnableParallel({"a": chain_a}) | model

# Implicit (Syntactic Sugar)
chain = {"a": chain_a} | model
```

This makes LCEL code look like JSON configuration, masking the complex async orchestration underneath.

---

## Quick Reference

| Feature | Description |
| :--- | :--- |
| **Input** | A single value (dict, str, etc.). |
| **Output** | A Dictionary `{key: branch_output}`. |
| **Concurrency** | Threads (Sync) or AsyncIO (Async). |
| **Error Handling** | If one branch fails, the whole map fails (by default). |
