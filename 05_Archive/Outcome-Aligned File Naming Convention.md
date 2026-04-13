---
ai-assist:
  - https://chatgpt.com/c/69905c90-15fc-83a0-bf20-f11dbfbb98a7
---

A file name exists to state **why the file must exist** for its outcome to become true.

If the name does not answer that, the file is incorrectly named.

A file name should answer one question only: **what role does this file play in making the [[Outcome-Driven Directory Structure|outcome]] true**.

---

### **Core structure**

`<intent>__<role>[__<scope>].<ext>`

• `intent` describes the state change the file causes  
• `role` explains the function the file serves  
• `scope` is optional and only used to clarify boundaries  
• the extension is purely technical and ignored conceptually

Double underscores separate meaning, not hierarchy.

---

###  **1) Intent rule**

Intent is written as a verb phrase that moves the outcome forward.

Use verbs that imply change or enforcement, not activity.

If the file does not clearly push the outcome toward “true,” it does not belong.

Correct:  
`define`, `decide`, `enforce`, `ensure`, `measure`, `validate`, `trigger`

Incorrect:  
`write`, `build`, `test`, `draft`

Example:  
`decide__task_prioritization.md`

---

### **2) Role rule**

The role states _what the file does_, not what it contains or how it is implemented.

Ask: “What would stop working if this file disappeared?”

Correct roles:  
`criteria`, `policy`, `signal`, `memory`, `contract`, `evaluator`, `schedule`

Incorrect roles:  
`notes`, `utils`, `script`, `final`, `v2`

Example:  
`enforce__planning_constraints.yaml`

---

### **3) One reason to exist**

Each file serves exactly one reason for the outcome.

If a file exists for multiple reasons, it must be split.

Correct:  
`measure__execution_signal.py`

Incorrect:  
`planning_and_execution.py`

---

### **4) Outcome-bound rule**

If the outcome is true, the file should still matter.

Process artifacts do not belong.

Correct:  
`ensure__context_continuity.memory`

Incorrect:  
`early_ideas.md`, `experiment_3.py`

---

### **5) Scope rule (optional)**

Scope is used only to distinguish meaning, never time, order, or version.

Correct:  
`enforce__constraints__daily.yaml`  
`enforce__constraints__long_term.yaml`

Incorrect:  
`constraints_final.yaml`, `constraints_2026.yaml`

---

### **6) Special rule for prompts**

Files whose primary function is to be consumed as prompts MUST end with `__prompt`, regardless of extension.

This suffix is semantic, not technical.

Prompt files follow:

`<intent>__<role>[__<scope>]__prompt.<ext>`

Examples:  
`decide__task_prioritization__prompt.md`  
`generate__daily_plan__prompt.txt`  
`evaluate__plan_quality__prompt.md`

Non-prompt files must not use this suffix.

---

### **7) Self-legibility requirement**

The filesystem must explain the system without external context.

A reader should infer the logic of the outcome by reading file names alone.

Correct set:  
`define__success_criteria.md`  
`decide__task_prioritization__prompt.md`  
`enforce__planning_constraints.yaml`  
`measure__execution_signal.py`  
`validate__plan_coherence.py`

Incorrect set:  
`notes.md`  
`utils.py`  
`script_v4.py`

---

### **Examples**

Examples within an outcome like “CC Autonomous Daily Planning”:

• `define__success_criteria.md`  
• `enforce__planning_constraints.yaml`  
• `decide__task_prioritization__prompt.md`  
• `measure__plan_execution_signal.py`  
• `ensure__context_continuity.memory`  
• `validate__daily_plan_coherence.py`  
• `trigger__planning_cycle.schedule`

None of these names care how they are implemented. Only why they exist.

---

This turns the filesystem into a truth table for CC’s progress, where [[Outcome-Driven Directory Structure#Directories|directories]] assert _what should exist_, and files assert _why each piece exists_.