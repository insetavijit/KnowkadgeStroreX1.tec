| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC1.4.5.1 Combining Chain Types]]**               | Mix different chain types                    | LLMChain + TransformChain, heterogeneous pipelines                              | Combine different chain types for varied functionality.             |
| **[[LC1.4.5.2 Nested Chains]]**                       | Chains within chains                         | Sub-chains, hierarchical composition, encapsulation                             | Nest chains for hierarchical, reusable structures.                  |
| **[[LC1.4.5.3 Modular Chain Design]]**                | Build reusable chain components              | Chain factories, parameterized chains, chain libraries                          | Design chains as modular, reusable components.                      |
| **[[LC1.4.5.4 Chains as Building Blocks]]**           | Think in terms of components                 | Lego-like composition, interface consistency, plug-and-play                     | Treat chains as interchangeable building blocks.                    |
| **[[LC1.4.5.5 Complex Workflow Patterns]]**           | Handle advanced scenarios                    | Parallel execution, conditional branching, error recovery                       | Complex workflows combine multiple composition patterns.            |

# Chain Composition: Advanced Wiring

You now know the primitives:
*   `|` (Sequence)
*   `RunnableLambda` (Function)

Now we cover the **Advanced Wiring**: Parallelism and Branching.
This is where LangChain moves from "Scripting" to "Distributed Systems Engineering."

---

## 1. Parallel Execution (`RunnableParallel`)

A common pattern is RAG with multiple retrievers, or generating "Pros" and "Cons" simultaneously.
`RunnableParallel` executes multiple runnables **concurrently** (in threads/asyncio) and merges their output into a dictionary.

```python
from langchain_core.runnables import RunnableParallel

model = ChatOpenAI()

# 1. Define the Fork
map_chain = RunnableParallel(
    joke=PromptTemplate.from_template("Tell a joke about {topic}") | model,
    poem=PromptTemplate.from_template("Write a poem about {topic}") | model
)

# 2. Invoke
# The two branches run at the same time!
result = map_chain.invoke({"topic": "bears"})

print(result)
# Output:
# {
#    "joke": AIMessage(content="Why did the bear..."),
#    "poem": AIMessage(content="Oh mighty bear...")
# }
```

**Architectural Use Case**:
Generating the `Summary`, `Sentiment`, and `Tags` for a document in a single pass before saving to a database.

---

## 2. Conditional Branching (`RunnableBranch`)

Logic is not always linear.
*   If input is "Math" -> Route to Math Chain.
*   If input is "Physics" -> Route to Physics Chain.

The `RunnableBranch` is the switch-statement of LCEL.

```python
from langchain_core.runnables import RunnableBranch

math_chain = PromptTemplate.from_template("Solve: {query}") | model
physics_chain = PromptTemplate.from_template("Explain physics: {query}") | model
general_chain = PromptTemplate.from_template("Answer: {query}") | model

# The Router
branch = RunnableBranch(
    (lambda x: "math" in x["query"].lower(), math_chain),
    (lambda x: "physics" in x["query"].lower(), physics_chain),
    general_chain # The "Default" (Interaction)
)

# Implementation
chain = branch | StrOutputParser()
```

> **Performance Note**: `RunnableBranch` runs the condition (lambda) first. If the condition requires an LLM call to decide (e.g. "Classify this intent"), that adds latency.

---

## 3. The "Micro-Chain" Pattern

In production, do not build one 500-line chain file.
Build tiny, testable chains and exporting them.

```python
# chains/summarization.py
summary_chain = (
    clean_text 
    | summary_prompt 
    | model 
    | StrOutputParser()
)

# chains/translation.py
translation_chain = (
    translation_prompt 
    | model 
    | StrOutputParser()
)

# app.py (Composition)
final_flow = (
    {"text": summary_chain}  # Run summary first
    | translation_chain      # Then translate the summary
)
```

**Why usage varies**:
In `final_flow`, the `translation_chain` receives the *output* of `summary_chain`.
Because `summary_chain` returns a string, `translation_chain` must accept a string (or you use `RunnablePassthrough` to wrap it).

---

## 4. Error Handling (Fallbacks)

What if the primary model fails (e.g., OpenAI 500 Error)?
`RunnableWithFallbacks` allows "Circuit Breaking."

```python
gpt4 = ChatOpenAI(model="gpt-4")
gpt3 = ChatOpenAI(model="gpt-3.5-turbo")

# If GPT-4 fails, automatically try GPT-3
robust_model = gpt4.with_fallbacks([gpt3])

chain = prompt | robust_model | parser
```

This logic happens entirely inside the chain execution graph. Your application code sees a success either way.

---

## Quick Reference

| Pattern | Class | Syntax |
| :--- | :--- | :--- |
| **Parallel** | `RunnableParallel` | `{"a": chain_a, "b": chain_b}` |
| **Branch** | `RunnableBranch` | `[(cond, chain), default]` |
| **Fallback** | `.with_fallbacks()`| `chain.with_fallbacks([backup])` |
| **Passthrough**| `RunnablePassthrough`| `x` (Identity function) |
