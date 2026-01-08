| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC1.5.7.1 Building Complex Chains]]**             | Combine many components                      | Multi-step pipelines, varied operations, comprehensive workflows                | Compose complex chains by combining multiple Runnables.             |
| **[[LC1.5.7.2 Nested LCEL Expressions]]**             | Create hierarchical chains                   | Sub-chains, grouped operations, parenthetical grouping                          | Nest LCEL expressions for hierarchical composition.                 |
| **[[LC1.5.7.3 Modular Design]]**                      | Build reusable chain modules                 | Chain factories, named chains, importable components                            | Design chains as modular, reusable components.                      |
| **[[LC1.5.7.4 Reusable Components]]**                 | Create a chain library                       | Common patterns, shared utilities, standardized interfaces                      | Build a library of reusable LCEL components.                        |
| **[[LC1.5.7.5 Composition Patterns]]**                | Apply advanced composition                   | Parallel execution, RunnableParallel, complex data flows                        | Use RunnableParallel for concurrent execution paths.                |

# Chain Composition with LCEL: The Orchestra

You have the instruments:
*   `|` (Sequence)
*   `.assign` (Context)
*   `RunnableParallel` (Concurrency)
*   `RunnableBranch` (Logic)

Now we conduct the orchestra. This file covers the **Standard Architectural Patterns** for production applications.

---

## 1. The Gather-Process-Scatter Pattern

This is the most common pattern for RAG.
1.  **Gather**: Collect Context and History.
2.  **Process**: Send to LLM.
3.  **Scatter**: Format output for UI.

```python
# 1. Gather (Parallel Input)
inputs = RunnableMap({
    "context": retriever,
    "question": RunnablePassthrough()
})

# 2. Process (The Thinking)
cognition = prompt | model | StrOutputParser()

# 3. Scatter (Format)
final_chain = inputs | cognition
```

**Architectural Insight**:
Notice how `inputs` is a self-contained unit. You can mock it in unit tests easily (`inputs.invoke("test")`) to verify your retrieval without paying for the LLM call.

---

## 2. The Loop Pattern (Self-Correction)

Standard DAGs are acyclic (no loops). But Agents need loops.
How do you do loops in LCEL?
**Answer**: You don't. You helper functions that *return* LCEL chains recursively, or you use `LangGraph` (which is a different library).

However, for simple "Retry" logic, you can use `.with_retry()` or generic python loops that invoke chains.

```python
# Simple Retry Logic
safe_chain = chain.with_retry(stop_after_attempt=3)
```

---

## 3. The "Router" Pattern (The Multi-Agent Facade)

A single endpoint that delegates to specialized experts.

```python
# The Specialized Experts
billing = billing_prompt | model
sales = sales_prompt | model

# The Router
router = RunnableBranch(
    (lambda x: x["topic"] == "billing", billing),
    (lambda x: x["topic"] == "sales", sales),
    default_chain
)

# The Composition
chain = (
    RunnablePassthrough.assign(topic=classifier_chain) 
    | router
)
```

---

## 4. Visualization (Mermaid)

LCEL chains can visualize themselves. This is critical for documentation.

```python
chain.get_graph().print_ascii()
```

Output:
```text
           +-------------+
           | Input       |
           +-------------+
                  *
                  *
          +----------------+
          | RunnableMap    |
          +----------------+
             *          *
           *              *
    +----------+      +-----------+
    | Retriever|      | Passthrough|
    +----------+      +-----------+
             *          *
           *              *
          +----------------+
          | PromptTemplate |
          +----------------+
```

---

## Quick Reference

| Pattern | LCEL Syntax |
| :--- | :--- |
| **Pipeline** | `A \| B \| C` |
| **Fan-Out** | `RunnableParallel(a=A, b=B)` |
| **Fan-In** | `Parallel \| Prompt` |
| **Conditional** | `RunnableBranch` |
| **Fallbacks** | `A.with_fallbacks([B])` |
