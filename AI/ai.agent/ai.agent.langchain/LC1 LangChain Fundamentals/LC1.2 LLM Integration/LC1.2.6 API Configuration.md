| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC1.2.6.1 API Keys & Environment Variables]]**    | Manage credentials securely                  | .env files, os.environ, python-dotenv, secret management                        | Store API keys in environment variables, never in code.             |
| **[[LC1.2.6.2 Timeout Settings]]**                    | Configure request timeouts                   | request_timeout, connection timeout, read timeout, retry after timeout          | Set timeouts to handle slow or unresponsive API calls.              |
| **[[LC1.2.6.3 Base URLs & Custom Endpoints]]**        | Configure alternative API endpoints          | base_url parameter, Azure OpenAI, self-hosted endpoints, proxies                | Override base_url for Azure or custom API deployments.              |
| **[[LC1.2.6.4 Retry Configuration]]**                 | Handle transient failures                    | max_retries, exponential backoff, retry conditions, CircuitBreaker              | Configure retries to handle rate limits and transient errors.       |
| **[[LC1.2.6.5 Secure Credential Handling]]**          | Protect sensitive information                | Secret managers, vault integration, credential rotation, audit logging          | Use secret managers for production credential handling.             |

# API Configuration: The Production Harness

Connecting to an LLM is easy. Staying connected at scale is hard.
In production, you face **Rate Limits**, **Latency Spikes**, and **Network Outages**.
LangChain's configuration layer is your "Seatbelt."

---

## 1. Reliability Engineering (Retries & Timeouts)

By default, network calls hang. If OpenAI is down, your app shouldn't freeze for 2 minutes.

### The Timeout Strategy
Always set an explicit timeout.
*   **Connect Timeout**: Is the server reachable? (Short: 5s)
*   **Read Timeout**: Is the model generating? (Long: 60s)

```python
chat = ChatOpenAI(
    request_timeout=30, # Raise error after 30 seconds
    max_retries=3       # Try 3 times before giving up
)
```

**Architectural Note on Backoff**:
LangChain uses **Exponential Backoff** (Wait 1s, then 2s, then 4s). This prevents your app from accidentally DDoS-ing the provider during an outage.

---

## 2. Enterprise Routing (Base URLs)

Not everyone connects to `api.openai.com`.
Enterprises often use **Azure OpenAI** or internal **API Gateways** (like Kong or LiteLLM) for governance.

### Azure OpenAI (The Corporate Standard)
Microsoft hosts OpenAI models on Azure infrastructure. The interface is same, but the endpoint differs.

```python
from langchain_openai import AzureChatOpenAI

chat = AzureChatOpenAI(
    azure_endpoint="https://my-corp.openai.azure.com/",
    azure_deployment="gpt-4-turbo-corporate",
    api_version="2024-02-15-preview"
)
```

### Proxies & Gateways
If you are using a proxy for logging or caching (e.g., Helicone, Portkey), you simply override the `base_url`.

```python
# Route traffic through a logging proxy
chat = ChatOpenAI(
    base_url="https://gateway.helicone.ai/v1",
    api_key="sk-..."
)
```

---

## 3. Secret Hygiene

API Keys are "Bearar Tokens"—whoever holds them can spend your money.

### Level 1: Environment Variables (Standard)
The `.env` file approach.
```python
# Good for Dev
import dotenv
dotenv.load_dotenv()
```

### Level 2: Runtime Injection (Production)
In Kubernetes/AWS Lambda, you inject secrets at runtime.
```python
# Better: Pass explicitly from a Secret Manager
pwd = aws_secrets.get("OPENAI_KEY")
chat = ChatOpenAI(api_key=pwd)
```

### Level 3: Token Rotation
For high security, keys rotate daily. Your application logic must handle re-instantiation if an `AuthenticationError` occurs.

---

## 4. Rate Limiting (The "429" Error)

LLM providers enforce strict limits (e.g., 500 RPM).
LangChain handles simple retries, but for **High Throughput** apps, you need a client-side limiter.

**The "Token Bucket" Pattern**:
While not built-in to the `ChatModel` class, it is architecturally standard to wrap your LangChain invocations in a semaphore to ensure you don't flood the API.

---

## Quick Reference

| Config | Code | Why? |
| :--- | :--- | :--- |
| **Timeout** | `request_timeout=10` | Fail fast instead of hanging. |
| **Retries** | `max_retries=5` | Handle "blips" automatically. |
| **Proxy** | `base_url="..."` | Use Gateways/Azure/LocalAI. |
| **Model** | `model="gpt-4"` | Select intelligence level. |
