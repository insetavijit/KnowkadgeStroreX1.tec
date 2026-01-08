| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC1.6.5.1 Defining Output Structures]]**          | Design structured schemas                    | Schema design, field selection, structure planning                              | Design output structures that match your data needs.                |
| **[[LC1.6.5.2 Nested Objects]]**                      | Handle hierarchical data                     | Nested Pydantic models, object composition, depth handling                      | Use nested Pydantic models for hierarchical structures.             |
| **[[LC1.6.5.3 Lists and Arrays]]**                    | Parse collection outputs                     | List[Type] annotations, array parsing, item validation                          | Use List[Type] for array outputs in schemas.                        |
| **[[LC1.6.5.4 Complex Schemas]]**                     | Handle advanced structures                   | Union types, Optional fields, complex type hints                                | Complex schemas support unions, optionals, and more.                |
| **[[LC1.6.5.5 Structured Output Best Practices]]**    | Apply effective patterns                     | Schema simplicity, clear naming, validation rules                               | Keep schemas simple and clearly named for best results.             |

# Structured Output: The Modern Standard

Forget `JsonOutputParser`. Forget `PydanticOutputParser`.
If you are using a modern model (OpenAI, Anthropic, Gemini, Mistral), there is only one correct way to get data out: **`.with_structured_output()`**.

This method uses the model's native **Function Calling / Tool Use** API to force structured generation at the tokenizer level, bypassing the fragility of prompt engineering.

---

## 1. The Syntax

It is elegantly simple. You define your schema (Pydantic) and bind it to the model.

```python
from langchain_openai import ChatOpenAI
from langchain_core.pydantic_v1 import BaseModel, Field

class Receipt(BaseModel):
    store_name: str = Field(description="Name of the merchant")
    items: list[str] = Field(description="List of purchased items")
    total: float = Field(description="Total amount spent")

llm = ChatOpenAI(model="gpt-4-turbo")

# The Magic Method
structured_llm = llm.with_structured_output(Receipt)

# Usage
receipt = structured_llm.invoke("I bought 3 apples at Walmart for $5.00")
# Output: Receipt(store_name='Walmart', items=['3 apples'], total=5.0)
```

**Architectural Change**:
Notice there is **NO PARSER** in the chain.
The LLM itself *returns* the Pydantic object. The parsing happens effectively "inside" the model invocation.

---

## 2. Under the Hood (Tool Mode vs JSON Mode)

`.with_structured_output(schema, method="...")` supports two backends:

1.  **`method="function_calling"` (Default)**:
    It binds your schema as a Tool and forces the model to call it. This is extremely robust because models are fine-tuned to call tools.

2.  **`method="json_mode"`**:
    It sets `response_format={"type": "json_object"}` (OpenAI API). This is useful if the schema is too complex for tool calling, but it requires you to parse the JSON manually (or LangChain handles it lightly).

**Recommendation**: Always stick to the default (Tool/Function calling) unless you hit specific limits.

---

## 3. Handling Complex Nested Schemas

Because this relies on Pydantic, you can build arbitrarily deep structures.

```python
class Address(BaseModel):
    street: str
    city: str

class User(BaseModel):
    name: str
    addresses: list[Address] # Nested List of Objects

structured_llm = llm.with_structured_output(User)
```

**Warning**: Deeply nested structures increase latency and token usage.
If you have a massive schema, consider breaking it into multiple smaller chains (The "Micro-Chains" pattern).

---

## 4. Multi-Schema Selection

What if the output could be a `Receipt` OR a `Invoice`?
You can pass a `Union` or a list of schemas.

```python
from typing import Union

structured_llm = llm.with_structured_output(Union[Receipt, Invoice])
```

The model will decide which schema to populate based on the semantic content of the user input.

---

## Quick Reference

| Feature | Details |
| :--- | :--- |
| **Reliability** | ⭐⭐⭐⭐⭐ (Highest) |
| **Complexity** | ⭐ (Lowest - 1 line of code) |
| **Supported Models** | OpenAI, Anthropic, Gemini, Mistral, VertexAI. |
| **Fallback** | If model unsupported, use `PydanticOutputParser`. |
