| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC1.3.6.1 Partial Prompt Templates]]**            | Pre-fill some variables                      | partial() method, fixed values, template specialization                         | Use partial() to pre-fill known variable values.                    |
| **[[LC1.3.6.2 Deferred Variable Binding]]**           | Delay variable resolution                    | Callable partials, lambda functions, runtime resolution                         | Pass functions to defer variable resolution until runtime.          |
| **[[LC1.3.6.3 Runtime vs Compile-Time Variables]]**   | Distinguish variable timing                  | Static values, dynamic values, binding strategies                               | Compile-time vars are fixed; runtime vars change per call.          |
| **[[LC1.3.6.4 Partial Formatting Strategies]]**       | Apply partials effectively                   | Progressive filling, factory patterns, partial chains                           | Use partials to build specialized prompts from general ones.        |
| **[[LC1.3.6.5 Use Cases for Partials]]**              | Apply partials in practice                   | Date/time injection, user context, environment-specific values                  | Partials excel for context like current date or user info.          |

# Partial Variables: Architecture of Dependency Injection

In Functional Programming, this is called **Currying**.
In Prompt Engineering, we call it **Partial Application**.

It addresses a specific architectural pain point:
**"I have variables that differ in lifecycle."**

*   `user_id`: Known at login session start.
*   `date`: Known at the moment of execution.
*   `query`: Known only when the user types.

You do not want to pass `date` and `user_id` into every single `.invoke()` call throughout your codebase.

---

## 1. Static Binding (The "Session" Pattern)

You have a generic prompt. You want to create a specialized instance for the current user.

```python
from langchain_core.prompts import PromptTemplate

# 1. The Generic Template (Requires 2 vars)
template = PromptTemplate.from_template(
    "User: {name}\nTask: {task}"
)

# 2. detailed_prompt requires just 'task'
my_prompt = template.partial(name="Alice")

# 3. Usage
print(my_prompt.invoke({"task": "Buy milk"}))
# Output: "User: Alice\nTask: Buy milk"
```

**Use Case**:
In a FastAPI dependency, you might create a `user_prompt` object immediately after authentication and inject *that* object into your business logic functions, which don't need to know the `name` anymore.

---

## 2. Dynamic Binding (Factory Functions)

Some variables change every time you run the prompt, but you don't want to pass them manually.
**Classic Example**: The Current Date.

If you hardcode `date="2024-01-01"`, your prompt becomes stale.
If you pass `date=datetime.now()` in every call, you boilerplate your code.

**The Solution**: Bind a **Function**, not a Value.

```python
from datetime import datetime

def get_current_date():
    return datetime.now().strftime("%Y-%m-%d")

# The prompt will call 'get_current_date' AUTOMATICALLY when invoked
template = PromptTemplate(
    template="Today is {date}. {query}",
    input_variables=["query"],
    partial_variables={"date": get_current_date} # Pass function reference
)

# Usage (No date passed!)
template.invoke({"query": "What day is it?"})
```

---

## 3. Architectural Layers

Using Partials allows you to build a **Layered Prompt Architecture**.

1.  **Layer 0 (Global)**: Safety & Date. (Partialed at App Startup)
2.  **Layer 1 (Session)**: User Name, Subscription Level. (Partialed at Request Start)
3.  **Layer 2 (Interaction)**: User Query. (Passed at Invocation)

```python
# Layer 0
base_prompt = PromptTemplate.from_template(
    "{safety}\nDate: {date}\nUser: {user}\nQ: {q}",
    partial_variables={"date": get_date, "safety": "Be Safe."}
)

# Layer 1
session_prompt = base_prompt.partial(user="Bob")

# Layer 2
session_prompt.invoke({"q": "Hi"})
```

---

## Quick Reference

| Binding Type | Syntax | Lifecycle |
| :--- | :--- | :--- |
| **Static** | `partial(foo="bar")` | Fixed for the lifetime of the object. |
| **Dynamic** | `partial_variables={"foo": func}` | Re-evaluated on every `.invoke()`. |
| **Missing** | ERROR | If you forget a variable and don't partial it, LangChain raises `ValidationError`. |
