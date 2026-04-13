---
role: rule
ai-assist:
  - https://chatgpt.com/c/698e795e-7a94-8320-adbb-34078974014f
---
### [[ADR v1 - Metadata|Metadata]]:

`adr-id`: ADR-XXXX
`adr-version`: X
`created-at`: YYYY-MM-DDTHH:mm
`status`: proposed | approved | implemented | deprecated | superseded
`proposer`: CC | H
`urgency`: high | medium | low
`risk-level`: high | medium | low | negligible
`change-domain`: skill | model | software | system | policy | memory
`impact-scope`: local | system-wide
`reversibility`: reversible | partially-reversible | irreversible
`related-adrs`: [ADR-XXXX, ADR-YYYY]

### Content:

**Context**  
Describe the situation, constraints, and conditions that led to this decision.  
State facts only. No conclusions or preferences.

**Decision**  
State exactly what is being changed, added, removed, or adopted.  
This section must be unambiguous and executable.

**Rationale**  
Explain why this decision was chosen over alternatives.  
Include assumptions, tradeoffs, and reasoning used at the time.
If the selected **urgency** or **risk-level** is non-obvious or counterintuitive, the reasoning must be explained here.  s

**Alternatives Considered**  
List other viable options that were available, including why they were not chosen.

**Success Criteria**  
Define concrete, observable conditions that determine whether the decision is successful.

**Rollback Plan**  
Describe how to revert or mitigate the change if success criteria are not met.

**Rejection Reasoning** _(required if status = rejected)_  
Explain why the decision was declined.  
This reasoning must be human-authored and explicit.

**Deprecation Reasoning** _(required if status = deprecated)_  
Explain why the decision is no longer preferred and under what conditions it remains in use, if any.

**Supersession Reasoning** _(required if status = superseded)_  
Explain why this decision was replaced and reference the ADR(s) that supersede it.

**Notes**  
Record additional assumptions, constraints, or future considerations that do not fit elsewhere.
