| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC1.5.4.1 Passing Data Through Chains]]**         | Forward data unchanged                       | RunnablePassthrough class, identity function, data forwarding                   | RunnablePassthrough forwards input data unchanged.                  |
| **[[LC1.5.4.2 Data Injection]]**                      | Add new data mid-chain                       | assign() method, adding fields, enriching context                               | Use assign() to add new fields to the data stream.                  |
| **[[LC1.5.4.3 Combining with Other Runnables]]**      | Use passthrough in pipelines                 | Parallel composition, merging data, complex patterns                            | Combine passthrough with other runnables strategically.             |
| **[[LC1.5.4.4 Passthrough Patterns]]**                | Apply common passthrough idioms              | RAG patterns, context preservation, input forwarding                            | Passthrough is essential for RAG and context patterns.              |
| **[[LC1.5.4.5 Preserving Context]]**                  | Maintain original input                      | Keeping original question, adding retrieval results, final formatting           | Use passthrough to preserve original context alongside new data.    |

# RunnablePassthrough: The Data Bus

In a linear pipeline `A | B | C`, step B consumes the output of A and destroys it to create the input for C.
But what if Step C needs data from Step A?

**RunnablePassthrough** is the "Wire" that lets you route data *around* components.

---

## 1. The Identity Function (`x -> x`)

On its own, `RunnablePassthrough()` does nothing. It takes the input and returns it exactly as is.
This is useful when constructed inside a `RunnableParallel` to keep a copy of the original input.

```python
from langchain_core.runnables import RunnableParallel, RunnablePassthrough

# The "Fork" Pattern
chain = RunnableParallel(
    original=RunnablePassthrough(), # Keep the input "bears"
    modified=lambda x: x.upper()    # Modify the input to "BEARS"
)

chain.invoke("bears")
# Output: {'original': 'bears', 'modified': 'BEARS'}
```

---

## 2. The Context Accumulator (`.assign`)

This is the most critical method in all of LCEL. It is used in 99% of RAG applications.
You have a dictionary state (Context), and you want to **add** a key without deleting the others.

```python
# Function that fetches extra data
def get_user_data(x):
    return "User: Bob"

# State: {"question": "What is LCEL?"}

chain = (
    RunnablePassthrough.assign(
        user_info=get_user_data  # Runs function, adds result to 'user_info'
    )
    # The Stream is now: {"question": "...", "user_info": "User: Bob"}
    | prompt 
    | model
)
```

**Architectural Mental Model**:
Think of `.assign()` like `git commit` or `pandas.df.assign()`. It creates a new version of the state with the added modifications, preserving the history.

---

## 3. The RAG Topology

The "Classical RAG" chain is built entirely on this topology.

```python
rag_chain = (
    {"context": retriever, "question": RunnablePassthrough()} 
    | prompt 
    | model 
    | StrOutputParser()
)
```

1.  **Split**: The input (string) enters the dictionary.
2.  **`question`**: The string passes through `RunnablePassthrough` -> becomes value of `question` key.
3.  **`context`**: The same string passes through `retriever` -> becomes value of `context` key.
4.  **Merge**: The resulting dictionary `{'question': '...', 'context': [...]}` hits the prompt.

---

## 4. Difference from RunnableParallel

*   `RunnableParallel({...})`: **Resets** the dictionary. It creates a *new* dict containing *only* the keys you specify.
*   `RunnablePassthrough.assign(...)`: **Mutates** (copies) the dictionary. It keeps *all* old keys and adds the new ones.

**Rule of Thumb**:
*   Use `Parallel` when formatting the final output or at the very start (converting String -> Dict).
*   Use `assign` in the middle of a chain to carry context forward through variable transformations.

---

## Quick Reference

| Method | Syntax | Effect |
| :--- | :--- | :--- |
| **Identity** | `RunnablePassthrough()` | Input `x` -> Output `x`. |
| **Assign** | `.assign(k=v)` | Input `dict` -> Output `dict + {k:v}`. |
| **Parallel** | `RunnableParallel(k=v)` | Input `x` -> Output `{k:v(x)}`. |
