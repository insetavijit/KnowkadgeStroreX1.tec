| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC2.5.3.1 Extracting Common Chains]]**            | Identify reusable patterns                   | Common operations, shared logic, extraction patterns                            | Extract common chain patterns for reuse.                            |
| **[[LC2.5.3.2 Parameterized Chains]]**                | Make chains configurable                     | Parameters, factory pattern, flexible chains                                    | Parameterize chains for varied use cases.                           |
| **[[LC2.5.3.3 Chain Factories]]**                     | Create chains programmatically               | Factory functions, chain builders, dynamic creation                             | Use factories to create configured chain instances.                 |
| **[[LC2.5.3.4 Composition Strategies]]**              | Choose composition approach                  | Inheritance vs composition, mixin patterns, composition first                   | Prefer composition over inheritance for chains.                     |
| **[[LC2.5.3.5 DRY Principles]]**                      | Avoid repetition                             | Code reuse, template chains, shared components                                  | Apply DRY principles across chain definitions.                      |

# Chain Reuse Patterns: The Factory Approach

Don't copy-paste chains. Use **Factories**.

---

## 1. The Problem of Repetition

You might have 5 similar chains that just differ in the model or prompt:

```python
# Bad: Copy-Paste
chain_a = prompt_a | llm_a | parser_a
chain_b = prompt_b | llm_a | parser_a  # Same LLM and Parser!
chain_c = prompt_c | llm_a | parser_a
```

If you need to change `parser_a`, you change it in 3 places. This is a maintenance nightmare.

---

## 2. The Factory Solution

```python
def create_chain(prompt_template: str, llm: Runnable) -> Runnable:
    prompt = PromptTemplate.from_template(prompt_template)
    parser = JsonOutputParser()  # Shared logic
    return prompt | llm | parser

# Usage
chain_a = create_chain("Summarize: {text}", gpt4)
chain_b = create_chain("Translate: {text}", gpt4)
chain_c = create_chain("Analyze: {text}", claude)
```

**Benefit**: The parser logic is defined once. Change it once, it updates everywhere.

---

## 3. Advanced: Dependency Injection

If you're using FastAPI, you can inject the `llm` at request time.

```python
# chains.py
def create_chain(llm: Runnable):
    return prompt | llm | parser

# api.py
@app.post("/generate")
async def generate(request: Request, settings: Settings = Depends(get_settings)):
    llm = get_llm(settings.model_provider)
    chain = create_chain(llm)
    return await chain.ainvoke(request.input)
```

**Benefit**: The chain definition is decoupled from the provider choice.

---

## Quick Reference

| Pattern | Use Case |
| :--- | :--- |
| **Static Chain** | Fixed logic, no variation. |
| **Factory Function** | Same structure, varied params. |
| **Dependency Injection** | Runtime model selection. |
