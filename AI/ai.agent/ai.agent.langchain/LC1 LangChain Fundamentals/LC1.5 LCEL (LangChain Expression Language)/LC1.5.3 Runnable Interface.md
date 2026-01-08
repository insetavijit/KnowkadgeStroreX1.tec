| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC1.5.3.1 Runnable Protocol]]**                   | Understand the Runnable contract             | Runnable interface, required methods, type consistency                          | All LCEL components implement the Runnable protocol.                |
| **[[LC1.5.3.2 Invoke Batch Stream Methods]]**         | Use core Runnable methods                    | invoke(), batch(), stream(), method signatures                                  | Runnables support invoke, batch, and stream methods.                |
| **[[LC1.5.3.3 Input Output Types]]**                  | Define Runnable typing                       | Input type, Output type, type hints, generic typing                             | Runnables have defined Input and Output types.                      |
| **[[LC1.5.3.4 Runnable Contract]]**                   | Follow interface requirements                | Method requirements, async variants, configurable options                       | Runnables must implement specific interface methods.                |
| **[[LC1.5.3.5 Understanding Runnables]]**             | Grasp the abstraction                        | Everything is a Runnable, uniform interface, composition basis                  | Runnables are the fundamental LCEL building block.                  |

# Runnable Interface: The Polymorpic Core

In Object-Oriented Design, **Polymorphism** allows you to treat different objects (Circle, Square) as the same thing (Shape).
In LangChain, **Runnables** allow you to treat `Prompt`, `Model`, `Retriever`, and `Chain` as the same thing: **A Function**.

Because they all share the exact same methods, they are infinitely composable.

---

## 1. The Standard Contract

Every object in LCEL implements these core methods.

### 1.1 The Synchronous Layer
*   `.invoke(input) -> output`: The standard call.
*   `.batch([inputs]) -> [outputs]`: Parallel execution using a ThreadPoolExecutor.
*   `.stream(input) -> Iterator[output]`: Tokens or Chunks.

### 1.2 The Asynchronous Layer
*   `.ainvoke(input) -> output`: Native `await` support.
*   `.abatch([inputs]) -> [outputs]`: Native `asyncio.gather`.
*   `.astream(input) -> AsyncIterator[output]`: For websockets/SSE.

> **Architectural Note**: This is why LCEL is superior to custom Python functions. If you write a standard function `def my_chain(x):`, you have to manually implement `batch` processing and `async` support. With LCEL, you get them for free.

---

## 2. Introspection (Validation)

Runnables are not just executable; they are **Self-Describing**.
They carry Pydantic schemas that describe what they expect and what they return.

```python
chain = prompt | model

# What input does this chain need?
print(chain.input_schema.schema_json())
# Output: {"properties": {"topic": {"type": "string"}}}

# What does it return?
print(chain.output_schema.schema_json())
# Output: {"properties": {"content": {"type": "string"}}}
```

**Use Case**:
LangServe uses these schemas to automatically generate Swagger/OpenAPI documentation for your API endpoints.

---

## 3. Configuration Injection (`.bind`)

Sometimes you need to pass "Meta-Parameters" that are not part of the data flow.
*   `stop`: Stop sequences for the LLM.
*   `functions`: OpenAI tools.
*   `configurable`: Runtime flags.

You use `.bind()` to attach these static arguments to a Runnable *before* execution.

```python
# The base model
model = ChatOpenAI()

# The specialized model (bound)
# Note: Input data flow does NOT need to contain 'stop'
model_with_stop = model.bind(stop=["\nEND"])

chain = prompt | model_with_stop
```

This is effectively **Currying** (Partial Application) at the object level.

---

## Quick Reference

| Method | Behavior | Use Case |
| :--- | :--- | :--- |
| **invoke** | One-in, One-out | CLI scripts, simple tests. |
| **batch** | Many-in, Many-out | Processing a CSV file. |
| **stream** | One-in, Many-out | Chat UI (Typewriter effect). |
| **bind** | Static Argument Binding | Setting LLM `temperature` or `max_tokens`. |
