| **Subtopic**                                          | **Focus & Purpose**                         | **Key Concepts / Details**                                                    | **One-Line Recall**                                               |
| ----------------------------------------------------- | ------------------------------------------- | ----------------------------------------------------------------------------- | ----------------------------------------------------------------- |
| **[[LC1.1.4.1 Recommended Directory Layout]]**        | Establish a clean folder structure          | `src/`, `prompts/`, `chains/`, `tools/`, `configs/`, `tests/` directories     | Organize code into logical directories for maintainability.       |
| **[[LC1.1.4.2 Organizing Prompts]]**                  | Manage prompt templates effectively         | Prompt files, versioning, separation from logic, template formats             | Keep prompts in dedicated files separate from code.               |
| **[[LC1.1.4.3 Organizing Chains & Agents]]**          | Structure orchestration logic               | Chain modules, agent definitions, composition patterns                        | Group chains and agents into cohesive modules.                    |
| **[[LC1.1.4.4 Configuration Management]]**            | Handle environment and runtime configs      | `.env` files, config loaders, secrets management, environment separation      | Use config files and environment variables for settings.          |
| **[[LC1.1.4.5 Entry Points & Runtime Code]]**         | Define application execution paths          | Main scripts, CLI entry points, API server setup, invocation patterns         | Define clear entry points for running LangChain applications.     |

# Project Structure: Anatomy of a Production App

A LangChain application is not a script; it is a system. Treating it like a script leads to the "Notebook Trap," where logic, prompts, and configuration are hopelessly entangled.

To build for production, we adopt a **Domain-Driven** approach. We separate the *Cognitive Layer* (Prompts) from the *Logic Layer* (Chains) and the *Integration Layer* (Tools).

---

## 1. The Standard Scaffold

This structure scales from a simple chatbot to a complex autonomous agent.

```
my-langchain-app/
├── 📂 app/                   # Application Source Code
│   ├── 📂 chains/            # The "Workflows" (Sequences)
│   │   ├── __init__.py       # Expose specific chains
│   │   └── summary_chain.py  # Specific logic
│   ├── 📂 agents/            # The "Brains" (Decision Makers)
│   │   └── research_agent.py
│   ├── 📂 tools/             # The "Hands" (Integrations)
│   │   └── calc_tool.py
│   └── 📂 server.py          # The API Interface (FastAPI/Streamlit)
│
├── 📂 prompts/               # The "Cognitive Layer" (Separated!)
│   ├── system_instructions.yaml
│   └── email_template.txt
│
├── 📂 tests/                 # Verification
│   ├── test_integration.py   # Connection tests
│   └── test_logic.py         # Unit tests
│
├── 📂 configs/               # Configuration Management
│   └── model_config.yaml     # Model names, temperature settings
│
├── .env                      # Secrets (NEVER COMMIT THIS)
├── pyproject.toml            # Dependencies
└── main.py                   # Entry Point
```

> **Key Principle**: **A Prompt is Code.** But it changes faster than Python code. Keep prompts in their own directory so non-engineers (Prompt Engineers/PMs) can edit them without breaking the app.

---

## 2. Organizing Prompts (The Cognitive Layer)

Hardcoding prompt strings inside Python functions is an anti-pattern. Detailed instructions belong in external files.

*   **Pattern**: Loading from separation.
*   **Format**: YAML or Text is preferred over Python strings for readability.

**Bad (Hardcoded):**
```python
# Impossible to read, impossible to version control distinctly
template = "You are a helpful assistant who answers questions about {topic}..."
```

**Good (Loaded):**
```python
# app/chains/summary_chain.py
from pathlib import Path
prompt_text = Path("prompts/system_instructions.yaml").read_text()
```

---

## 3. Organizing Chains (The Function Layer)

Chains should be stateless definitions. They take input, process it, and return output.

*   **Encapsulation**: Each chain file should export a single `get_chain()` function or a configured Runnable.
*   **Composition**: A "Master Chain" in `app/server.py` simply imports and pipes together smaller chains from `app/chains/`.

**Example:**
`app/chains/rag_chain.py` -> Exports a retriever chain.
`app/chains/format_chain.py` -> Exports a formatting chain.
`main.py` -> `full_chain = rag_chain | format_chain`

---

## 4. Configuration Management

LLM apps have more "knobs" than traditional apps: Model Name (`gpt-4` vs `gpt-3.5`), Temperature, Token Limits, and Base URLs.

*   **Secrets vs Configs**:
    *   **Secrets** (API Keys) -> `.env` (Use `python-dotenv`).
    *   **Hyperparameters** (Temperature) -> `configs/model_config.yaml`.

This allows you to switch from "Debug Mode" (Temperature 0) to "Creative Mode" (Temperature 0.9) without changing code.

---

## 5. Entry Points

Where does the execution start?

1.  **CLI (`main.py`)**: For local testing and development loops.
2.  **API (`app/server.py`)**: For production serving (usually via LangServe or FastAPI).

**The Separation Rule**: Your *Business Logic* (Chains) should never depend on your *Interaction Layer* (FastAPI/CLI). This ensures you can swap the interface without rewriting the bot.

---

## Quick Reference

| Component | best Practice | Why? |
| :--- | :--- | :--- |
| **Prompts** | Store in `prompts/*.yaml` | Allows non-coders to edit; cleaner git diffs. |
| **Chains** | One chain per file in `app/chains/` | Modular testing; easier reuse. |
| **Configs** | `configs/*.yaml` | Change behavior (temp/model) without code deploys. |
| **Secrets** | `.env` only | Security. Never commit API keys. |
| **Tools** | `app/tools/` | Isolates external integration logic. |
