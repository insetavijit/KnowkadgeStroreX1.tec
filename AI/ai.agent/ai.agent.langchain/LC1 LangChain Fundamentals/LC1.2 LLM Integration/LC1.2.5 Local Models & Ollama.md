| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC1.2.5.1 Running Local LLMs]]**                  | Understand local model deployment            | CPU/GPU requirements, memory considerations, latency trade-offs                 | Local LLMs offer privacy but require hardware resources.            |
| **[[LC1.2.5.2 Ollama Integration]]**                  | Use Ollama with LangChain                    | ChatOllama, Ollama model library, pulling models, configuration                 | Use ChatOllama() to connect to locally running Ollama models.       |
| **[[LC1.2.5.3 LlamaCpp Integration]]**                | Run GGUF models directly                     | LlamaCpp class, GGUF model files, n_ctx, n_gpu_layers                           | LlamaCpp runs quantized GGUF models directly in Python.             |
| **[[LC1.2.5.4 HuggingFace Local Models]]**            | Use HuggingFace transformers locally         | HuggingFacePipeline, model loading, tokenizers, device placement                | HuggingFacePipeline wraps transformers for local inference.         |
| **[[LC1.2.5.5 Local vs Cloud Trade-Offs]]**           | Compare deployment options                   | Privacy, cost, latency, capability, maintenance, scaling                        | Choose local for privacy/cost; cloud for capability/scale.          |

# Local Models: The Sovereign AI Stack

Running models locally (on your own hardware) is the ultimate architectural shift. It moves AI from a "Service" (API) to a "Utility" (Binary).

**Why bother?**
1.  **Privacy**: Legal/Medical data never leaves your VPC.
2.  **Cost**: Zero per-token fees. (Only electricity).
3.  **Latency**: Zero network overhead.

---

## 1. The Architecture of Local Inference

In Cloud AI, you have a client (`langchain-openai`) and a remote server.
In Local AI, you generally have two choices: **The Embedded Engine** or **The Inference Server**.

### Option A: The Inference Server (Ollama)
This is the "Docker for LLMs." Recommended for 95% of users.
*   **Architecture**: Ollama runs as a background service (daemon) exposing a localhost API (`http://127.0.0.1:11434`).
*   **LangChain Role**: `ChatOllama` acts as a thin client hitting that local API.

```python
from langchain_community.chat_models import ChatOllama

# Connects to localhost:11434 by default
chat = ChatOllama(model="llama3")
```

### Option B: The Embedded Engine (LlamaCpp)
This runs the model *inside* your Python process RAM.
*   **Architecture**: Python C-bindings load the GGUF file directly into memory.
*   **Pros**: precise control over raw logits.
*   **Cons**: If your app crashes, the model crashes. Blocking IO.

---

## 2. Quantization: The Magic Trick

How do you fit a 70GB model onto a 16GB MacBook? **Quantization**.
We reduce the precision of weights from 16-bit floats (`FP16`) to 4-bit integers (`Q4_K_M`).

*   **Impact**: 75% RAM reduction with <1% quality loss.
*   **GGUF Protocol**: The file format standard for these quantized models.

> **Mental Model**: If `gpt-4` is a lossless FLAC audio file, `llama-3-q4` is a high-quality MP3.

---

## 3. Ollama Integration Details

Ollama handles the hardware abstraction (Metal on Mac, CUDA on NVidia). LangChain provides the interface.

**Streaming & JSON Mode**:
Just like OpenAI, `ChatOllama` supports the full Runnable protocol.

```python
chat = ChatOllama(
    model="mistral",
    format="json", # Enforce JSON output
    temperature=0
)

for chunk in chat.stream("Why is the sky blue?"):
    print(chunk.content, end="", flush=True)
```

**Keep-Alive**:
Local models take time to load into VRAM (3-10s). Ollama keeps them loaded for 5 minutes by default. LangChain handles the pings to keep them "hot."

---

## 4. The Trade-Off Matrix

| Feature | OpenAI (Cloud) | Ollama (Local) |
| :--- | :--- | :--- |
| **Intelligence** | 10/10 (GPT-4) | 7/10 (Llama-3-70b) |
| **Privacy** | Trusted Third Party | **Absolute** |
| **Cost** | $$$/Token | Fixed (Hardware) |
| **Latency** | Network + Inference | Pure Inference (Fast on GPU) |
| **Setup** | API Key | Install Drivers + RAM Tuning |

---

## 5. HuggingFace Pipelines (The Researcher's Path)

For those who need raw access to `transformers` (e.g., fine-tuning or experimental architectures not supported by Ollama yet):

```python
from langchain_huggingface import HuggingFacePipeline

# Downloads raw weights (~20GB) to disk
llm = HuggingFacePipeline.from_model_id(
    model_id="meta-llama/Meta-Llama-3-8B",
    task="text-generation",
    pipeline_kwargs={"max_new_tokens": 100}
)
```

**Warning**: This is heavy. It requires managing CUDA versions, `torch` dependencies, and massive disk space manually. Use primarily for R&D.

---

## Quick Reference

| Tool | Role | Best For |
| :--- | :--- | :--- |
| **Ollama** | The standard server | Developers, Production Inference. |
| **LlamaCpp** | Direct embedding | Edge devices, Raspberry Pi. |
| **GGUF** | File format | Efficient storage of quantized models. |
| **ChatOllama**| The LangChain Client | Connecting your code to the local metal. |
