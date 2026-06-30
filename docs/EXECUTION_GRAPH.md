# Execution Graph

## Overview

The Human Action Graph determines **what should happen next**.

The Execution Graph determines **how to accomplish that action** using the available tools, APIs, software, or devices.

Unlike the Human Action Graph, the Execution Graph is implementation-specific and may change as software platforms evolve.

---

# Separation of Responsibilities

Semut separates coordination from execution.

```text
Trace
    │
    ▼
Human Action Graph
    │
"What should happen?"
    ▼
AI Agent
    │
"How can this be accomplished?"
    ▼
Execution Graph
    │
    ▼
Tools / APIs / Applications
```

This separation allows coordination knowledge to remain stable while execution methods continue to evolve.

---

# Human Action Graph

Example:

```text
Customer Accepted Quote
        │
        ▼
Schedule Visit
```

This graph represents coordination.

It is independent of any software implementation.

---

# Execution Graph

The selected action is translated into executable steps.

Example:

```text
Schedule Visit
        │
        ├── Open Calendar
        ├── Find Available Time
        ├── Create Event
        ├── Notify Customer
        └── Record Confirmation
```

These steps are implementation details rather than business coordination.

---

# AI Agent

The AI Agent acts as the translator between coordination and execution.

Responsibilities include:

* interpreting the selected action
* selecting available tools
* generating execution plans
* calling APIs
* generating code when necessary
* observing execution results

The AI Agent may use:

* existing APIs
* browser automation
* desktop automation
* robotics
* dynamically generated code
* reusable execution templates

The Human Action Graph remains unchanged regardless of the execution method.

---

# Execution Learning

Execution methods may improve over time.

Example:

Initial execution:

```text
Open Browser

↓

Navigate to Calendar

↓

Create Event
```

Later:

```text
Call Calendar API

↓

Create Event
```

Or:

```text
Use Local Calendar SDK
```

Multiple execution methods may exist for the same coordination action.

---

# Relationship to Artifact Memory

Execution may create or modify artifacts.

Example:

Action:

```text
Send Invoice
```

Artifacts:

* invoice.pdf
* email thread
* payment record

Artifact Memory preserves these artifacts independently from execution.

---

# Relationship to Action Memory

Action Memory determines:

> What should happen next?

Execution Graph determines:

> How is the selected action accomplished?

Both layers are independent.

---

# Design Principles

* Separate coordination from execution.
* Keep business logic independent from software implementations.
* Allow multiple execution methods for the same action.
* Support AI-generated execution plans.
* Support reusable execution templates.
* Permit execution strategies to evolve without modifying the Human Action Graph.

---

# Future Directions

As AI systems become more capable, execution may become increasingly dynamic.

Rather than requiring manually written integrations for every application, AI agents may generate execution plans at runtime while learning successful execution strategies over time.

Semut does not require a single execution mechanism.

Its responsibility is to preserve coordination knowledge while enabling flexible execution through AI and external tools.
