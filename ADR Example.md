---
role: definition
---
## **ADR-001: Run Core Reasoning Locally, Not via External APIs**

**[Metadata]**

* adr-id: ADR-001
* adr-version: 1
* created-at: 2026-02-13T10:30
* status: approved
* proposer: CC
* urgency: medium
* risk-level: medium
* change-domain: system
* impact-scope: system-wide
* reversibility: partially-reversible
* related-adrs: []

---

**[Content]**

**Context**
CC requires reliable, low-latency reasoning with predictable behavior. External APIs introduce variability in availability, cost, latency, and policy changes. Long-term autonomy and control require minimizing dependency on external services for core cognition.

**Decision**
Core reasoning and decision-making will run locally on CC’s machine. External APIs may be used only for non-core tasks such as optional enrichment or fallback capabilities.

**Rationale**
Local execution provides deterministic performance, full control over data, and independence from third-party constraints. While external APIs may offer stronger models at times, reliance on them for core reasoning introduces unacceptable operational and governance risk.

**Alternatives Considered**

* Fully external reasoning via third-party APIs: rejected due to dependency and control risk.
* Hybrid core reasoning split across local and external services: rejected due to complexity and unclear failure modes.

**Success Criteria**

* CC performs core reasoning without requiring external API calls.
* Reasoning latency remains within acceptable local hardware limits.
* System continues to function during complete external network outages.

**Rollback Plan**
If local reasoning proves insufficient, temporarily re-enable external APIs for specific reasoning tasks while preserving local execution as the default path.

**Notes**
This decision assumes local hardware can support required model sizes. If hardware constraints change, a new ADR may be required.
