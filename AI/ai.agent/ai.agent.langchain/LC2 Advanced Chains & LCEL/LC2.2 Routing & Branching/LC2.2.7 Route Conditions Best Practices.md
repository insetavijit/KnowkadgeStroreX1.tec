| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC2.2.7.1 Clear Condition Logic]]**               | Write understandable conditions              | Single responsibility, clear naming, simple logic                               | Write conditions with clear, single-purpose logic.                  |
| **[[LC2.2.7.2 Avoiding Overlap]]**                    | Prevent ambiguous routing                    | Mutually exclusive conditions, no ambiguity, clear boundaries                   | Ensure conditions are mutually exclusive to avoid ambiguity.        |
| **[[LC2.2.7.3 Testable Conditions]]**                 | Make conditions unit testable                | Isolated functions, injectable dependencies, test fixtures                      | Design conditions as independently testable functions.              |
| **[[LC2.2.7.4 Documentation]]**                       | Document routing logic                       | Condition descriptions, flow diagrams, decision tables                          | Document routing logic clearly for maintainability.                 |
| **[[LC2.2.7.5 Maintainable Routing]]**                | Build for the future                         | Extensible design, refactoring patterns, code review                            | Design routing for easy extension and maintenance.                  |

# Route Conditions: Deterministic Best Practices

The biggest mistake developers make is putting **Fuzzy Logic** into **Hardcoded Routers**.
If your router depends on `if "important" in text`, it will fail.

---

## 1. Probabilistic vs Deterministic

**Probabilistic (Semantic Routing)**:
*   Uses Embeddings.
*   "Is this text effectively similar to 'Refund Request'?"
*   Good for: User Intent.

**Deterministic (Keyword Routing)**:
*   Uses RegEx / Exact Match.
*   "Does this text contain the string 'refund'?"
*   Good for: Tool Outputs / Structured Data.

**Best Practice**:
Use Deterministic Routing whenever possible. It is 1000x faster and easier to debug. Only resort to Semantic Routing when the user input is unstructured relative to your triggers.

---

## 2. Order Matters (The Waterfall)

Since `RunnableBranch` evaluates sequentially, you must order from **Specific** to **Generic**.

**Bad**:
1. `is_question` (Matches everything)
2. `is_math_question` (Never reached)

**Good**:
1. `is_math_question`
2. `is_question`

---

## 3. The "State Validator" Pattern

Don't just check text strings. Check the **State Object**.

```python
def is_ready_for_final_answer(state):
    # Complex business logic
    has_answer = "final_answer" in state
    is_safe = state.get("safety_score", 0) > 0.9
    steps_taken = len(state.get("steps", []))
    
    return has_answer and is_safe and steps_taken < 10
```

By extracting this logic into a pure function `(dict) -> bool`, you can:
1.  Unit Test it (without mocking LLMs).
2.  Reuse it in multiple branches.

---

## Quick Reference

| Smell | Fix |
| :--- | :--- |
| **Stringly Typed Logic** | Use Pydantic objects or Enums in state. |
| **Huge Lambda** | Extract to a named function `def check_x(s):`. |
| **Nested If/Else** | Flatten into distinct `RunnableBranch` levels. |
