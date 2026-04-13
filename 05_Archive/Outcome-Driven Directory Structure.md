---
ai-assist:
  - https://chatgpt.com/c/69904f50-6b5c-8322-a952-b697f2973cb9
  - https://chatgpt.com/c/6990590e-ebd4-8320-90f9-3aa05d599dfa
---
An outcome-driven directory structure is organized by **outcomes**, not by technology, layer, or function.

It treats the filesystem as a map of **intent**, not implementation.

An _outcome_ is a concrete state change intended to exist in the world if the work succeeds. Every top-level directory represents exactly one outcome and is named after that outcome.

---

### **Directories**

Top-level directories must be named as outcomes, not tasks, tools, or abstractions. Names describe an achieved state, not an activity. If the outcome no longer matters, the entire directory can be archived without affecting others.

Each root directory answers one question only: _what is supposed to exist in the world if this succeeds_.

#### Examples (good directory names):

• Acquire First 100 Users  
• Enable CC Daily Autonomous Planning  
• Generate Weekly Business Insights  
• Reduce User Onboarding Friction  
• Launch Public CC Beta  
• Automate Personal Knowledge Capture

These names describe a **concrete outcome** or **state change**. If completed, the name would read as true.

A *state change name* encodes a before and after. [[CC]] can always tell whether the directory is “true” or “false.”

#### Counter-examples (bad directory names):

• Marketing  
• AI Agent  
• Planning System  
• Backend  
• Experiments  
• Prompts  
• Analytics Tools

These describe functions, components, or domains rather than outcomes. They do not imply completion or success and therefore fail as outcome roots.

---

### **Contents**

Everything inside an outcome directory exists solely to serve that outcome. If a file cannot clearly justify its contribution to the outcome named at the root, it does not belong there.

Code, prompts, data, experiments, notes, and automation live together because they share a single reason to exist.

There is no fixed internal directory structure. Internal structure is allowed to emerge organically and may differ between outcomes. Subdirectories are created only when repetition or scale makes them unavoidable.

[[Outcome-Aligned File Naming Convention|File naming]] is strict and carries meaning independently of location.

Files must remain understandable when viewed, copied, searched, or generated in isolation. Meaning must not rely on directory position.

---

Directory is fragile, file naming is robust.
Directories express  *groupings*, filenames express *identity* and *role*.

Identity survives change; grouping does not.

Structure is deferred, not denied. Patterns that consistently emerge across multiple outcomes may later be standardized, but never in advance.

This rule prioritizes intent clarity, mobility, and long-term coherence over premature order.