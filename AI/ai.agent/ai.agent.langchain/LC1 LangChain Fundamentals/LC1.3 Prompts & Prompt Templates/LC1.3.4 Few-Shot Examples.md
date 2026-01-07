| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC1.3.4.1 Adding Examples to Prompts]]**          | Include demonstrations                       | Example formatting, input-output pairs, example structure                       | Include examples to demonstrate expected behavior.                  |
| **[[LC1.3.4.2 FewShotPromptTemplate]]**               | Use dedicated few-shot templates             | FewShotPromptTemplate class, example_prompt, examples list                      | FewShotPromptTemplate manages example formatting.                   |
| **[[LC1.3.4.3 Example Formatting]]**                  | Format examples consistently                 | Example templates, separator strings, prefix/suffix                             | Format each example with consistent input/output structure.         |
| **[[LC1.3.4.4 Dynamic Example Selection]]**           | Choose relevant examples                     | ExampleSelector, semantic similarity, length-based selection                    | Use ExampleSelector to pick relevant examples dynamically.          |
| **[[LC1.3.4.5 Example Separators]]**                  | Delineate between examples                   | Separator strings, prefix/suffix, visual breaks, parsing considerations         | Use separators to clearly distinguish between examples.             |

# Few-Shot Examples: In-Context Learning (ICL)

The most powerful lever in Prompt Engineering is not the instruction; it is the **Example**.
Telling a model "Output JSON" succeeds 80% of the time.
Showing a model `User: "Hi" -> AI: "{'msg': 'Hi'}"` succeeds 99% of the time.

LangChain formalizes this "Teaching by Demonstration" into the `FewShotPromptTemplate`.

---

## 1. The Legacy Way (String Few-Shot)

For completion models (and simple text tasks), you "bake" the examples into the string.

```python
from langchain_core.prompts import PromptTemplate, FewShotPromptTemplate

# 1. Define the Example Structure
example_formatter = PromptTemplate.from_template(
    "Word: {word}\nAntonym: {antonym}"
)

# 2. Define the Syllabus
examples = [
    {"word": "happy", "antonym": "sad"},
    {"word": "tall", "antonym": "short"},
]

# 3. Compile the Prompt
prompt = FewShotPromptTemplate(
    examples=examples,
    example_prompt=example_formatter,
    prefix="Give the antonym for every input.",
    suffix="Word: {input}\nAntonym:",
    input_variables=["input"],
    example_separator="\n\n"
)
```

**Why Use A Class?**: Why not just f-string it?
Because `FewShotPromptTemplate` validates that your examples match your schema variables.

---

## 2. The Modern Way (Chat Few-Shot)

For `ChatModel` (GPT-4), baking examples into a single string is suboptimal.
You should inject them as **Fake History**.

```python
from langchain_core.prompts import (
    ChatPromptTemplate, 
    FewShotChatMessagePromptTemplate
)

# 1. Define the Example Structure (As Messages!)
example_prompt = ChatPromptTemplate.from_messages([
    ("human", "{word}"),
    ("ai", "{antonym}")  # Showing the model how to behave
])

examples = [
    {"word": "happy", "antonym": "sad"},
    {"word": "tall", "antonym": "short"},
]

# 2. Create the Few-Shot Block
few_shot_prompt = FewShotChatMessagePromptTemplate(
    example_prompt=example_prompt,
    examples=examples
)

# 3. Assemble the Final Chain
final_prompt = ChatPromptTemplate.from_messages([
    ("system", "You are an antonym generator."),
    few_shot_prompt,  # Inserts the Fake History here
    ("human", "{input}")
])
```

> **Architectural Advantage**: This leverages the model's native training on conversation turns. It is far more robust than separators (`\n\n`) which the model might ignore.

---

## 3. Dynamic Selection (The "RAG" of Prompts)

You cannot put 1,000 examples in the context window.
You need to pick the **Top-K most relevant examples**.
This is effectively "RAG for Prompt Engineering."

LangChain provides the `SemanticSimilarityExampleSelector`.

```python
from langchain_chroma import Chroma
from langchain_openai import OpenAIEmbeddings
from langchain_core.example_selectors import SemanticSimilarityExampleSelector

# 1. Initialize Vector Store with Examples
selector = SemanticSimilarityExampleSelector.from_examples(
    examples,
    OpenAIEmbeddings(),
    Chroma,
    k=1  # Only pick the 1 best example
)

# 2. Use Selector instead of hardcoded list
few_shot_prompt = FewShotChatMessagePromptTemplate(
    example_selector=selector, # Dynamic!
    example_prompt=example_prompt,
)
```

**Runtime Behavior**:
*   Input: "Gigantic" -> Selector finds "Tall/Short" -> Prompt uses that example.
*   Input: "Elated" -> Selector finds "Happy/Sad" -> Prompt uses that example.

---

## Quick Reference

| Method | Use Case | Mechanism |
| :--- | :--- | :--- |
| **Fixed Lists** | Production Stability | Hardcoded list of 3-5 golden examples. |
| **Selectors** | Long-tail Knowledge | Dynamic retrieval from a database of 100+ examples. |
| **Fake History**| Chat Models | Inserting `Human -> AI` pairs before the real query. |
| **Suffix** | Completion Models | The text that comes *after* the examples (usually the user query). |
