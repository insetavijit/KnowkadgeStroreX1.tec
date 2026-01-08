| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC2.1.2.1 RunnableParallel Syntax]]**             | Learn basic syntax                           | RunnableParallel constructor, dict syntax, shorthand notation                   | Use dict syntax or RunnableParallel() to create parallel chains.    |
| **[[LC2.1.2.2 Dictionary-Based Definition]]**         | Define branches with dicts                   | {"key": runnable} format, branch naming, output mapping                         | Define parallel branches as a dictionary of runnables.              |
| **[[LC2.1.2.3 Naming Parallel Branches]]**            | Choose meaningful names                      | Key naming, output access, descriptive names                                    | Name branches clearly for easy output access.                       |
| **[[LC2.1.2.4 Basic Parallel Chain Setup]]**          | Set up first parallel chain                  | Step-by-step setup, simple example, verification                                | Start with simple two-branch parallel chains.                       |
| **[[LC2.1.2.5 Parallel Chains in LCEL Pipelines]]**   | Integrate with LCEL                          | Pipe operator, chaining after parallel, input passing                           | Use parallel chains as steps in larger LCEL pipelines.              |

# Creating Parallel Chains: Syntax & Patterns

Complexity in AI systems usually comes from **Orchestration**.
"Run A, then B. While B runs, run C. When B and C finish, run D."

LCEL solves this via **Implicit Coercion**.

---

## 1. The Explicit Way

If you prefer Type Safety and readability, use the class constructor.

```python
from langchain_core.runnables import RunnableParallel

chain = RunnableParallel(
    context=retriever,
    question=RunnablePassthrough()
)
```

**Pros**: Explicit import clearly signals intent to junior developers.
**Cons**: Verbose.

---

## 2. The Implicit Way (Recommended)

LangChain's pipe `|` operator is overloaded.
If it sees a **Dictionary** on either side, it automatically wraps it in `RunnableParallel`.

```python
# Fully Implicit
chain = (
    {"context": retriever, "question": RunnablePassthrough()} 
    | prompt 
    | model
)
```

**Architectural Insight**:
This pattern turns Python Dictionaries into **Execution Graphs**.
The keys (`context`, `question`) become the **API Contract** for the next step (the prompt).

---

## 3. The Passthrough Trick

A "Branch" usually transforms data. But often, you just want to **Keep** data.
`RunnablePassthrough()` is the identity function `f(x) = x`.

**Pattern: The Context Injection**
Input: `"What is LangChain?"`
Goal: Inject `context` but keep the `question`.

```python
chain = {
    "context": retriever,            # Branch 1: Retrieval (Slow)
    "question": RunnablePassthrough() # Branch 2: Identity (Fast)
}
```

**Output**:
```json
{
    "context": [Document(...)],
    "question": "What is LangChain?"
}
```

This output structure perfectly matches `PromptTemplate.from_template("{question}... {context}")`.

---

## Quick Reference

| Syntax | Behavior | Use Case |
| :--- | :--- | :--- |
| `RunnableParallel({...})` | Parallel Execution | Official / Explicit readability. |
| `{"key": runnable}` | Parallel Execution | Fast prototyping / Clean implementations. |
| `RunnablePassthrough()` | Copy Input | Preserving original user questions. |
