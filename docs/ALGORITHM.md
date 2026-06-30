# Semut Memory Algorithm

## Overview

Semut Memory transforms traces into reusable coordination memory.

The system separates two kinds of memory:

1. **Action Memory** — records meaningful action transitions for coordination.
2. **Artifact Memory** — preserves documents, code, images, conversations, and other artifacts efficiently.

Action Memory answers:

> What happened next?

Artifact Memory answers:

> How can the original artifact be reconstructed?

---

# Architecture

```text
                 Incoming Trace
                        │
        ┌───────────────┴───────────────┐
        │                               │
        ▼                               ▼
 Action Instance                 Artifact Update
        │                               │
        ▼                               ▼
   Action Graph                 Root + Delta Storage
        │                               │
        └───────────────┬───────────────┘
                        ▼
                  Knowledge Layer
                        ▼
               Recommended Actions
                        ▼
                      AI Agent
                         │
                "How do we do it?"
                         │
                         ▼
                  Execution Graph
                         │
                         ▼
                Tools / APIs / Browser
```

---

# Processing Pipeline

## Step 1 — Receive Trace

Incoming traces may originate from:

* humans
* AI agents
* businesses
* sensors
* external systems

Example:

Customer accepted quote.

---

## Step 2 — Create Action Instance

Create an immutable record describing:

* action
* timestamp
* optional actor
* optional entity
* related artifacts

Example:

Customer Accepted Quote

---

## Step 3 — Update Action Graph

Locate the Action Node.

If it does not exist:

Create it.

Observe the next action.

Create or update the transition.

Example:

Customer Accepted Quote

↓

Schedule Visit

---

## Step 4 — Update Artifact Memory

If the trace modifies an artifact:

* locate artifact root
* compute delta
* store delta
* preserve reconstruction history

Artifacts are stored independently from the Action Graph.

---

## Step 5 — Expose Memory

Semut Memory exposes:

* action transitions
* artifact references

Knowledge consumes these memories to discover reusable patterns.

---

# Responsibilities

## Action Memory

Responsible for:

* action transitions
* coordination history
* reconstructing action sequences

## Artifact Memory

Responsible for:

* artifact preservation
* version history
* reconstruction
* efficient storage

## Knowledge

Responsible for:

* discovering patterns
* recommending next actions
* extracting reusable workflows

Knowledge never modifies historical memory.
