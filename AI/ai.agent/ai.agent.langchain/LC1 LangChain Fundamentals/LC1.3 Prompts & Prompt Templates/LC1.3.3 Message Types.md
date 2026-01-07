| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC1.3.3.1 SystemMessage]]**                       | Define system-level instructions             | SystemMessage class, setting AI behavior, context establishment                 | SystemMessage sets the AI's role and constraints.                   |
| **[[LC1.3.3.2 HumanMessage]]**                        | Represent user inputs                        | HumanMessage class, user queries, input content                                 | HumanMessage contains the user's input to the AI.                   |
| **[[LC1.3.3.3 AIMessage]]**                           | Represent assistant responses                | AIMessage class, model outputs, conversation history                            | AIMessage holds the AI's response in conversation.                  |
| **[[LC1.3.3.4 ToolMessage & FunctionMessage]]**       | Handle tool/function outputs                 | ToolMessage, FunctionMessage, tool_call_id, function results                    | ToolMessage returns results from tool executions.                   |
| **[[LC1.3.3.5 Message Content Structure]]**           | Understand content formats                   | String content, multimodal content, content blocks, metadata                    | Messages can contain text, images, or structured content.           |

# Message Types: The Data Structure of Thought

In raw APIs (OpenAI), messages are loose dictionaries: `{"role": "user", "content": "..."}`.
In LangChain, messages are **Strictly Typed Classes**.

Why the extra abstraction?
1.  **Normalization**: It maps `role="model"` (Gemini) and `role="assistant"` (OpenAI) to a single `AIMessage`.
2.  **Payload Verification**: It ensures Tool Calls match Tool Outputs via IDs.
3.  **Multimodality**: It handles image encoding consistently.

---

## 1. The Core Trinity

### SystemMessage (The Laws of Physics)
This message is unseen by users but defines the reality for the model.
*   **Usage**: Security policies, personality, output format constraints.
*   **Architectural Note**: Some models (older Llama 2) do not support this natively. LangChain automatically "shims" it by prepending it to the first `HumanMessage` if needed.

### HumanMessage (The Stimulus)
The user's input.
*   **Advanced**: In multimodal models, `.content` can be a list: `[{"text": "Look at this"}, {"image_url": "..."}]`.

### AIMessage (The Response)
The model's output.
*   **Property**: `.tool_calls` -> A list of structured tool requests (e.g., `{'name': 'search', 'args': {'q': 'weather'}}`). This is distinct from `.content` (which might be empty during a tool call).

---

## 2. The Tool Protocol (`ToolMessage`)

This is where beginners get stuck.
When an AI calls a tool, the conversation enters a **Stateful Loop**.

**The Sequence**:
1.  `HumanMessage`: "What is the weather?"
2.  `AIMessage`: "I need to check." (Includes `tool_calls=[{id='call_123'}]`)
3.  **`ToolMessage`**: "25 Degrees." (Must include `tool_call_id='call_123'`)
4.  `AIMessage`: "The weather is 25 degrees."

**The Critical Rule**:
You cannot send a `ToolMessage` without a preceding `AIMessage` that requested it. The `tool_call_id` must match exactly. If you break this chain, the model creates a "Orphaned Tool Output" error.

```python
from langchain_core.messages import ToolMessage

# Correct Response to a tool call
msg = ToolMessage(
    content='{"temperature": 25}', 
    tool_call_id='call_A1B2C3D4',
    name='get_weather'
)
```

---

## 3. Multimodality (Images/Audio)

Text is easy. Images are hard. LangChain standardizes the "Content Block" format.

```python
from langchain_core.messages import HumanMessage

msg = HumanMessage(content=[
    {
        "type": "text", 
        "text": "Describe this architecture"
    },
    {
        "type": "image_url", 
        "image_url": {"url": "https://example.com/diagram.png"}
    }
])
```

This works identically on `ChatOpenAI` (GPT-4o) and `ChatAnthropic` (Claude 3.5), despite their APIs expecting completely different JSON structures for images.

---

## Quick Reference

| Class | Role | Key Attribute |
| :--- | :--- | :--- |
| **SystemMessage** | Context | `.content` (String) |
| **HumanMessage** | Input | `.content` (String or List) |
| **AIMessage** | Output | `.tool_calls` (List[Dict]) |
| **ToolMessage** | Function Result | `.tool_call_id` (Match required) |
| **FunctionMessage**| *Legacy* | **Do not use.** Deprecated in favor of `ToolMessage`. |

> **Pro Tip**: Use `convert_to_messages(dict)` utility if you need to ingest raw JSON dumps from logs back into LangChain objects.
