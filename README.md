# Zero-Trust LLM Gateway

A production-grade, highly performant reverse proxy engineered to enforce **NIST SP 800-207 Zero Trust Architecture** and **NIST AI RMF** compliance for autonomous agent workflows and enterprise LLM usage.

## 🚀 Architectural Pillars

* **Cryptographic Machine Identity Auth:** Eliminates standard long-lived static tokens, validating incoming client workloads utilizing mutual TLS (mTLS) properties and cryptographically bound session-level authorization tokens.
* **Inline Data Loss Prevention (DLP):** Real-time, regex-driven matching combined with Named Entity Recognition (NER) models to intercept payloads and scrub Protected Health Information (PHI) or PII at the network edge before it reaches upstream cloud platforms.
* **Decoupled Policy Engine (OPA):** Out-of-band Policy Decision Point validation powered by Open Policy Agent (`rego`), checking identity roles, maximum permissible context constraints, and regulatory boundary rules dynamically.
* **Deterministic Re-Identification:** Features tokenization mapping logic to securely preserve upstream analytics without leaking sensitive raw customer structures.

## 🛠️ Technology Stack

* **Framework:** FastAPI (Asynchronous Python ASGI backend)
* **Policy Enforcement:** Open Policy Agent (OPA)
* **Data Defense:** Microsoft Presidio & Advanced Pre-compiled REGEX Pipes
* **Client Protocol:** HTTPX / Model Context Protocol (MCP) compatible

## 📦 Local Installation & Deployment

### 1. Set Up Environment Variables
Create a `.env` configuration file in the project base directory:
```bash
UPSTREAM_API_URL="[https://api.anthropic.com/v1/messages](https://api.anthropic.com/v1/messages)"
UPSTREAM_API_KEY="your-high-privilege-upstream-key-here"
OPA_SERVER_URL="http://localhost:8181/v1/data/llm/authz"
