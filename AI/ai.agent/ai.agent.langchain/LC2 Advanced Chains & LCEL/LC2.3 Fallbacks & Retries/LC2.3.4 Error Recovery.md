| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC2.3.4.1 Catching Exceptions]]**                 | Trap errors in chains                        | try/except, exception types, error categorization                               | Catch exceptions to implement recovery logic.                       |
| **[[LC2.3.4.2 Error Types]]**                         | Classify chain errors                        | API errors, parsing errors, timeout errors, custom errors                       | Classify errors to apply appropriate recovery.                      |
| **[[LC2.3.4.3 Recovery Strategies]]**                 | Implement error recovery                     | Retry, fallback, default value, user notification                               | Choose recovery strategy based on error type.                       |
| **[[LC2.3.4.4 Partial Recovery]]**                    | Salvage partial results                      | Partial data, continuing with available, best-effort                            | Salvage partial results when full recovery fails.                   |
| **[[LC2.3.4.5 Logging Failures]]**                    | Track recovery events                        | Error logging, failure metrics, debugging info                                  | Log all failures for debugging and monitoring.                      |

# Error Recovery: Self-Correcting Chains

This is a specific pattern: Use the **Error Message** to help the LLM fix itself.
This is the core of `OutputFixingParser` and `RetryOutputParser` (LC1.6.7).

---

## 1. The Correction Prompt Pattern

When an LLM returns malformed JSON, you can *show it the error* and ask it to retry.

```python
correction_prompt = """
The previous output failed to parse. Error: {error}

Original output:
{completion}

Please produce valid JSON matching this schema: {schema}
"""
```

**Architecture**: The "Inner Loop".
Instead of just retrying blindly, the retry includes **Context** about *why* things failed. This is far more likely to succeed.

---

## 2. Exception Hooks

LangChain runnables provide hooks to intercept exceptions.

```python
# Using RunnableLambda to catch and handle
def safe_call(x):
    try:
        return original_chain.invoke(x)
    except OutputParserException as e:
        # Log it, then try to fix it
        return correction_chain.invoke({"error": str(e), "input": x})

safe_chain = RunnableLambda(safe_call)
```

This is a manual pattern, but it's useful for **Domain-Specific** error handling.

---

## 3. Partial Recovery (Best Effort)

Sometimes, 3 out of 5 parallel branches succeed.
Do you throw away the 3 good results? Or return a partial answer?

**Pattern**: Catch errors within the branch, return `None`, then filter.

```python
def safe_branch(chain):
    def wrapper(x):
        try:
            return chain.invoke(x)
        except Exception:
            return None
    return RunnableLambda(wrapper)

parallel = RunnableParallel({
    "a": safe_branch(chain_a),
    "b": safe_branch(chain_b),
})

# Output: {"a": "...", "b": None}
```

The downstream consumer can then filter out `None` values.

---

## Quick Reference

| Strategy | When | Outcome |
| :--- | :--- | :--- |
| **Retry** | Transient Error | Same action, delay. |
| **Correction** | Semantic Error | New prompt with context. |
| **Partial** | Parallel Failure | Return non-null results. |
