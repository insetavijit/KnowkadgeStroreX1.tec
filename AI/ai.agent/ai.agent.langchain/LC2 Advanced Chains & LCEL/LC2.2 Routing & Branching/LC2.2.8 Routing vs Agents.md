| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC2.2.8.1 When to Use Routing]]**                 | Choose deterministic routing                 | Known categories, predictable inputs, fast decisions                            | Use routing when conditions are deterministic and known.            |
| **[[LC2.2.8.2 When to Use Agents]]**                  | Choose LLM-driven routing                    | Ambiguous inputs, complex decisions, dynamic categories                         | Use agents when routing requires LLM reasoning.                     |
| **[[LC2.2.8.3 Deterministic vs LLM Routing]]**        | Compare approaches                           | Speed, accuracy, cost, predictability trade-offs                                | Deterministic is faster; LLM routing is more flexible.              |
| **[[LC2.2.8.4 Hybrid Approaches]]**                   | Combine both methods                         | LLM for classification, routing for execution                                   | Use LLM to classify, then deterministic routing.                    |
| **[[LC2.2.8.5 Decision Framework]]**                  | Apply structured choice                      | Decision tree, evaluation criteria, best-fit selection                          | Apply framework to choose routing vs agent approach.                |

# Routing vs Agents: The Complexity Boundary

When does a "Smart Chain" become an "Agent"?
The industry definition is fuzzy, but architecturally, it's clear.

---

## 1. The Definitions

**Router (Flow Engineering)**:
The developer writes the graph. The edges are fixed. Only the *path choice* is dynamic.
*   "If A, go to B. Else go to C."

**Agent (Autonomous Loop)**:
The developer provides a toolbox. The LLM writes the graph at runtime.
*   "Here is a Calculator. Solve this problem however you want."

---

## 2. The Trade-Off Matrix

| Feature | Router | Agent |
| :--- | :--- | :--- |
| **Control** | High (Developer defined) | Low (LLM defined) |
| **Cost** | Low (Single pass) | High (Multiple loops) |
| **Reliability** | **Deterministic** | **Probabilistic** |
| **Debugging** | Easy (Traceable) | Hard (Why did it do that?) |

**Architectural Advice**:
Start with a **Router**. Only upgrade to an **Agent** if you find yourself writing 50+ branches or if the user requests are truly unpredictable.

---

## 3. The Hybrid Pattern (Router-Guided Agents)

The best systems use Routers to scope the problem for Agents.

**Scenario**: Customer Service for a Bank.
1.  **Router**: Determines topic (Mortgage vs Credit Card).
2.  **Specialized Agent**:
    *   If Mortgage: Launch "Mortgage Agent" (Has access to rate tables).
    *   If Card: Launch "Card Agent" (Has access to transaction history).

This prevents the "Credit Card Agent" from hallucinating about interest rates, because it simply *doesn't have those tools*.

---

## Quick Reference

| Symptom | Diagnosis | Prescription |
| :--- | :--- | :--- |
| "I have 50 if/else statements." | Too Complex. | Upgrade to **Agent**. |
| "My Agent is looping forever." | Too Unconstrained. | Downgrade to **Router**. |
| "I need 100% reliability." | Probabilistic. | Use **Router** (Hardcode it). |
