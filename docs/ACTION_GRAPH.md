# Action Graph

## Overview

The Action Graph is the primary coordination memory of Semut.

Instead of organizing memory around documents or entities, Semut organizes memory around meaningful actions and the actions that historically followed them.

Artifacts are stored separately.

The Action Graph stores only coordination history.

---

# Action Nodes

Every meaningful completed action becomes an Action Node.

Examples:

* Quote Requested
* Quote Accepted
* Job Scheduled
* Job Completed
* Review Received
* Payment Failed

Action Nodes are reusable across all entities.

---

# Action Transitions

Observed continuations become transitions.

Example:

```text 
Quote Accepted
│
├── Schedule Visit
├── Request Deposit
├── Send Confirmation
└── Cancel
```

The graph grows continuously as new traces arrive.

---

# Action Instances

Every observation creates an Action Instance.

Example:

Action:
Job Completed

Metadata:

* timestamp
* business
* customer
* artifact references
* confidence

Action Instances contribute to the shared Action Graph.

---

# Artifact References

The Action Graph does not duplicate artifacts.

Instead, Action Instances reference them.

Example:

Action:

Quote Sent

Artifacts:

* quote.pdf
* email thread
* images
* notes

Artifact storage is handled by Semut Artifact Memory.

---

# Entity Histories

Individual histories are reconstructed by following Action Instances.

Business A:

Quote Requested

↓

Quote Accepted

↓

Schedule Visit

↓

Job Completed

↓

Review Received

Multiple businesses contribute to the same shared Action Graph while preserving separate histories.

---

# Relationship to Knowledge

Memory records observed transitions.

Knowledge analyzes the graph to discover:

* common continuations
* successful workflows
* recurring coordination patterns
* recommended next actions

The Action Graph remains an objective historical record.

Recommendations belong to the Knowledge layer.
