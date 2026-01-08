| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC2.2.3.1 Branch Tuple Syntax]]**                 | Define branch syntax                         | (condition, runnable) tuples, list of branches                                  | Define branches as (condition, runnable) tuples.                    |
| **[[LC2.2.3.2 Condition-Runnable Pairs]]**            | Pair conditions with chains                  | Matching conditions to handlers, pair structure                                 | Each condition pairs with its handler runnable.                     |
| **[[LC2.2.3.3 Branch Ordering]]**                     | Order branches correctly                     | First-match wins, priority order, overlap handling                              | Branches are evaluated in order; first match wins.                  |
| **[[LC2.2.3.4 Syntax Patterns]]**                     | Use common patterns                          | Lambda conditions, RunnableLambda, inline definitions                           | Use lambda functions for simple branch conditions.                  |
| **[[LC2.2.3.5 Branch Readability]]**                  | Write maintainable branches                  | Named conditions, clear structure, documentation                                | Use named functions and clear structure for readability.            |

# Branch Definition: The "Then" Block

The "Branch" part of `RunnableBranch` is simply a Runnable.
It executes **if and only if** its condition is True.

---

## 1. Syntax: The Tuple List

The constructor takes a Variable Argument list of `(condition, runnable)` tuples.

```python
branch = RunnableBranch(
    (condition_a, chain_a),  # If condition_a(input) is True -> run chain_a(input)
    (condition_b, chain_b),
    default_chain
)
```

**Scope Rule**:
The branched runnable receives the **Original Input** passed to `RunnableBranch`.
It does *not* receive the output of the condition function (which is just a boolean).

---

## 2. Priority Ordering

Evaluation is **Sequential**.

```python
# Logic:
branch = RunnableBranch(
    (lambda x: x > 10,  chain_large),  # Evaluated 1st
    (lambda x: x > 5,   chain_medium), # Evaluated 2nd
    chain_small                        # Default
)
```
Input `15` triggers `chain_large`.
Input `8` triggers `chain_medium` (because `8 > 10` is False).

**Architectural Tip**:
Always order specific rules *before* general rules.
Put `lambda x: "python code" in x` *before* `lambda x: "code" in x`.

---

## 3. The "Pass-Through" Branch

Sometimes, if a condition is met, you want to do **Nothing** (just return the input).
This is common for "Filters" that only act on bad data.

```python
# If valid, pass through. If invalid, fix it.
branch = RunnableBranch(
    (is_valid, RunnablePassthrough()), 
    fix_chain
)
```

**Pattern**: The **Guardrail**.
1. Input -> 2. Branch (If Safe: Pass. If Unsafe: Block) -> 3. LLM.

---

## Quick Reference

| Component | Input Received | Output Expected |
| :--- | :--- | :--- |
| **Branch Runnable** | The original input `x`. | Any `y` (Must match downstream schema). |
| **PassThrough** | The original input `x`. | The original input `x`. |
| **Lambda Branch** | The original input `x`. | Calculated value. |
