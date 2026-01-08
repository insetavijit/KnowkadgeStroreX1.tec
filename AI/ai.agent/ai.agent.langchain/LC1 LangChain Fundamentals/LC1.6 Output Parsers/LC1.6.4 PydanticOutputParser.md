| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC1.6.4.1 Type-Safe Parsing with Pydantic]]**     | Get validated, typed outputs                 | PydanticOutputParser class, Pydantic models, type validation                    | PydanticOutputParser returns validated Pydantic objects.            |
| **[[LC1.6.4.2 Defining Output Schemas]]**             | Create Pydantic models for output            | BaseModel subclass, Field definitions, type annotations                         | Define Pydantic models to specify expected output structure.        |
| **[[LC1.6.4.3 Automatic Validation]]**                | Validate LLM output                          | Field validators, type coercion, constraint checking                            | Pydantic automatically validates parsed output.                     |
| **[[LC1.6.4.4 Format Instructions Generation]]**      | Auto-generate prompting hints                | get_format_instructions(), schema to prompt, automatic guidance                 | get_format_instructions() generates LLM prompting hints.            |
| **[[LC1.6.4.5 PydanticOutputParser in Practice]]**    | Apply in real chains                         | Integration patterns, chain setup, error handling                               | Add PydanticOutputParser to chains for typed outputs.               |

# PydanticOutputParser: The Strict Validator

If `JsonOutputParser` is a "Suggestion Box", `PydanticOutputParser` is a "Bouncer".
It enforces strict schema validation based on Python type hints.

---

## 1. The Schema-First Approach

In modern AI engineering, you **start** with the Pydantic model, not the Prompt.

```python
from langchain_core.pydantic_v1 import BaseModel, Field, validator

class UserProfile(BaseModel):
    name: str = Field(description="The full name of the user")
    age: int = Field(description="Age in years")
    interests: list[str] = Field(description="List of 3 hobbies")

    @validator("age")
    def check_age(cls, v):
        if v < 0:
            raise ValueError("Age cannot be negative!")
        return v
```

This class acts as the **SSOT (Single Source of Truth)** for both:
1.  **Prompt Instruction** (Description fields are sent to LLM).
2.  **Runtime Validation** (Logic runs after generation).

---

## 2. Wiring the Chain

The parser generates a massive block of text instructions which you must inject into the prompt.

```python
parser = PydanticOutputParser(pydantic_object=UserProfile)

prompt = PromptTemplate(
    # {format_instructions} is where the magic happens
    template="Create a profile for {persona}.\n{format_instructions}",
    input_variables=["persona"],
    partial_variables={"format_instructions": parser.get_format_instructions()}
)

chain = prompt | model | parser
```

**What the LLM sees**:
> Create a profile for a coder.
> The output should be formatted as a JSON instance that conforms to the JSON schema below.
> {"properties": {"name": ...}}

---

## 3. The "Legacy Trap"

**WARNING**: `PydanticOutputParser` relies on Prompt Engineering.
It asks the model to "Please output JSON".

For weak models (Llama-2-7b, Mistral-7b), this often fails.
For strong models (GPT-4), it works 99% of the time, but it uses up context tokens.

**Architectural Decision**:
*   Use `PydanticOutputParser` when using models that **DO NOT** support Function Calling / Tools.
*   Use `.with_structured_output(UserProfile)` (Next Chapter) for models that **DO** support Tools (OpenAI, Anthropic, Gemini).

---

## 4. Handling Validation Errors

If the model outputs valid JSON (e.g., `{"age": -5}`) but invalid logic, Pydantic raises a `ValidationError`.
This crashes the chain.

You can wrap this in a `OutputFixingParser`, which takes the error and the bad output, and sends it *back* to the LLM to fix.

```python
from langchain.output_parsers import OutputFixingParser

fixer = OutputFixingParser.from_llm(parser=parser, llm=model)
chain = prompt | model | fixer
```

---

## Quick Reference

| Component | Responsibility |
| :--- | :--- |
| **BaseModel** | Defines the Schema + Validation Logic. |
| **Field** | Defines the "Prompt" for each property. |
| **get.format...** | Generates the Prompt Injection text. |
| **invoke** | Validation + Type Coercion. |
