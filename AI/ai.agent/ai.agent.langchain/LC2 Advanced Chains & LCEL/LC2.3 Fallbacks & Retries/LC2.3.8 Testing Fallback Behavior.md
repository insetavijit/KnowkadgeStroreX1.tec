| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC2.3.8.1 Simulating Failures]]**                 | Test fallback activation                     | Mock failures, error injection, chaos testing                                   | Simulate failures to test fallback activation.                      |
| **[[LC2.3.8.2 Testing Fallback Activation]]**         | Verify fallbacks trigger                     | Unit tests, integration tests, activation verification                          | Test that fallbacks activate correctly on errors.                   |
| **[[LC2.3.8.3 Coverage]]**                            | Test all fallback paths                      | Path coverage, edge cases, exhaustive testing                                   | Test all fallback paths for comprehensive coverage.                 |
| **[[LC2.3.8.4 Regression Testing]]**                  | Prevent fallback regressions                 | Automated tests, CI/CD integration, regression prevention                       | Include fallback tests in automated regression suite.               |
| **[[LC2.3.8.5 Fallback Monitoring]]**                 | Track fallback usage in production           | Fallback metrics, activation rates, alerting                                    | Monitor fallback usage to detect upstream issues.                   |

# Testing Fallback Behavior: Chaos Engineering

You designed your fallbacks. But have you *proven* they work?
The only way to know is to **Cause a Failure Intentionally**.

---

## 1. The "Mock Failure" Test

```python
import pytest
from unittest.mock import patch

def test_fallback_activates_on_timeout():
    # Mock the primary LLM to always raise
    with patch.object(ChatOpenAI, "invoke", side_effect=TimeoutError):
        result = resilient_chain.invoke("test")
    
    # Assert that the result came from the fallback
    assert "I am currently unavailable" in result
```

**Principle**: If you can't trigger the fallback in tests, you don't really have a fallback.

---

## 2. Production Monitoring (Fallback Rate)

A key metric: **Fallback Activation Rate**.
*   Under 1%: Healthy.
*   1-5%: Warning. Investigate intermittent issues.
*   Over 5%: Alert. Something is systematically wrong with the primary.

```python
# In a Custom Callback Handler
class FallbackMonitor(BaseCallbackHandler):
    def on_chain_error(self, error, **kwargs):
        metrics.increment("primary_failures")
    
    def on_fallback_start(self, **kwargs):
        metrics.increment("fallback_activations")
```

---

## 3. Chaos Engineering (In Production)

Netflix's Chaos Monkey randomly kills servers. You can do the same for LLMs.

**Pattern**: Scheduled Degradation.
Once a week (at 3 AM on Sunday), force the primary LLM to fail. Verify the fallback takes over.

This is a **Fire Drill** for your AI system.

---

## Quick Reference

| Level | What to Test | How |
| :--- | :--- | :--- |
| **Unit** | Single Runnable Fallback | `pytest` with mocks. |
| **Integration** | Chain with Fallbacks | LangSmith dataset playback. |
| **Production** | Live System Resilience | Chaos Engineering / Fire Drills. |
