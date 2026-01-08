| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC2.3.2.1 With Fallbacks Method]]**               | Use with_fallbacks()                         | .with_fallbacks() method, syntax, basic usage                                   | Call .with_fallbacks() to add fallback chains.                      |
| **[[LC2.3.2.2 Fallback List]]**                       | Define multiple fallbacks                    | List of fallbacks, sequential try, ordered backups                              | Provide list of fallbacks in priority order.                        |
| **[[LC2.3.2.3 Fallback Order]]**                      | Order fallbacks correctly                    | Try order, reliability vs cost, speed considerations                            | Order fallbacks by reliability and cost.                            |
| **[[LC2.3.2.4 Multiple Fallbacks]]**                  | Chain many backups                           | Cascading failures, deep fallback chains, final resort                          | Chain multiple fallbacks for maximum resilience.                    |
| **[[LC2.3.2.5 Fallback Configuration]]**              | Configure fallback behavior                  | exceptions_to_handle, fallback conditions                                       | Configure which exceptions trigger fallbacks.                       |

# Defining Fallback Chains: The Backup Plan

The key insight: Fallbacks receive the **Same Input** as the Primary.
This allows you to substitute models without changing the surrounding chain logic.

---

## 1. Syntax: The List

```python
chain_with_backup = primary_chain.with_fallbacks([backup_chain])
```

The argument is a **List** because you can have multiple fallbacks (ordered by priority).

---

## 2. Chain-Level vs Model-Level

You can add fallbacks at two granularities:

**Model-Level** (Recommended for Provider Outages):
```python
llm = gpt4.with_fallbacks([claude])
chain = prompt | llm | parser
```
If GPT-4 times out, Claude is used. The prompt and parser remain unchanged.

**Chain-Level** (Recommended for Logic Fallbacks):
```python
complex_chain = (retriever | prompt | llm | parser)
simple_chain = (simple_prompt | llm)

resilient_chain = complex_chain.with_fallbacks([simple_chain])
```
If the complex RAG chain fails (e.g., retriever returns 0 docs), fall back to a simpler "Ask the LLM directly" strategy.

---

## 3. The "Hardcoded" Fallback (Last Resort)

The final fallback should be **Instant** and **Cost-Free**.

```python
def hardcoded_response(x):
    return "I am temporarily unable to answer. Please try again later."

chain = (
    rag_chain
    .with_fallbacks([simple_llm_chain])
    .with_fallbacks([RunnableLambda(hardcoded_response)])
)
```

**Architecture**: This guarantees 100% Uptime. The user *always* gets a response. The quality degrades, but the service never 500s.

---

## Quick Reference

| Component | Scope | Best For |
| :--- | :--- | :--- |
| `llm.with_fallbacks(...)` | Provider | Rate limits, outages. |
| `chain.with_fallbacks(...)` | Logic | Multi-strategy reasoning. |
| `RunnableLambda(...)` | Hardcoded | Catastrophic failure. |
