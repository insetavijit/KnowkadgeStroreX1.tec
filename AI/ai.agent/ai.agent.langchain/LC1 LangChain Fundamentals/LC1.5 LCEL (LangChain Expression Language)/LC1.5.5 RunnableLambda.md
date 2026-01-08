| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC1.5.5.1 Custom Functions in Chains]]**          | Add Python logic to LCEL                     | RunnableLambda class, function wrapping, inline logic                           | RunnableLambda wraps Python functions for LCEL use.                 |
| **[[LC1.5.5.2 Wrapping Python Functions]]**           | Convert functions to Runnables               | RunnableLambda(), @chain decorator, conversion patterns                         | Use RunnableLambda() or @chain to wrap functions.                   |
| **[[LC1.5.5.3 Lambda Expressions]]**                  | Use inline lambdas                           | Lambda syntax, simple transformations, quick operations                         | Use lambdas for simple inline transformations.                      |
| **[[LC1.5.5.4 Function Signatures]]**                 | Define proper function inputs/outputs        | Input types, return types, single input pattern                                 | Lambda functions take single input and return output.               |
| **[[LC1.5.5.5 Error Handling in Lambdas]]**           | Handle errors gracefully                     | Try/except, fallbacks, error propagation                                        | Handle errors within lambdas for robust chains.                     |

# RunnableLambda: The Bridge

The power of LangChain is not that it hides Python, but that it **wraps** Python.
`RunnableLambda` allows you to turn any Python function into a component of the graph.

---

## 1. Implicit Coercion

You rarely need to import `RunnableLambda`.
LangChain's `|` operator automatically converts any `callable` on its right side.

```python
def length_function(text: str) -> dict:
    return {"length": len(text)}

# Standard usage
chain = prompt | model | length_function
```

**Crucial Constraint**:
The function must accept **exactly one argument**.
If you need multi-argument logic, your single argument must be a dictionary.

---

## 2. The `@chain` Decorator

What if you want to compose a mini-chain and treat it as a function?
The `@chain` decorator converts a function that *returns* a Runnable into a Runnable itself.

```python
from langchain_core.runnables import chain

@chain
def custom_chain(text: str):
    # Dynamic Logic here
    if len(text) > 100:
        model_id = "gpt-4"
    else:
        model_id = "gpt-3.5-turbo"
        
    return ChatOpenAI(model=model_id).invoke(text)
```

**Architectural Benefit**:
This allows you to write "Imperative Logic" (if/else statements) that lives comfortably inside a "Declarative Graph."

---

## 3. Streaming Generators

If your python function returns an `Iterator`, it automatically supports `.stream()`.

```python
def stream_words(text: str):
    for word in text.split():
        yield word + " "
        time.sleep(0.1)

chain = RunnableLambda(stream_words)

for chunk in chain.stream("The quick brown fox"):
    print(chunk, flush=True)
```

This is how you build **Custom Parsers** that stream partial JSON results before the parenthesis is closed.

---

## 4. Metadata and Tracing

When you view a trace in LangSmith, pure lambdas often show up as `RunnableLambda` (Generic).
For proper observability, assign names manually.

```python
func = RunnableLambda(my_func).with_config(run_name="MySpecialLogic")
```

Or just name your python functions descriptively (`def clean_text:`), and LangChain will auto-extract the name.

---

## Quick Reference

| Usage | Syntax | Note |
| :--- | :--- | :--- |
| **Simple** | `chain \| func` | Implicit conversion. |
| **Explicit** | `RunnableLambda(func)` | For added config/names. |
| **Decorator** | `@chain` | Turning imperative code into graph nodes. |
