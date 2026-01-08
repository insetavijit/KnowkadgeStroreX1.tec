| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC2.5.2.1 Breaking Chains into Modules]]**        | Decompose large chains                       | Module extraction, logical grouping, separation of concerns                     | Break large chains into focused module chains.                      |
| **[[LC2.5.2.2 Single Responsibility]]**               | One purpose per chain                        | Focused chains, clear purpose, minimal scope                                    | Each chain module should have single responsibility.                |
| **[[LC2.5.2.3 Module Interfaces]]**                   | Define clear I/O contracts                   | Input/output specs, type definitions, documentation                             | Define clear input/output interfaces for modules.                   |
| **[[LC2.5.2.4 Documentation]]**                       | Document modules                             | Usage docs, interface specs, examples                                           | Document each module's purpose and interface.                       |
| **[[LC2.5.2.5 Clean Architecture]]**                  | Apply architecture principles                | Dependency direction, abstraction, testability                                  | Apply clean architecture principles to chain modules.               |

# Modular Chain Design: Clean Architecture for AI

The same principles that make backend code maintainable apply to AI chains.

---

## 1. Single Responsibility Principle

Each module should do **One Thing**.

*   **Good**:
    *   `retrieval_module`: Takes query, returns docs.
    *   `generation_module`: Takes docs + query, returns answer.
    *   `citation_module`: Takes answer, returns formatted answer with sources.

*   **Bad**:
    *   `do_everything_chain`: Retrieves, generates, formats, logs, and sends email.

---

## 2. Clean Interfaces (Input/Output Contracts)

Define what each module *needs* and what it *provides*.

```python
# Module A: Retrieval
# Input: {"query": str}
# Output: {"docs": list[Document]}

# Module B: Generation
# Input: {"query": str, "docs": list[Document]}
# Output: {"answer": str}
```

If your output doesn't match the next module's input, use `RunnablePassthrough.assign()` or a small `RunnableLambda` adapter.

---

## 3. Dependency Inversion

Modules should not import each other. They should communicate via **Interfaces**.

```python
# Good: Pass the LLM as a parameter
def create_generation_module(llm: Runnable):
    return prompt | llm | parser

# Bad: Hard-code the LLM inside
def create_generation_module():
    from langchain_openai import ChatOpenAI
    llm = ChatOpenAI()  # Tightly coupled!
    return prompt | llm | parser
```

**Benefit**: Allows swapping models without changing module code.

---

## Quick Reference

| SOLID Principle | Chain Equivalent |
| :--- | :--- |
| **Single Responsibility** | One chain = one task. |
| **Open/Closed** | Extend via composition, not modification. |
| **Liskov Substitution** | Any `Runnable[str, dict]` is interchangeable. |
| **Interface Segregation** | Small, focused input schemas. |
| **Dependency Inversion** | Pass LLMs/Retrievers as arguments. |
