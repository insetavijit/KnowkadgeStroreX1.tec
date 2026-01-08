| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC2.1.4.1 Input Distribution]]**                  | Distribute input to branches                 | Same input to all, input broadcasting, parallel processing                      | Fan-out distributes the same input to all branches.                 |
| **[[LC2.1.4.2 Broadcasting Data]]**                   | Send data to multiple consumers              | Broadcast pattern, one-to-many, cloned inputs                                   | Broadcasting sends identical input to each parallel branch.         |
| **[[LC2.1.4.3 One-to-Many Patterns]]**                | Scale processing                             | Multiple processors, varied operations, parallel queries                        | One input triggers many parallel operations.                        |
| **[[LC2.1.4.4 Fan-Out Use Cases]]**                   | Apply in practice                            | Multi-retriever, multi-model, multi-format generation                           | Use fan-out for querying multiple sources simultaneously.           |
| **[[LC2.1.4.5 Selective Fan-Out]]**                   | Route to specific branches                   | Conditional distribution, partial broadcasting, filtered routing                | Selectively fan out based on input conditions.                      |

# Fan-Out Patterns: The Broadcasting Architecture

**Fan-Out** is the process of taking a single signal (Input) and feeding it to multiple independent workers.

---

## 1. The Expert Panel (Multi-Model Evaluation)

Imagine you want a "Diversity of Thought". You ask the same question to 3 different "Experts":
1.  **The Optimist** (High temperature, creative prompt).
2.  **The Doomer** (Safety focused, strict prompt).
3.  **The Fact Checker** (Wikipedia retriever).

```python
experts = RunnableParallel({
    "optimist": optimist_chain,
    "doomer": doomer_chain,
    "checker": fact_check_chain
})
```

**Architecture**:
This increases **Quality** at the cost of **Cost**.
You pay for 3x generation, but you minimize the risk of a single model having a blind spot.

---

## 2. The Hybrid Search (Multi-Retriever)

This is standard for Enterprise Search.
Users don't know if they want "Keywords" (BM25) or "Concepts" (Vectors).
**Solution**: Run both.

```python
hybrid_retriever = RunnableParallel({
    "keyword_docs": bm25_retriever,
    "semantic_docs": vector_retriever
})

# Input: "How to fix wifi?"
# Output: { "keyword_docs": [...], "semantic_docs": [...] }
```

You then merge them in the next step (Fan-In), often using Reciprocal Rank Fusion (RRF).

---

## 3. The "Side Effect" Fan-Out

Sometimes, a branch isn't for the user. It's for **You**.

```python
chain = RunnableParallel({
    "response": main_chain,        # The actual answer
    "analytics": log_to_postgres,  # Async side-effect (doesn't block)
    "safety": moderation_api       # Check for bad words
})
```

**Note**: In production, `log_to_postgres` should be a `RunnableLambda` wrapped in `asyncio.create_task` so it doesn't slow down the `response`.

---

## Quick Reference

| Use Case | Architecture | Benefit |
| :--- | :--- | :--- |
| **Mixture of Experts** | 1 Input -> N Models | Higher Quality / Robustness. |
| **Hybrid Search** | 1 Query -> N Retrievers | Higher Recall (Finding the right doc). |
| **Auditing** | 1 Input -> Response + Log | Observability without code clutter. |
