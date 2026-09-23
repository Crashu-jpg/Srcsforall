# SRCS — Safety & Reliability Control Systems
> **Deterministic Pre-Execution Firewall & State-Machine Proxy for Autonomous Web3 & Crypto AI Agents.**

---

## 🛑 Clarification: SRCS is NOT Just a "Guardrail"

Most AI safety tools today call themselves "guardrails," but they are nothing more than **prompt filters or LLM output validators**. They try to guess if text is safe using another LLM.

**SRCS is fundamentally different. It is NOT a prompt filter.**

SRCS is a **deterministic execution proxy state machine** that sits directly between the AI agent runtime and external execution layers (Crypto Wallets, Smart Contracts, DeFi Protocols, and Sensitive APIs). 

* **Prompt Guardrails:** Try to check text *after* the model speaks.
* **SRCS Execution Proxy:** Intercepts state *before* any transaction or code executes, enforcing cryptographic identity, atomic state locks, rolling spend limits, and hash-chained proof of execution.

---

## 🚨 The Web3 Market Opportunity & FOMO

Right now, Silicon Valley startups and Y Combinator-backed companies are rushing to lock down the AI agent security layer behind proprietary closed-source SaaS platforms. They want developers to route private crypto keys, wallet payloads, and transaction states through their black-box servers.

### Why Web3 & Crypto CANNOT Use Closed-Source AI Proxies
1. **The Black-Box Paradox:** You cannot achieve trustless Web3 security by routing agent transactions through an un-auditable, proprietary server.
2. **The Drip-Feed Wallet Attack:** AI agents executing multi-step DeFi transactions can be manipulated via prompt injection to bypass single-tx limiters. SRCS enforces **cumulative rolling-window caps** (e.g., max 2 ETH per 24 hours across 100 micro-transactions).
3. **Open-Source Urgency:** The execution safety standard for Web3 AI agents is being established right now. SRCS exists to ensure this layer remains a **free, transparent public good** rather than a VC-controlled monopoly.

---

## 📊 Proven Engineering Metrics & Statistics

SRCS is not a mock concept. Built independently with production-grade engineering standards, the core engine is fully implemented and tested:

| Metric | Verified Benchmark / Value |
| :--- | :--- |
| **Release Candidate** | `v1.0.0-rc3` |
| **Automated Test Suite** | **209 Passing Tests** |
| **Branch Coverage** | **>90% Branch-Aware Coverage** |
| **Static Security Audit** | **0 High/Medium Vulnerabilities** (Bandit Scan Clean) |
| **Execution Latency** | **< 4ms Pre-Execution Evaluation Time** |
| **Audit Verification** | **100% Deterministic SHA-256 Hash Chaining** |
| **Architecture** | Python FastAPI, Atomic SQLite/PostgreSQL, Sync/Async SDKs |

---

## ⚡ How SRCS Works in Web3 & Crypto

SRCS intercepts every action call before it reaches the execution layer:
```
Core Architecture:-

              [ Web3 / Crypto AI Agent ]
                        │
 1. Proposed Action (e.g., Swap / Transfer / Contract Write)
                        v
┌────────────────────────────────────────────────────────┐
│              SRCS PRE-EXECUTION FIREWALL               │
│                                                        │
│  • Identity Check (SHA-256 API Key RBAC)               │
│  • Rule Engine (Permission Matrix)                     │
│  • 24-Hour Rolling Spend Cap (Smurfing Defense)        │
│  • State Lock (Atomic Claim & Release)                 │
└───────────────────────────┬────────────────────────────┘
|
              ┌─────────────┴─────────────┐    
              │                           │
       [ REJECTED / BLOCKED ]       [ PERMITTED ]
              │                           │
              v                           v
     ┌────────────────────┐      ┌─────────────────────────┐
     │ Hash-Chained Audit │      │ Smart Contract / Wallet │
     │    Log Recorded    │      │  Transaction Executed   │
     └────────────────────┘      └─────────────────────────┘
     ```
   ````
### Core Safety Features
* **Cumulative Spend Limits:** Tracks agent transfers over a rolling 24-hour window to stop "smurfing" and wallet-draining loops.
* **Fail-Closed State Recovery:** If an agent process crashes mid-execution, SRCS automatically recovers the state to `BLOCKED` to prevent orphaned, unverified execution.
* **Tamper-Evident Hash Chain:** Every execution decision generates an immutable cryptographic hash chain, making audit logs tamper-evident.

---

## 💻 Developer Integration (Python SDK)

```python
from srcs_sdk import SRCSClient

# Initialize local or self-hosted SRCS Proxy
client = SRCSClient(api_key="srcs-agent-key")

# Intercept a crypto transfer proposal before sending to network
decision = client.intercept(
    agent_id="DeFi-Arbitrage-Bot-01",
    action_type="wallet_transfer",
    payload={"amount_usdc": 500, "recipient": "0x742d...44e"}
)

if decision["status"] == "ALLOWED":
    # Safe to sign and broadcast transaction on-chain
    execute_blockchain_transaction()
else:
    # Action blocked deterministically before hitting the blockchain
    print(f"Transaction Blocked [{decision['reason_code']}]: {decision['message']}")


``` 
Project Progress & Roadmap
[x] Phase 1 (Complete): Core engine, deterministic policy evaluator, 209 passing tests, fail-closed recovery, local hash chaining.

[ ] Phase 2: Complete Python framework middleware (srcs-langchain, srcs-crewai).

[ ] Phase 3: On-chain audit checkpointing (anchoring log head-hashes directly to Base / Filecoin / L2s).

[ ] Phase 4: Model Context Protocol (MCP) Gateway Proxy wrapper for AI tool servers.

📄 License
Dual-licensed under Apache License 2.0 and MIT License — Open Source Public Good.
