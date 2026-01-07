| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC1.4.2.1 Basic LLMChain]]**                      | Create simple LLM chains                     | LLMChain class, constructor, minimal setup                                      | LLMChain combines a prompt and LLM into one callable.               |
| **[[LC1.4.2.2 Combining Prompt and LLM]]**            | Connect prompts to models                    | Prompt template + LLM, automatic formatting                                     | LLMChain auto-formats prompts and sends to the LLM.                 |
| **[[LC1.4.2.3 Input Output Handling]]**               | Manage chain data flow                       | Input variables, output keys, data dictionary                                   | LLMChain accepts dict inputs and returns dict outputs.              |
| **[[LC1.4.2.4 LLMChain Parameters]]**                 | Configure chain behavior                     | verbose, memory, callbacks, output_key                                          | Configure LLMChain with verbose, memory, and callbacks.             |
| **[[LC1.4.2.5 Simple Use Cases]]**                    | Apply LLMChain practically                   | Q&A, translation, summarization, single-step tasks                              | LLMChain suits single-step LLM tasks with templating.               |

# LLMChain: The Legacy Primitive

> [!WARNING]
> **Deprecation Notice**: As of LangChain 0.1, `LLMChain` is considered "Legacy." New code should use the `prompt | model` syntax (LCEL).
> This document explains `LLMChain` because you will see it in 90% of tutorials written before 2024.

---

## 1. The Class-Based Approach

In the early days, LangChain mirrored traditional Object-Oriented Programming (OOP) patterns.
To create a "Cognitive Step," you instantiated a class that bundled a Prompt and a Model.

```python
# THE OLD WAY (Do not use for new projects)
from langchain.chains import LLMChain
from langchain_openai import OpenAI

prompt = PromptTemplate.from_template("Tell me a joke about {topic}")
llm = OpenAI()

chain = LLMChain(prompt=prompt, llm=llm)
result = chain.run("bears")
# Output: "Why did the bear..."
```

**The Problem**:
This structure is opaque. You cannot easily see "inside" the chain. It hides the logic of variable formatting and output parsing behind a `.run()` method that behaves differently depending on the inputs.

---

## 2. Parameter Configurations

The `LLMChain` class had rigid configuration hooks that are now decoupled in LCEL.

### Output Keys
By default, `LLMChain` returns a dict `{'text': '...'}`.
If you wanted the key to be `joke` instead of `text`, you had to configure it at construction time.

```python
chain = LLMChain(
    prompt=prompt, 
    llm=llm, 
    output_key="joke",  # Renaming output
    verbose=True        # Print to console
)
```

**LCEL Equivalent**:
In modern LangChain, you just rename it in the dictionary using a `RunnableMap`.
`chain = prompt | model | {"joke": StrOutputParser()}`.

---

## 3. The "Chain of Chains" Pattern

The primary reason `LLMChain` existed was to serve as a building block for strictly typed higher-order chains like `SequentialChain`.
You would build `chain_one`, `chain_two`, and then pass them as objects into a manager.

```python
# Legacy Composition
chain_one = LLMChain(llm=llm, prompt=prompt_one)
chain_two = LLMChain(llm=llm, prompt=prompt_two)

overall_chain = SimpleSequentialChain(
    chains=[chain_one, chain_two],
    verbose=True
)
```

**Why this failed at scale**:
It forces a linear structure. Real-world AI apps are rarely linear; they curve, loop, and branch based on data values (Routing), which OOP classes handle poorly compared to functional graphs.

---

## 4. Migration Guide (Refactoring to LCEL)

If you inherit a codebase full of `LLMChain`, here is how you translate it to the "Professional Mental Model."

| Feature | Legacy `LLMChain` | Modern `LCEL` |
| :--- | :--- | :--- |
| **Creation** | `LLMChain(prompt=p, llm=m)` | `p | m` |
| **Execution** | `chain.run("input")` | `chain.invoke({"topic": "input"})` |
| **Output** | `{'text': 'Response'}` | `AIMessage(...)` |
| **Parsing** | (None / String only) | `p | m | StrOutputParser()` |

> **Architectural Benefit**: LCEL makes the *Data Shape* visible. You know `p | m` returns a Message. You know `p | m | parser` returns a String. `LLMChain` was a "Black Box" that returned... something.

---

## Quick Reference

| Term | Status | Definition |
| :--- | :--- | :--- |
| **LLMChain** | Legacy | The wrapper class for Prompt+LLM. |
| **chain.run()** | Legacy | The execution method. Convenience wrapper around invoke. |
| **chain.apply()**| Legacy | Batch processing method (replaced by `.batch()`). |
| **SimpleSequentialChain** | Legacy | A list of LLMChains. |
