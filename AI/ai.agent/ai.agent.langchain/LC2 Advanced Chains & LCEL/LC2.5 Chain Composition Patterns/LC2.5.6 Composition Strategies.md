| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC2.5.6.1 Sequential vs Parallel Decisions]]**    | Choose between patterns                      | Sequential needs, parallel opportunities, decision criteria                     | Choose sequential for dependencies; parallel for independence.      |
| **[[LC2.5.6.2 Branching Decisions]]**                 | Choose when to branch                        | Conditional needs, specialized handling, routing opportunities                  | Branch when inputs need different handling.                         |
| **[[LC2.5.6.3 Hybrid Patterns]]**                     | Combine multiple patterns                    | Sequential + parallel, branch + parallel, complex flows                         | Combine patterns for complex workflows.                             |
| **[[LC2.5.6.4 Optimization]]**                        | Choose efficient patterns                    | Performance impact, resource usage, latency                                     | Choose patterns that optimize for requirements.                     |
| **[[LC2.5.6.5 Pattern Selection]]**                   | Apply structured selection                   | Decision framework, trade-off analysis, best-fit                                | Apply framework to select appropriate patterns.                     |

# Composition Strategies: The Decision Matrix

Given a task, how do you choose between Sequential, Parallel, and Branching?

---

## 1. The Dependency Test

**Question**: Does Step B need the output of Step A?
*   **Yes** -> Sequential (`A | B`).
*   **No** -> Parallel (`RunnableParallel({A, B})`).

---

## 2. The Specialization Test

**Question**: Does the input type determine the processing logic?
*   **Yes** -> Branch (`RunnableBranch(...)`).
*   **No** -> Linear.

---

## 3. Common Hybrid Patterns

**Retrieve-and-Generate (Sequential First, Then Parallel)**:
```
Query -> Retrieve -> Generate | Summarize | Fact-Check (Parallel)
```

**Classify-Then-Route (Branch First)**:
```
Query -> RunnableBranch(
    (is_code, CodeChain | Linter),
    (is_text, TextChain | Grammar)
)
```

---

## 4. Performance Implications

| Pattern | Latency | Cost |
| :--- | :--- | :--- |
| **Sequential** | Sum of all steps. | Standard. |
| **Parallel** | Max of all branches. | N x Standard (N branches). |
| **Branch** | Single path. | Standard. |

**Key Insight**: Parallel is faster but more expensive (you pay for all branches). Use it when latency is critical and cost is acceptable.

---

## Quick Reference

| Question | Answer | Pattern |
| :--- | :--- | :--- |
| Is Step B dependent on Step A? | Yes | Sequential `|` |
| Can A and B run at the same time? | Yes | Parallel `{}` |
| Does text type change the chain? | Yes | Branch `RunnableBranch` |
