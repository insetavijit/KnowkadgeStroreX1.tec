| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC1.4.3.1 SimpleSequentialChain]]**               | Chain with single I/O                        | SimpleSequentialChain class, single input/output, linear flow                   | SimpleSequentialChain passes single output to next input.           |
| **[[LC1.4.3.2 SequentialChain]]**                     | Chain with multiple I/O                      | SequentialChain class, multiple keys, flexible mapping                          | SequentialChain handles multiple named inputs and outputs.          |
| **[[LC1.4.3.3 Chaining Multiple Steps]]**             | Connect multiple chain links                 | Multi-step workflows, adding chains, order matters                              | Chain multiple steps by adding them to sequential chain.            |
| **[[LC1.4.3.4 Output to Input Mapping]]**             | Map data between steps                       | Key matching, renaming, data transformation between chains                      | Match output keys of one chain to input keys of the next.           |
| **[[LC1.4.3.5 Linear Workflows]]**                    | Build straight-line pipelines                | Step-by-step execution, predictable flow, debugging linear chains               | Linear workflows execute chains in defined order.                   |

# Sequential Chains: The Pipeline Pattern

> [!TIP]
> **Modern Equivalent**: This file describes the Legacy class `SequentialChain`. In modern LangChain, this is simply the pipe operator `|` (RunnableSequence).

The core operation of any AI application is **Composition**: taking the output of one step and feeding it as input to the next.

---

## 1. The Single-Input Pipeline (`SimpleSequentialChain`)

In 90% of cases, your chain is linear A -> B -> C.
1.  **Synopsis Chain**: Writes a plot summary.
2.  **Review Chain**: Writes a review of that summary.

**Legacy Class Implementation**:
```python
# The Old Way
synopsis_chain = LLMChain(llm=llm, prompt=synopsis_template)
review_chain = LLMChain(llm=llm, prompt=review_template)

overall_chain = SimpleSequentialChain(
    chains=[synopsis_chain, review_chain],
    verbose=True
)
```

**Modern LCEL Implementation**:
```python
# The "Professional" Way
chain = (
    synopsis_template 
    | llm 
    | StrOutputParser() # Output of A
    | review_template   # Input of B
    | llm
)
```

**Architectural Insight**:
The legacy class was "Magic." It assumed the *only* output of chain A should be fed to the *only* input variable of chain B.
LCEL makes this explicit. You can see the string flow.

---

## 2. The Multi-Input Pipeline (`SequentialChain`)

Real applications have multiple variables.
*   Chain A outputs: `summary`, `sentiment`.
*   Chain B needs: `summary`, `user_language`.

The legacy `SequentialChain` required manual wiring of `output_variables` and `input_variables`.

```python
# The "Boilerplate" Way
chain = SequentialChain(
    chains=[chain_a, chain_b],
    input_variables=["doc_text", "language"],
    output_variables=["summary", "translation"]
)
```

**The LCEL Data Bus Pattern**:
In modern LangChain, we handle this using `RunnablePassthrough` to keep the data dictionary alive.

```python
from langchain_core.runnables import RunnablePassthrough

# Map inputs -> Process -> Add to Dictionary
chain = (
    RunnablePassthrough.assign(
        summary = (
            summary_prompt 
            | llm 
            | StrOutputParser()
        )
    )
    | translation_prompt # Consumes 'summary' and 'language'
    | llm
)
```

> **Mental Model**: In LCEL, the data flows as a Dictionary. `.assign()` operates like adding a column to a Pandas DataFrame or a key to a Dict. It calculates a new value and appends it to the stream.

---

## 3. Why the Shift? (The "Box" vs The "Stream")

Why did LangChain rewrite its entire core from `SequentialChain` to `|`?

1.  **Streaming**: `SequentialChain` computed step 1 fully, then step 2. You waited 20 seconds.
    LCEL streams token-by-token from Step 1 -> Step 2 -> User. You wait 200ms.
2.  **Debugging**: In the legacy class, an error inside Step 3 was hard to pinpoint. In LCEL, stack traces point exactly to the Runnable line.
3.  **Typing**: LCEL provides static analysis support.

---

## Quick Reference

| Feature | Legacy Class | Modern Syntax |
| :--- | :--- | :--- |
| **Linear** | `SimpleSequentialChain` | `A | B | C` |
| **Complex** | `SequentialChain` | `RunnablePassthrough.assign(...)` |
| **Branching** | `RouterChain` | `RunnableBranch` |
| **Parallel** | (No native support) | `RunnableParallel` |
