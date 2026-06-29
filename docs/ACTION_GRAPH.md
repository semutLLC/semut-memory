# Action Graph

## Overview

Semut Memory represents history as an Action Graph.

Instead of organizing memory around individual entities, the Action Graph organizes memory around reusable actions and the actions that historically followed them.

Each meaningful action becomes a reusable memory node.

Each observed continuation becomes a branch.

The graph continuously grows as more traces are recorded.

---

# Why an Action Graph?

Traditional systems primarily answer:

> What is the current state?

Semut Memory instead asks:

> Given this action, what usually happened next?

This allows historical experience to be reused across different businesses, users, and domains.

---

# Action Node

Every meaningful completed action becomes an Action Node.

Examples:

* Quote Requested
* Quote Accepted
* Deposit Received
* Technician Assigned
* Job Completed
* Review Received
* Payment Failed

Action Nodes are reusable.

Thousands of independent entities may contribute to the same node.

---

# Branches

Every observed next action becomes a branch.

Example:

```text
Quote Accepted
        │
        ├── Schedule Visit
        ├── Request Deposit
        ├── Send Confirmation
        └── Cancel
```

Each branch stores historical observations rather than recommendations.

Possible metadata:

* occurrence count
* timestamps
* confidence
* witnesses
* context
* business category
* tags

---

# Continuous Expansion

Every destination becomes another Action Node.

```text
Schedule Visit
        │
        ├── Technician Assigned
        ├── Customer Rescheduled
        ├── Visit Cancelled
        └── Reminder Sent
```

The graph therefore grows naturally without requiring predefined workflows.

---

# Entity History

Although memory is stored as an Action Graph, individual histories remain reconstructable.

Example:

```text
Business A

Quote Requested

↓

Quote Accepted

↓

Schedule Visit

↓

Job Completed

↓

Review Received
```

Another business may follow:

```text
Business B

Quote Requested

↓

Quote Accepted

↓

Request Deposit

↓

Schedule Visit

↓

Job Completed
```

Both businesses contribute to the same Action Graph while maintaining separate historical timelines.

---

# Relationship to Knowledge

Memory stores observations.

Knowledge analyzes observations.

Memory answers:

* What happened?
* What happened next?
* How often?

Knowledge answers:

* Which branch is most successful?
* Which branch is fastest?
* Which branch is most reliable?
* Which branch should be recommended?

Knowledge never rewrites historical memory.

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
        ├── Ask for Referral
        └── Close Ticket
```

Knowledge may later determine that:

```text
Job Completed

↓

Request Review

↓

Repeat Customer
```

produces better long-term outcomes.

The recommendation belongs to Knowledge.

The observations remain in Memory.

---

# Design Principles

* Memory is action-centric rather than entity-centric.
* Every meaningful action becomes reusable.
* Branches represent observed continuations.
* History is append-only.
* Individual timelines are reconstructed from action paths.
* Knowledge is built by analyzing many action graphs.
* The graph continuously evolves as new traces are recorded.
