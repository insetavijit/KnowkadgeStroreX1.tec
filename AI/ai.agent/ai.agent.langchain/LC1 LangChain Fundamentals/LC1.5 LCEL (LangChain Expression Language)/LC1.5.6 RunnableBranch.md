| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC1.5.6.1 Conditional Execution]]**               | Execute different paths conditionally        | RunnableBranch class, if/else logic, dynamic routing                            | RunnableBranch enables if/else logic in LCEL chains.                |
| **[[LC1.5.6.2 Branching Logic]]**                     | Define branch conditions                     | Condition functions, branch selection, predicate patterns                       | Define condition functions to select branches.                      |
| **[[LC1.5.6.3 Condition Functions]]**                 | Write branch predicates                      | Boolean returns, input inspection, condition logic                              | Condition functions return True/False to select branch.             |
| **[[LC1.5.6.4 Default Branches]]**                    | Handle fallback cases                        | Default runnable, catch-all logic, no-match handling                            | Always define a default branch for unmatched conditions.            |
| **[[LC1.5.6.5 Decision Trees in LCEL]]**              | Build complex branching                      | Nested branches, multi-level decisions, complex routing                         | Nest RunnableBranch for multi-level decision trees.                 |

# RunnableBranch: The Logic Switch

In traditional Python, you use `if/elif/else`.
In LCEL, since you are building a **Graph**, you cannot use python keywords. You must use a **Routing Node**.

`RunnableBranch` is the "Switch Statement" of the graph.

---

## 1. The Structure

A Branch takes a list of `(Condition, Chain)` tuples and a final `Default Chain`.

```python
from langchain_core.runnables import RunnableBranch

branch = RunnableBranch(
    (lambda x: "math" in x["topic"], math_chain),       # if topic == math
    (lambda x: "history" in x["topic"], history_chain), # elif topic == history
    general_chain                                       # else
)
```

**Architectural Note**:
LangChain evaluates the conditions **in order** (Top to Bottom). The first one that returns `True` wins. The rest are ignored.

---

## 2. The Classification Pattern

The most powerful use of branching is **Semantic Routing**.
You don't route based on keywords (hardcoded); you route based on **Intent**.

This requires a "Classifier Step" *before* the Branch.

```python
# Step 1: The Classifier Chain
classifier_chain = (
    PromptTemplate.from_template(
        "Classify this query into: [billing, technical, sales]. Query: {q}"
    )
    | chat_model
    | StrOutputParser() # Returns "billing", "technical", or "sales"
)

# Step 2: The Routing Logic
route_logic = RunnableBranch(
    (lambda x: "billing" in x["topic"].lower(), billing_chain),
    (lambda x: "technical" in x["topic"].lower(), tech_support_chain),
    sales_chain
)

# Step 3: The Full Pipeline
full_chain = (
    RunnablePassthrough.assign(topic=classifier_chain) # Add classification to state
    | route_logic                                      # Route based on classification
)
```

---

## 3. Performance Considerations

**Latency Warning**:
In the example above, `classifier_chain` calls an LLM. This implies:
1.  **Latency**: T + T_branch.
2.  **Cost**: 2x calls (1 to classify, 1 to answer).

To optimize, use **Lightweight Models** (e.g., `gpt-3.5-turbo` or a local classifier) for the routing step, and reserve the **Heavy Model** (`gpt-4`) for the actual specialized chains.

---

## Quick Reference

| Component | Role |
| :--- | :--- |
| **Condition** | `Callable[[Input], bool]` |
| **Branch** | `Runnable` to execute if condition is true. |
| **Default** | `Runnable` to execute if NO conditions are true. |
