| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC1.4.1.1 Chain Concept]]**                       | Understand what chains represent             | Chains as workflows, multi-step processing, abstraction over operations         | Chains compose multiple operations into a single workflow.          |
| **[[LC1.4.1.2 Composing LLM Calls]]**                 | Combine LLM with other operations            | Pre-processing, post-processing, chained LLM calls                              | Chains allow combining LLM calls with data transformations.         |
| **[[LC1.4.1.3 Chain as Workflow]]**                   | View chains as pipelines                     | Input-process-output, data flow, orchestration                                  | Think of chains as data processing pipelines.                       |
| **[[LC1.4.1.4 Chain vs Single LLM Call]]**            | Know when to use chains                      | Complexity threshold, multi-step needs, simple vs complex tasks                 | Use chains when a task needs multiple processing steps.             |
| **[[LC1.4.1.5 Chain Philosophy]]**                    | Understand design principles                 | Modularity, composability, reusability, separation of concerns                  | Chains embody composable, modular design principles.                |

# What Are Chains? The Glue Layer

An LLM on its own is just a text generator.
An **Application** is a sequence of logic:
`User Input -> Validation -> Retrieval -> Formatting -> LLM -> Parsing -> Database`.

A **Chain** is the architectural construct that binds these steps together into a single, executable Unit of Work.

---

## 1. The Core Philosophy: "Pipes and Filters"

LangChain borrows its core mental model from Unix.
Just as you pipe commands in bash (`ls | grep .py | wc -l`), you pipe cognitive steps in LangChain.

**The Evolution**:
1.  **Legacy Chains** (`LLMChain`): Class-based wrappers. (Deprecated but ubiquitous).
2.  **LCEL** (LangChain Expression Language): The modern, functional syntax using the `|` operator.

> **Architectural Decision**: New projects should use **LCEL** exclusively. Legacy chains are harder to inspect, type-check, and stream.

---

## 2. Anatomy of a Chain

A Chain is simply a sequence of **Runnables**.
A `Runnable` is anything that implements `.invoke(x)`.

```python
# The "Hello World" Chain
chain = prompt | model | parser
```

1.  **Prompt**: `Dict -> StringPromptValue` (Transforms data into schema).
2.  **Model**: `StringPromptValue -> AIMessage` (Performs cognition).
3.  **Parser**: `AIMessage -> String` (Extracts content).

**Why this matters**:
Because the input types and output types match (Covariance), you can swap the Model (OpenAI -> Anthropic) or the Prompt (English -> French) without changing the "Wiring" of the application.

---

## 3. Atomic vs Composite Chains

### Atomic Chains
The smallest unit of work.
*   **Prompt**: Pure logic.
*   **Retriever**: Pure IO.
*   **Tool**: Pure Compute.

### Composite Chains
A chain that contains other chains.
*   **SequentialChain**: Linear `A -> B -> C`.
*   **RouterChain**: Conditional `if X then Chain A else Chain B`.

**Mental Model**:
Treat Chains like **Lego Bricks**. You can build a small "Summary Chain" and then plug that entire chain into a larger "Document Analysis Chain" as if it were a single function.

---

## 4. The Data Flow (State)

The hardest part of Chains is managing **State**.
In a Python function, you have variables scope.
In a Chain, you have a **Dictionary** that flows through the pipe.

**Input**: `{"topic": "bears"}`
**Step 1 (Prompt)**: Consumes "topic", produces "String".
**Step 2 (Model)**: Consumes "String", produces "Message".

*Wait, where did "topic" go?*
In simple chains, it is lost. In complex chains (using `RunnablePassthrough`), you must explicitly carry the state forward.

```python
# Preserving State
chain = (
    {"context": retriever, "question": RunnablePassthrough()} 
    | prompt 
    | model
)
```

---

## Quick Reference

| Term | Definition | Unix Analogy |
| :--- | :--- | :--- |
| **Chain** | A generic sequence of steps. | A Script. |
| **Runnable** | A single step (Prompt/Model). | A Command (`grep`). |
| **LCEL** | The syntax `|`. | The Pipe `|`. |
| **Invocation** | Running the chain. | Executing `./script`. |
