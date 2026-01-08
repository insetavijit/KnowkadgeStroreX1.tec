| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC2.2.5.1 Selecting Chains at Runtime]]**         | Choose chains dynamically                    | Runtime evaluation, input-driven selection, flexible architectures              | Select chains dynamically based on input at runtime.                |
| **[[LC2.2.5.2 Input-Driven Routing]]**                | Route based on input                         | Content-based routing, field-based selection, type routing                      | Route to different chains based on input content.                   |
| **[[LC2.2.5.3 Dynamic Workflow Paths]]**              | Create flexible flows                        | Variable paths, adaptive processing, context-aware routing                      | Create workflows that adapt to input characteristics.               |
| **[[LC2.2.5.4 Flexible Architectures]]**              | Build adaptable systems                      | Extensible routing, plug-in chains, modular handlers                            | Design architectures that easily add new routes.                    |
| **[[LC2.2.5.5 Metadata-Based Routing]]**              | Route on metadata                            | User info, context, session data, configuration routing                         | Route based on metadata like user role or context.                  |

# Dynamic Chain Selection: Configurable Logic

Often, you don't even know *which* chains exist until runtime.
Example: You load 5 plugins from a database. You can't hardcode `if plugin_1: ...` because the code doesn't know about `plugin_1` at deploy time.

---

## 1. The Configurable Runnable

LCEL has a built-in primitive for this: `RunnableLambda` returning a Runnable.

```python
def route_by_config(info):
    # This logic can check a database, a config file, or user settings
    model_name = info["config"]["configurable"]["model"]
    if model_name == "gpt-4":
        return gpt4_chain
    elif model_name == "local":
        return local_llama_chain
    return default_chain

# The "Router" is just a function that returns a Chain
dynamic_router = RunnableLambda(route_by_config)
```

**Architecture**: The Factory Pattern.
The `route_by_config` function is a **Chain Factory**. It runs once per request to decide *what* graph to build.

---

## 2. `.with_config()` Injection

This allows you to change the behavior of the chain *per request* without changing the code.

```python
# The User Request
chain.invoke(
    "Hello", 
    config={"configurable": {"model": "local"}}
)
```

This is how **LangServe** works. It exposes these configuration parameters as API fields, allowing the frontend to toggle "Search On/Off" or "Model A/B".

---

## 3. Metadata Routing (Multi-Tenant)

If you are building a SaaS, User A might have access to "Finance Module" while User B does not.

```python
def auth_router(input, config):
    user_permissions = config["metadata"]["permissions"]
    if "finance" in user_permissions:
        return finance_chain
    return standard_chain
```

This ensures isolation at the **Logic Level**, deeper than just API auth.

---

## Quick Reference

| Method | Dynamism | Use Case |
| :--- | :--- | :--- |
| `RunnableBranch` | Low (Hardcoded) | Fixed logic (Math vs Code). |
| `RunnableLambda` | High (Code) | Database-driven plugins. |
| `with_config` | High (Injection) | User settings / Feature Flags. |
