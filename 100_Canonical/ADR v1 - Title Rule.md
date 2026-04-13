---
role: rule
ai-assist:
  - https://chatgpt.com/c/698e795e-7a94-8320-adbb-34078974014f
---
An ADR title must be a **single declarative sentence** that states the **final architectural decision** in clear, concrete terms.

### Core requirements
- State **what is being adopted, enforced, added, removed, or replaced**
- Use a verb that implies execution or commitment
- Refer to a **system domain or capability**, not a vague concept
- The title must still be unambiguous when read alone in a list
- Explicitly include **what is chosen** and **what is rejected**
- Do not describe intent, exploration, or process

### Contrast requirement
- If the decision **explicitly forbids, replaces, or constrains** a viable alternative, the rejected option **must** be named in the title using a clear contrast (e.g., “not”, “instead of”, “replacing”)
- If the decision is purely additive or enabling, **do not invent a contrast**

### Examples
- Run Core Reasoning Locally, Not via External APIs
- Replace Heuristic Planning with Model-Based Planning
- Add Vision Capability to CC
- Introduce Structured Memory for User Preferences