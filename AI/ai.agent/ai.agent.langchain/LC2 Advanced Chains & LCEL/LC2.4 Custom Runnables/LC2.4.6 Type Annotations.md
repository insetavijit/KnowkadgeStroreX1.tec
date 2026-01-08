| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC2.4.6.1 InputType and OutputType]]**            | Define type parameters                       | Type aliases, generic parameters, type variables                                | Define InputType and OutputType for type safety.                    |
| **[[LC2.4.6.2 Generic Typing]]**                      | Use generic types                            | Generic[Input, Output], type variables, typing patterns                         | Use generics for flexible, typed runnables.                         |
| **[[LC2.4.6.3 Type Safety]]**                         | Ensure type correctness                      | Static checking, mypy, IDE support                                              | Type annotations enable static type checking.                       |
| **[[LC2.4.6.4 Type Inference]]**                      | Let types be inferred                        | Automatic inference, chaining types, composition types                          | Type inference works through LCEL chains.                           |
| **[[LC2.4.6.5 Pydantic Integration]]**                | Use Pydantic for types                       | BaseModel inputs/outputs, validation, schema generation                         | Use Pydantic models for complex typed I/O.                          |

# Type Annotations: Static Analysis for Chains

Python is dynamically typed, but modern Python (3.10+) uses type hints for IDE support and static analysis.
LCEL leverages Generics to make chains type-safe.

---

## 1. The `Runnable[Input, Output]` Generics

```python
class Runnable(Generic[Input, Output], ABC):
    def invoke(self, input: Input, ...) -> Output: ...
```

When you declare `class MyStep(Runnable[str, int])`, you're telling the type checker:
*   `.invoke()` takes a `str`.
*   `.invoke()` returns an `int`.

---

## 2. Chaining Types

When you compose: `A | B | C`
The LCEL machinery knows:
*   `A.OutputType` must be compatible with `B.InputType`.
*   `B.OutputType` must be compatible with `C.InputType`.

If you try to chain `Runnable[str, int]` to `Runnable[list, str]`, a type checker (`mypy`, Pyright) will flag it.

---

## 3. Pydantic Models for Complex Types

For complex structured data, use Pydantic `BaseModel`.

```python
from pydantic import BaseModel

class ChainInput(BaseModel):
    question: str
    user_id: str

class ChainOutput(BaseModel):
    answer: str
    confidence: float

class MyChain(Runnable[ChainInput, ChainOutput]):
    def invoke(self, input: ChainInput, config=None) -> ChainOutput:
        ...
```

**Benefit**: Automatic validation. If your chain receives `{"question": 123}`, Pydantic throws a clear `ValidationError` instead of a cryptic `TypeError` deep in your logic.

---

## Quick Reference

| Type System Feature | LangChain Support |
| :--- | :--- |
| **Generics** | `Runnable[I, O]` |
| **Pydantic** | First-class for I/O contracts. |
| **MyPy / Pyright** | Full compatibility. |
