| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC2.1.3.1 Parallel Output Structure]]**           | Understand output format                     | Dict output, key-value pairs, branch results                                    | Parallel chains return a dict with branch names as keys.            |
| **[[LC2.1.3.2 Accessing Branch Results]]**            | Retrieve specific outputs                    | Dict access, key lookup, result handling                                        | Access results using branch name as dictionary key.                 |
| **[[LC2.1.3.3 Merging Strategies]]**                  | Combine parallel outputs                     | Post-processing, aggregation, transformation                                    | Apply post-processing to merge parallel outputs.                    |
| **[[LC2.1.3.4 Result Transformation]]**               | Transform merged results                     | RunnableLambda, custom processing, format conversion                            | Use RunnableLambda to transform parallel outputs.                   |
| **[[LC2.1.3.5 Flattening Results]]**                  | Simplify nested outputs                      | Flatten patterns, extract values, reduce nesting                                | Flatten complex parallel outputs for simpler downstream use.        |

# Result Merging: Aggregation Patterns

`RunnableParallel` is a "Fork" operation. Only forks are useless without a "Join".
Generally, there are two ways to Join: **Syntactic Join** (Prompting) and **Semantic Join** (Code).

---

## 1. The Syntactic Join (Prompt Assembly)

This is the standard pattern for RAG.
You don't manually merge the strings. You pass the dictionary state to a Prompt, which "Templates" the merge.

```python
# The Fork
inputs = RunnableParallel({
    "context": retriever,
    "question": RunnablePassthrough()
})

# The Join template
template = """
Answer the question based on the context:
Context: {context}
Question: {question}
"""

# The Merge happens HERE implicitly
chain = inputs | PromptTemplate.from_template(template) | model
```

**Architecture**: The Prompt acts as the **Aggregator**. It takes the parallel outputs and serializes them into a single string for the LLM.

---

## 2. The Semantic Join (Custom Logic)

Sometimes you want to calculate something, not just format text.
Use `RunnableLambda` to merge.

```python
def average_scores(inputs: dict) -> float:
    return (inputs["judge1_score"] + inputs["judge2_score"]) / 2

parallel_judges = RunnableParallel({
    "judge1_score": chain_a, # Returns float
    "judge2_score": chain_b  # Returns float
})

# The Join Code
final_chain = parallel_judges | RunnableLambda(average_scores)
```

**Architecture**: Map-Reduce.
`RunnableParallel` maps the input to 2 workers.
`RunnableLambda` reduces the 2 outputs to 1 value.

---

## 3. The Flattening Problem

Nested Parallels can create messy state: `{"a": {"b": 1}}`.
Use `.assign()` (covered in LC1.5.4) to merge results into the *existing* workflow instead of creating a new nested dict.

```python
# This keeps the original input keys AND adds the new keys
chain = RunnablePassthrough.assign(
    embedding=embed_docs,
    summary=summarize_docs
)
```

**Output**: `{"original_input": "...", "embedding": [...], "summary": "..."}`.

---

## Quick Reference

| Pattern | Component | Output Type |
| :--- | :--- | :--- |
| **Templating** | `PromptTemplate` | `PromptValue` (String-like) |
| **Reducing** | `RunnableLambda` | Any (Float, Listing, Obj) |
| **Augmenting** | `.assign()` | `Dict` (Combines Input + Output) |
