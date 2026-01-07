| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC1.3.5.1 Combining Prompts]]**                   | Merge multiple prompt pieces                 | Prompt concatenation, + operator, sequential combination                        | Combine prompts using + operator or composition methods.            |
| **[[LC1.3.5.2 PipelinePromptTemplate]]**              | Build multi-part templates                   | PipelinePromptTemplate class, pipeline_prompts, final_prompt                    | PipelinePromptTemplate chains multiple prompts together.            |
| **[[LC1.3.5.3 Modular Prompt Design]]**               | Create reusable prompt modules               | Component prompts, shared components, maintainability                           | Design prompts as reusable, composable modules.                     |
| **[[LC1.3.5.4 Reusable Prompt Components]]**          | Build a prompt library                       | Common instructions, shared context, template libraries                         | Create reusable prompt components for consistency.                  |
| **[[LC1.3.5.5 Template Inheritance]]**                | Extend base templates                        | Base templates, specialized variants, override patterns                         | Inherit from base prompts to create specialized variants.           |

# Prompt Composition: The Micro-Components Approach

In large applications, copying the same "System Instruction" into 50 different prompt files is a violation of the **DRY (Don't Repeat Yourself)** principle. If you need to update your Safety Policy, you shouldn't have to edit 50 files.

LangChain treats prompts as **Composable Modules**.

---

## 1. String Composition (The `+` Operator)

Code can be added together. So can prompts.

```python
from langchain_core.prompts import PromptTemplate

# 1. Define Atomic Units
header = PromptTemplate.from_template("ROLE: {role}")
body = PromptTemplate.from_template("TASK: {task}")
footer = PromptTemplate.from_template("OUTPUT: JSON")

# 2. Compose
full_prompt = header + "\n" + body + "\n" + footer

# 3. Usage
# Result input_variables=['role', 'task'] 
# (Footer has no vars, so it's just appended)
```

This works for `ChatPromptTemplate` as well.
`full_chat = system_prompt + inputs + history + user_msg`.

---

## 2. The PipelinePromptTemplate (Micro-Frontends for AI)

Sometimes you want to inject a "Prompt inside a Prompt."
This is useful when you have a **Master Template** (The "Skeleton") and many **Sub-Templates** (The "Organs").

**Use Case**: A standard "Chain of Thought" harness where only the core question changes.

```python
from langchain_core.prompts import PipelinePromptTemplate

# 1. The Skeleton
full_template = PromptTemplate.from_template(
    """
    {system_level_instructions}
    
    context: {specific_context}
    
    Question: {input}
    """
)

# 2. The Organs
system_prompt = PromptTemplate.from_template("You are a helpful bot.")
context_prompt = PromptTemplate.from_template("Today is Monday.")

# 3. The Wiring
pipeline_prompt = PipelinePromptTemplate(
    final_prompt=full_template,
    pipeline_prompts=[
        ("system_level_instructions", system_prompt),
        ("specific_context", context_prompt),
    ],
)
```

**Why do this?**
It decouples the **Structure** (The Skeleton) from the **Content** (The Organs). You can swap the system instructions globally without touching the specific context logic.

---

## 3. Modular Design Strategy

In a production repo, organize prompts by **Scope**, not just by feature.

```
prompts/
├── core/
│   ├── safety_header.yaml       # "Do not be racist..."
│   ├── json_formatter.yaml      # "Ensure valid JSON..."
│   └── personality.yaml         # "Be cheerful..."
├── features/
│   ├── email_writer.yaml        # Imports core/personality
│   └── sql_generator.yaml       # Imports core/json_formatter
```

You load the `core` prompts at runtime and partial them into the `feature` prompts.

```python
# app/prompts.py
safety = load_prompt("core/safety_header.yaml")

def get_email_prompt():
    base = load_prompt("features/email_writer.yaml")
    return safety + base  # Composition!
```

---

## Quick Reference

| Method | Analogy | Use Case |
| :--- | :--- | :--- |
| **`+` Operator** | Concatenation | Stacking System + Tool + User instructions. |
| **PipelinePrompt** | Dependency Injection | Injecting a specific Persona into a generic Conversation loop. |
| **Partial** | Currying | Fixing the "Date" or "User Name" once at the start of a session. |
