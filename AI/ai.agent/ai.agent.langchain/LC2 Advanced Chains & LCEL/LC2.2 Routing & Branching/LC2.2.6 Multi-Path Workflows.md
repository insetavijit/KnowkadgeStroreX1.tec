| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC2.2.6.1 Complex Branching Scenarios]]**         | Handle sophisticated routing                 | Multiple decision points, layered conditions, comprehensive routing             | Handle complex scenarios with multi-level branching.                |
| **[[LC2.2.6.2 Nested Branches]]**                     | Branch within branches                       | Sub-branches, hierarchical decisions, deep nesting                              | Nest branches for hierarchical decision making.                     |
| **[[LC2.2.6.3 Combining Routing with Parallel]]**     | Mix patterns                                 | Branch then parallel, parallel then branch, hybrid patterns                     | Combine branching and parallel for complex workflows.               |
| **[[LC2.2.6.4 Workflow Graphs]]**                     | Think in graph terms                         | DAG patterns, flow visualization, graph-like chains                             | Visualize complex routing as workflow graphs.                       |
| **[[LC2.2.6.5 Managing Complexity]]**                 | Keep routing maintainable                    | Modularization, documentation, testing strategies                               | Manage complex routing with modular, documented design.             |

# Multi-Path Workflows: Thinking in Graphs

Once you combine `RunnableParallel` (Horizontal) and `RunnableBranch` (Vertical), you are no longer writing "chains". You are building **DAGs** (Directed Acyclic Graphs).

---

## 1. Nested Branches (Decision Trees)

You can nest a router *inside* a router.

```python
# Level 1: Intent
main_router = RunnableBranch(
    (is_support, support_chain), # -> Level 2: Support Type
    (is_sales, sales_chain),
    default_chain
)

# Level 2 (Support)
support_chain = RunnableBranch(
    (is_technical, tech_support),
    (is_billing, billing_support),
    general_support
)
```

**Architecture**: Hierarchical Classification.
This follows the "Divider & Conquer" strategy. It is cheaper to first decide "Support vs Sales" (Keyword Check) before running the heavier "Technical vs Billing" (LLM Check).

---

## 2. Route-Then-Fan-Out

A common pattern: First decide *what* to do, then do it *massively*.

**Scenario**: Research Task.
1.  **Router**: Is this "Law" or "Medicine"?
2.  **Parallel**: If "Law", search 3 Legal DBs. If "Medicine", search 3 Medical DBs.

```python
law_branch = RunnableParallel({...}) # Searches LexisNexis
med_branch = RunnableParallel({...}) # Searches PubMed

workflow = RunnableBranch(
    (is_law, law_branch),
    (is_med, med_branch),
    general_search
)
```

---

## 3. Fan-Out-Then-Route

**Scenario**: Safety Filtering.
1.  **Parallel**: Run the Query *AND* run a Moderation Check at the same time.
2.  **Router**: If Moderation fails, block the Query result.

```python
step_1 = RunnableParallel({
    "answer": generation_chain,
    "safety": moderation_chain
})

def route_safety(inputs):
    if inputs["safety"] == "UNSAFE":
        return warning_chain
    # Pass the already generated answer
    return RunnablePassthrough() 

workflow = step_1 | RunnableLambda(route_safety)
```

**Architectural Insight**:
This is a **Speculative Execution** pattern. We generate the answer *before* we know if it's safe, to save latency. If it turns out unsafe, we just throw away the work.

---

## Quick Reference

| Pattern | Shape | Use Case |
| :--- | :--- | :--- |
| **Nested Router** | Tree | Customer Support Bots. |
| **Route -> Parallel** | Fork | Domain-Specific Search. |
| **Parallel -> Route** | Diamond | Guardrails / Moderation. |
