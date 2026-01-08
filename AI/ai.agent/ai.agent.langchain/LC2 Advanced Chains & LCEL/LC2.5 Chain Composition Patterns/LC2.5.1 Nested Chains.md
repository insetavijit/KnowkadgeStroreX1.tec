| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC2.5.1.1 Chains Within Chains]]**                | Create hierarchical chains                   | Nested composition, sub-chains, encapsulation                                   | Nest chains within chains for hierarchical structure.               |
| **[[LC2.5.1.2 Hierarchical Composition]]**            | Build layered architectures                  | Multiple levels, abstraction layers, contained complexity                       | Build layered chains for managing complexity.                       |
| **[[LC2.5.1.3 Nesting Depth]]**                       | Manage nesting levels                        | Depth limits, debugging challenges, readability                                 | Limit nesting depth for maintainability.                            |
| **[[LC2.5.1.4 Readability Considerations]]**          | Keep nested chains readable                  | Naming, documentation, extraction, refactoring                                  | Extract named sub-chains for readability.                           |
| **[[LC2.5.1.5 When to Nest]]**                        | Choose nesting appropriately                 | Reuse opportunities, encapsulation needs, complexity hiding                     | Nest when encapsulation and reuse justify complexity.               |

# Nested Chains: Hierarchical Abstraction

Just like functions can call other functions, Chains can contain other Chains.
This is how you build **Large AI Architectures** from smaller, tested components.

---

## 1. The "Sub-Chain" Pattern

```python
# Define a small, reusable unit
rag_core = retriever | context_formatter | llm | parser

# Wrap it in a larger workflow
full_application = (
    input_validator
    | user_history_injector
    | rag_core                    # <-- Nested chain
    | response_formatter
    | safety_filter
)
```

**Benefit**: `rag_core` can be tested and versioned independently.

---

## 2. Encapsulation: Hiding Complexity

When you expose `full_application.invoke()`, the consumer doesn't need to know about the 5 internal steps. They see a single "black box".

This is the **Facade Pattern** from software architecture, applied to AI.

---

## 3. Depth Limits (The 3-Level Rule)

In practice, avoid nesting deeper than **3 levels**.

*   **Level 1**: Application Entry Point.
*   **Level 2**: Domain-Specific Sub-Chains (RAG, Router).
*   **Level 3**: Primitive Combinations (Prompt | LLM | Parser).

Deeper nesting makes debugging traces unreadable in tools like LangSmith.

---

## Quick Reference

| Nesting Level | Abstraction | Example |
| :--- | :--- | :--- |
| **0** | Primitives | `ChatOpenAI`, `PromptTemplate` |
| **1** | Composed Chain | `prompt | llm | parser` |
| **2** | Feature Module | `RAGModule`, `RouterModule` |
| **3** | Application | `FullChatbotApp` |
