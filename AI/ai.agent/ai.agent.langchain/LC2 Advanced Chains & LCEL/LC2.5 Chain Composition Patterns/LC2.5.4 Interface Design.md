| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC2.5.4.1 Consistent I/O Contracts]]**            | Maintain uniformity                          | Standard formats, consistent types, predictable interfaces                      | Use consistent input/output formats across chains.                  |
| **[[LC2.5.4.2 Schema Definition]]**                   | Define formal schemas                        | Pydantic models, type definitions, validation                                   | Define formal schemas for chain inputs and outputs.                 |
| **[[LC2.5.4.3 Versioning]]**                          | Manage interface changes                     | Version numbers, migration, deprecation                                         | Version interfaces for backward compatibility.                      |
| **[[LC2.5.4.4 Backward Compatibility]]**              | Preserve existing behavior                   | Optional fields, defaults, evolution patterns                                   | Design interfaces for backward compatibility.                       |
| **[[LC2.5.4.5 API Design Principles]]**               | Apply good API design                        | Clarity, consistency, minimal surface, documentation                            | Apply API design principles to chain interfaces.                    |

# Interface Design: The Contract Layer

When you expose a chain as an API (e.g., via LangServe), its Input/Output schema becomes a **Public Contract**.

---

## 1. Pydantic Schemas (The Standard)

```python
from pydantic import BaseModel, Field

class ChainInput(BaseModel):
    question: str = Field(description="The user's query")
    context: str = Field(default="", description="Optional context")

class ChainOutput(BaseModel):
    answer: str = Field(description="The generated answer")
    sources: list[str] = Field(default_factory=list)
```

**Benefit**: LangServe automatically generates an OpenAPI spec from these models.

---

## 2. Versioning Your Interface

When you change the schema, bump the version.

```python
# v1
class ChainInputV1(BaseModel):
    query: str

# v2 (breaking change: renamed field)
class ChainInputV2(BaseModel):
    question: str  # Renamed
```

**Pattern**: Support both for a deprecation period.

---

## 3. Backward Compatibility (Additive Changes)

**Safe Change**: Adding a new *optional* field.
```python
class ChainInput(BaseModel):
    question: str
    metadata: dict = Field(default_factory=dict)  # New, optional
```

**Breaking Change**: Removing a field, or changing a type.

---

## Quick Reference

| Change Type | Breaking? | Recommendation |
| :--- | :--- | :--- |
| Add optional field | No | Safe. |
| Add required field | Yes | Provide default or new version. |
| Remove field | Yes | Deprecate first, then remove. |
| Change field type | Yes | New version. |
