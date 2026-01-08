| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC2.2.1.1 What Is RunnableBranch]]**              | Define branching concept                     | RunnableBranch class, conditional execution, decision points                    | RunnableBranch executes different chains based on conditions.       |
| **[[LC2.2.1.2 Conditional Execution Concept]]**       | Understand if/else for chains                | Condition evaluation, branch selection, dynamic paths                           | Conditional execution chooses paths at runtime.                     |
| **[[LC2.2.1.3 Branching vs Linear Chains]]**          | Compare execution modes                      | When to branch, complexity trade-offs, maintainability                          | Use branching when inputs require different processing.             |
| **[[LC2.2.1.4 When to Use Branching]]**               | Identify appropriate scenarios               | Different intents, varied inputs, specialized handlers                          | Branching adapts processing to input intent.                        |
| **[[LC2.2.1.5 Branching Benefits]]**                  | Summarize advantages                         | Specialized handling, efficiency, cleaner code                                  | Branching enables specialized, efficient processing paths.          |

# RunnableBranch: The Control Flow Layer

In standard Python, you use `if / elif / else`.
In LCEL, you use `RunnableBranch`.

It is the primitive for **Conditional Logic** within a chain, allowing a single invocation to route to different downstream runnables based on the input state.

---

## 1. The Core Abstraction

`RunnableBranch` behaves exactly like a Python `case` statement.
It takes a list of `(condition, branch)` tuples and a final `default_branch`.

```python
from langchain_core.runnables import RunnableBranch

# Logic:
# if query has "math" -> run math_chain
# elif query has "code" -> run coding_chain
# else -> run general_chain

branch = RunnableBranch(
    (lambda x: "math" in x["topic"], math_chain),
    (lambda x: "code" in x["topic"], coding_chain),
    general_chain  # The Default (Else)
)
```

**Architectural Note**:
Conditions are **Predicates** (Functions that return bool). They are evaluated sequentially. The first one to return `True` wins.

---

## 2. The Agentic Boundary

A common confusion is: "Is `RunnableBranch` an Agent?"
**No.**

*   **RunnableBranch (Router)**: The logic is **Hardcoded** by the developer. (If *keyword* X, do Y). It is deterministic and cheap.
*   **Agent**: The logic is **Inferred** by an LLM. (Here is a tool, decide if you need it). It is probabilistic and expensive.

**Rule of Thumb**:
Always prefer `RunnableBranch` if you can define the rules in code. Only use Agents when the rules are fuzzy.

---

## 3. Implicit vs Explicit

Just like `RunnableParallel`, you rarely import `RunnableBranch` directly.
You "route" by combining simple runnables.

However, explicitly defining branches is crucial for **Observability**.
In LangSmith, a `RunnableBranch` shows up as a "Decision Diamond," making it clear which path execution took.

---

## Quick Reference

| Component | Equivalent | Behavior |
| :--- | :--- | :--- |
| **Condition** | `if condition:` | Predicate function `f(x) -> bool`. |
| **Branch** | `then: ...` | Runnable `f(x) -> y`. |
| **Default** | `else: ...` | Fallback Runnable. |
