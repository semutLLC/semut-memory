# Semut Memory Algorithm

## Overview

Semut Memory preserves reusable action history.

Instead of organizing memory around individual entities, Semut Memory organizes memory around meaningful actions and the actions that historically followed them.

Every completed action becomes a reusable memory node.

Every observed continuation becomes a branch.

The result is a continuously growing graph of historical coordination.

---

# Core Concept

Traditional systems ask:

> What is the current state?

Semut Memory asks:

> Given this action, what actions historically followed?

Every meaningful action becomes a reusable memory node.

```text
Action Node

Customer Accepted Quote
```

Historical continuations become branches.

```text
Customer Accepted Quote
        │
        ├── Schedule Visit
        ├── Request Deposit
        ├── Send Confirmation
        └── Cancel
```

The graph grows naturally as more traces are observed.

---

# Processing Pipeline

## 1. Receive Trace

Incoming traces arrive from:

* humans
* AI agents
* businesses
* sensors
* software systems

Example:

```text
Customer accepted quote.
```

---

## 2. Locate Action Node

Find the corresponding action node.

If none exists:

Create a new node.

```text
Customer Accepted Quote
```

---

## 3. Observe Next Action

Observe what happened next.

Example:

```text
Customer Accepted Quote

↓

Schedule Visit
```

---

## 4. Create or Update Branch

Create the branch if it does not exist.

Otherwise update its history.

```text
Customer Accepted Quote
        │
        ├── Schedule Visit
        ├── Request Deposit
        └── Cancel
```

Each branch stores metadata such as:

* occurrence count
* timestamps
* confidence
* witnesses
* context
* tags

---

## 5. Continue

Every next action becomes another action node.

```text
Schedule Visit
        │
        ├── Technician Assigned
        ├── Customer Rescheduled
        └── Visit Cancelled
```

The graph continuously expands.

---

# Reconstruction

An entity's history can be reconstructed by following its sequence of action nodes.

Example:

```text
Quote Requested
        │
Accepted Quote
        │
Schedule Visit
        │
Job Completed
        │
Review Received
```

Semut Memory therefore stores reusable coordination rather than isolated timelines.

---

# Relationship to Knowledge

Memory does not determine which path is best.

Memory only records observed continuations.

Knowledge analyzes many action graphs to answer questions such as:

* Which branch occurs most often?
* Which branch produces better outcomes?
* Which branch is faster?
* Which branch is more reliable?
* Which branch should be recommended?

Knowledge transforms historical memory into reusable guidance.

---

# Example

Action Node

```text
Job Completed
```

Historical branches

```text
Job Completed
        │
        ├── Send Invoice
        ├── Request Review
        ├── Schedule Follow-up
        ├── Close Ticket
        └── Ask for Referral
```

Memory records every observed continuation.

Knowledge later discovers that:

```text
Job Completed

↓

Request Review

↓

Repeat Customer
```

occurs significantly more often than alternative paths.

The recommendation belongs to Knowledge.

The history belongs to Memory.

---

# Design Principles

* Every meaningful action becomes a reusable memory node.
* Every observed continuation becomes a branch.
* Memory is append-only.
* Memory stores history, not recommendations.
* Current state is reconstructed by following action paths.
* Knowledge analyzes memory but does not modify historical memory.
* New traces continuously expand the graph.
