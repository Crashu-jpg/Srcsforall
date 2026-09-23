# SRCS — Safety & Reliability Control Systems
> **Deterministic Pre-Execution Authorization & Tamper-Evident Audit Guardrails for Web3 AI Agents.**

---

## 🚨 The Market Gap: Why SRCS Will Revolutionize Web3 AI

Right now, almost every AI agent guardrail tool on the market is **CLOSED SOURCE**, controlled by well-funded Silicon Valley startups and VC platforms. They force developers to route private transaction payloads, API keys, and sensitive workflow states through third-party proprietary servers.

This creates a dangerous paradox: **you cannot guarantee deterministic security by relying on a proprietary black box.**

### The Open Source Breakthrough
* **No Black-Box Lock-in:** Security infrastructure for autonomous Web3 AI agents must be transparent, locally verifiable, and self-hostable.
* **Dominating the Web3 Agent Layer:** Web3 agents are managing real crypto capital, smart contracts, and high-value APIs. SRCS delivers the first open-source, deterministic firewall with cumulative rolling transfer caps to prevent wallet-draining attacks.
* **Public Good Standard:** By backing SRCS, funders ensure that the fundamental safety layer for autonomous AI agents remains a free, open-source public good—rather than a closed monopoly.

---

## 🔓 Code Availability & Funding Commitment

> **Current Repository Status:** **Private Release Candidate (`v1.0.0-rc3`)**

For obvious pre-launch security reasons, threat-model verification, and IP protection during active development, the full codebase is currently held in a private repository. 

**Our Commitment to Funders:**
Upon receiving grant funding, we will finalize the remaining integration adapters (LangChain/CrewAI), complete on-chain audit log anchoring, and immediately transition the entire codebase to **100% Public Open Source** under the dual Apache 2.0 / MIT license.

---

## 📈 Current Progress & Production Hygiene

SRCS is not vaporware. The core engine is already built and validated with rigorous engineering standards:

* **Release Candidate:** `v1.0.0-rc3` (Internal rehearsal complete)
* **Automated Test Suite:** 209 passing tests
* **Test Coverage:** >90% branch-aware coverage enforced in CI
* **Security Audits:** Automated Bandit static analysis & Ruff linting green
* **SDKs Ready:** Synchronous & Asynchronous Python SDKs built (`srcs_sdk`)

---

## ⚡ Core Architecture




















### Key Safety Capabilities
1. **Deterministic Policy Engine:** Finite-state rules with stable, machine-readable reason codes.
2. **Cumulative Smurfing Defense:** Evaluates rolling 24-hour agent spend limits to stop "drip-feed" wallet drains.
3. **Fail-Closed Recovery:** Automatically recovers workflows stuck in `EXECUTING` state after process crashes.
4. **Tamper-Evident Audit Chain:** Hash-chained event logs with head checkpoints to detect log tampering or deletion.

---

## 💻 Python SDK Preview

python
from srcs_sdk import SRCSClien

with SRCSClient(api_key="your-agent-key") as client:
    decision = client.intercept(
        agent_id="Web3-Agent-01",
        action_type="contract_execution",
        payload={"value_eth": 1.5}
    )
    
    if decision["status"] == "ALLOWED":
        # Execute tool or transaction safely
        print("Authorized:", decision["workflow_id"])
    else:
        print(f"Blocked [{decision['reason_code']}]: {decision['message']}")
🛣️ Grant Milestones & Next Steps
[x] Phase 1 (Done): Core deterministic engine, fail-closed recovery, local hash-chaining (209 passing tests).

[ ] Phase 2 (Grant Funded): Open-source public repository release & PyPI package distribution.

[ ] Phase 3 (Grant Funded): On-chain audit checkpointing (anchoring log hashes on Base / IPFS / Filecoin).

[ ] Phase 4 (Grant Funded): Drop-in 1-line middleware plugins (srcs-langchain, srcs-crewai, srcs-mcp).

📄 Open Source License
Committed to dual-licensing under Apache License 2.0 and MIT License upon public grant release
