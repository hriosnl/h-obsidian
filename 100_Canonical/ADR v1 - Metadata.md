---
role: rule
ai-assist:
  - https://chatgpt.com/c/698e795e-7a94-8320-adbb-34078974014f
---
**adr-id**  
A unique, permanent identifier for this decision record.  
It must never be reused or changed.  
Its purpose is stable referencing and traceability across time.


---

**adr-version**  
The version of the ADR schema and governance rules in effect when this ADR was created.  
It does not describe the decision itself and must not change after creation.  
It is used to correctly interpret metadata semantics in the future.


---

**created-at**  
The exact timestamp when the ADR was first created.  
It represents when the decision was proposed, not when it was approved or implemented.


---

**status**  
The current lifecycle state of the decision.

- **proposed**  
    The decision is suggested but not yet approved.

- **approved**  
    The decision is authorized but not yet executed.

- **implemented**  
    The decision has been executed and is in effect.

- **rejected**  
    The decision was formally evaluated and explicitly declined.  
    When an ADR is marked as _rejected_, a **human-authored reasoning** explaining why the decision was rejected **must be added** to the ADR content.


- **deprecated**  
    The decision is no longer recommended but may still be in use.
    When an ADR is marked as _deprecated_, a **reasoning explaining why the decision is no longer preferred** must be added to the ADR content.

- **superseded**  
    The decision has been explicitly replaced by another ADR.
    When an ADR is marked as _superseded_, a **reasoning explaining the replacement** and references to the superseding ADR(s) **must be added** to the ADR content.

---

**proposer**  
Identifies who initiated the decision.

- **cc**  
    The decision was proposed autonomously by CC.

- **H**  
    The decision was proposed by H.


---

**urgency**  
Describes how time-sensitive the decision is, independent of risk.

- **high**  
    Delay will cause immediate or near-term degradation, blockage, or loss of capability.

- **medium**  
    Delay is acceptable for a limited time; acting sooner improves outcomes but is not critical.

- **low**  
    No time pressure; postponement has no negative impact.


---

**risk-level**  
Describes the likelihood and severity of negative outcomes if the change fails.

- **high**  
    Failure can cause loss of control, security exposure, irreversible damage, or inability to recover.

- **medium**  
    Failure can degrade core functionality but does not threaten overall recoverability.

- **low**  
    Failure affects non-core behavior and is contained and recoverable.

- **negligible**  
    Failure has no meaningful impact beyond minor inconvenience.


---

**change-domain**  
Describes which part of CC is primarily affected by the decision.  
This list is extensible.

- **[[Skill|skill]]**  
    Adds or modifies a specific capability.

- **model**  
    Changes the AI model or inference behavior.

- **software**  
    Installs, removes, or modifies external tools.

- **system**  
    Alters core architecture or permissions.

- **policy**  
    Changes governing rules or constraints.

- **memory**  
    Alters information storage or retrieval.


---

**impact-scope**  
Describes how broadly the change affects CC.

- **local**  
    The change affects a single, isolated component.

- **system-wide**  
    The change affects core mechanisms or multiple components.


---

**reversibility**  
Describes the ability to undo the change and restore the prior state.

- **reversible**  
    Full restoration is possible with no loss.

- **partially-reversible**  
    Functional restoration is possible with some loss.

- **irreversible**  
    The prior state cannot be restored.


---

**related-adrs**  
A list of ADR identifiers that are contextually linked to this decision, such as dependencies or superseded records.
