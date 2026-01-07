| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC1.3.2.1 Building Chat Prompts]]**               | Construct chat-based templates               | ChatPromptTemplate class, from_messages() method, message lists                 | Use ChatPromptTemplate.from_messages() for chat prompts.            |
| **[[LC1.3.2.2 Message Placeholders]]**                | Add dynamic message content                  | MessagesPlaceholder, variable message history, dynamic insertion                | MessagesPlaceholder injects variable message lists.                 |
| **[[LC1.3.2.3 Role-Based Templates]]**                | Structure by message role                    | SystemMessagePromptTemplate, HumanMessagePromptTemplate, role separation        | Create templates for each role (system, human, AI).                 |
| **[[LC1.3.2.4 System Message Templates]]**            | Define AI behavior instructions              | System prompt patterns, persona definition, constraint setting                  | System messages set context and behavioral guidelines.              |
| **[[LC1.3.2.5 Chat-Specific Formatting]]**            | Handle chat format requirements              | Message ordering, role alternation, content formatting                          | Follow chat conventions for message order and roles.                |

# ChatPromptTemplate: The Conversation Schema

`PromptTemplate` produces a string.
`ChatPromptTemplate` produces a **List of Messages**.

This distinction is vital. If you send a string to a Chat Model (GPT-4), it gets wrapped in a generic `HumanMessage`. You lose the power to give "System Instructions."
`ChatPromptTemplate` allows you to engineer the **Role Topology** of the interaction.

---

## 1. Composition: The Message Stack

A chat prompt is a sequence of roles.

```python
from langchain_core.prompts import ChatPromptTemplate

template = ChatPromptTemplate.from_messages([
    ("system", "You are a specialized legal assistant."),
    ("human", "Explain this contract clause: {clause}"),
])

prompt_value = template.invoke({"clause": "Force Majeure..."})
# Result: [SystemMessage(...), HumanMessage(...)]
```

> **Why Tuples?**: `("role", "content")` is a shorthand. You can also use explicit classes like `SystemMessagePromptTemplate`, but the tuple syntax is the standard readability convention.

---

## 2. MessagesPlaceholder: The History Socket

In a real conversation, you don't know how many messages came before. You need a "Slot" to insert the Chat History dynamically.

**The Anti-Pattern**:
String concatenation. `template = system + history_str + human`. This breaks if the history contains special characters or formatting.

**The Pattern**: `MessagesPlaceholder`.

```python
from langchain_core.prompts import MessagesPlaceholder

template = ChatPromptTemplate.from_messages([
    ("system", "You are a helpful assistant."),
    MessagesPlaceholder(variable_name="chat_history"),
    ("human", "{question}")
])

# Implementation
template.invoke({
    "chat_history": [HumanMessage(content="Hi"), AIMessage(content="Hello")],
    "question": "What is my name?"
})
```

This ensures the history is inserted as **Native Message Objects**, not as a flattened string.

---

## 3. Role Engineering

Different roles have different "Permissions" in the model's cognitive space.

| Role | Permission | Usage |
| :--- | :--- | :--- |
| **System** | High Authority | Set rules, tone, and security guardrails. Harder for users to override. |
| **Human** | Intent Provider | The user's query. |
| **AI** | Example Provider | Used in "Few-Shot" prompting to show *how* the model should have replied. |

**Few-Shotting with Roles**:
To teach a model a specific JSON format, you don't just *tell* it. You *show* it a fake conversation.

```python
few_shot_prompt = ChatPromptTemplate.from_messages([
    ("system", "Convert text to JSON."),
    ("human", "My name is John."),
    ("ai", "{'name': 'John'}"),  # Fake example
    ("human", "{user_input}")     # Real input
])
```

---

## 4. Multi-Modal Inputs

`ChatPromptTemplate` is the only way to send images correctly.

```python
template = ChatPromptTemplate.from_messages([
    ("system", "Describe this image."),
    ("human", [
        {"type": "text", "text": "What is in this picture?"},
        {"type": "image_url", "image_url": "{image_path}"}
    ])
])
```

---

## Quick Reference

| Feature | Code | Why? |
| :--- | :--- | :--- |
| **Tuple Syntax** | `("system", "...")` | Standard, clean shorthand. |
| **History** | `MessagesPlaceholder` | Safety. Prevents injection via history. |
| **Few-Shot** | `("ai", "example")` | Teaches by demonstration. |
| **Output** | `PromptValue` | Can be cast to string or list. |
