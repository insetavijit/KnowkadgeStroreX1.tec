| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC2.1.8.1 Handling Branch Failures]]**            | Manage failing branches                      | Exception handling, failure isolation, error propagation                        | Handle branch failures to prevent total chain failure.              |
| **[[LC2.1.8.2 Partial Success Handling]]**            | Continue with partial results                | Optional branches, default values, degraded operation                           | Design for partial success when branches may fail.                  |
| **[[LC2.1.8.3 Error Propagation]]**                   | Control error flow                           | First-error-fails, all-errors-collected, error strategies                       | Choose error propagation strategy for parallel chains.              |
| **[[LC2.1.8.4 Resilient Parallel Chains]]**           | Build fault-tolerant chains                  | Fallbacks per branch, retry logic, circuit breakers                             | Add per-branch fallbacks for resilient parallel chains.             |
| **[[LC2.1.8.5 Error Logging in Parallel]]**           | Track failures effectively                   | Per-branch logging, error aggregation, debugging parallel errors                | Log per-branch errors for effective parallel debugging.             |

# Parallel Error Handling: Survive the Crash

When you run 5 things at once, the probability of failure increases 5x.
By default, `RunnableParallel` behaves like `asyncio.gather`: **Fail Fast**.
If one branch errors, the whole dictionary throws.

---

## 1. The Branch Fallback (Circuit Breaker)

To prevent a single bad API call from crashing your entire app, wrap the *Branch* in a fallback.

```python
# Create a fallback that returns a "Safe" value
safe_fallback = RunnableLambda(lambda x: "Service Unavailable")

chain = RunnableParallel({
    "reliable": chain_a,
    "unreliable": chain_b.with_fallbacks([safe_fallback])
})
```

**Outcome**:
If `chain_b` fails, the output is `{"reliable": "...", "unreliable": "Service Unavailable"}`.
The execution continues.

---

## 2. Silent Failures (Returning None)

Sometimes you don't even want a string message. You effectively want to "catch and ignore".

```python
def silent_catch(err):
    # Log the error but return None
    print(f"Branch failed: {err}")
    return None

chain = RunnableParallel({
    "critical": chain_a,
    "optional": chain_b.with_fallbacks([RunnableLambda(silent_catch)])
})
```

**Architecture**:
This is common for "Side Effects" (e.g., "Also generate a summary for the dashboard"). If the summary fails, the user shouldn't know.

---

## 3. Retrying Specific Branches

You can also apply retries per-branch.

```python
chain = RunnableParallel({
    "fast_api": chain_a,
    "flaky_api": chain_b.with_retry(stop_after_attempt=3)
})
```

**Important**:
This retry logic happens **Concurrently**. `chain_a` might finish while `chain_b` is on its 2nd retry attempt. The final result waits for both.

---

## Quick Reference

| Strategy | Behavior | Use Case |
| :--- | :--- | :--- |
| **Default** | Exception raised immediately. | Critical dependencies. |
| **Fallback** | Returns default value. | UI Features (Widgets). |
| **Retry** | Retries N times, then raises. | Network flakes. |
