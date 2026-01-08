| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC2.1.5.1 Collecting Parallel Results]]**         | Gather branch outputs                        | Result collection, waiting for all, synchronization                             | Fan-in collects all parallel results before continuing.             |
| **[[LC2.1.5.2 Aggregation Strategies]]**              | Combine collected results                    | Concatenation, merging, summarization, voting                                   | Aggregate parallel results using appropriate strategy.              |
| **[[LC2.1.5.3 Many-to-One Patterns]]**                | Reduce multiple to single                    | Result reduction, final output, consolidation                                   | Many-to-one reduces parallel outputs to single result.              |
| **[[LC2.1.5.4 Result Consolidation]]**                | Create unified output                        | Combining documents, merging responses, unified format                          | Consolidate parallel outputs into cohesive final output.            |
| **[[LC2.1.5.5 Post-Parallel Processing]]**            | Process after collection                     | Final LLM call, synthesis, format output                                        | Apply final processing after collecting parallel results.           |

# Fan-In Patterns: The Synthesis Architecture

Fan-Out is easy (Just let them run).
Fan-In is hard. You have conflicting opinions, different formats, and noise.
The **Fan-In** component (or Reducer) is responsible for resolving this entropy.

---

## 1. The Concatenator (Simplest)

Use this when you just want to "Show your work".
You gathered 3 jokes. You want to show all 3.

```python
template = """
Here are 3 jokes I found:
1. {joke_a}
2. {joke_b}
3. {joke_c}
"""

fan_in_chain = parallel_jokes | PromptTemplate.from_template(template)
```

---

## 2. The Synthesizer (Map-Reduce)

Use this when the user wants **One Answer**, but you consulted 5 sources.

**Architecture**:
1.  **Map**: Ask 3 Models "Is this code safe?"
    *   Model A: "Yes"
    *   Model B: "No, SQL Injection risk"
    *   Model C: "Maybe"
2.  **Reduce**: Ask a "Judge" Model to review the arguments.

```python
# The Input to the Judge is the Dictionary of opinions
judge_prompt = """
Review the following opinions:
Opinion A: {opinion_a}
Opinion B: {opinion_b}
Opinion C: {opinion_c}

Synthesize a final verdict. If there is any disagreement, err on the side of caution.
"""

chain = experts | judge_prompt | judge_model
```

**Why this is powerful**:
The Judge Model can be smaller/cheaper because it has "Pre-digested" context.

---

## 3. The Voter (Programmatic)

Use this when you want strict logic, not LLM vibes.

```python
def vote(inputs: dict) -> str:
    votes = [inputs["a"], inputs["b"], inputs["c"]]
    if votes.count("YES") > 1:
        return "APPROVED"
    return "REJECTED"

chain = experts | RunnableLambda(vote)
```

This is crucial for **Guardrails**.
If "Safety Filter" says BLOCK, it doesn't matter what "Helpful Bot" says. The voter overrides it.

---

## Quick Reference

| Pattern | Logic | Use Case |
| :--- | :--- | :--- |
| **Concatenate** | `String.join` | Lists, Research Reports. |
| **Synthesize** | `LLM(Context)` | Complex Reasoning, Conflict Resolution. |
| **Vote** | `Python Code` | Safety Checks, Classification. |
