# Semut Memory Algorithm

## Overview

Semut Memory transforms raw traces into persistent memory.

Unlike traditional storage systems that periodically save complete snapshots, Semut Memory stores only meaningful state transitions. Every stored transition becomes a branch that can later be reconstructed, analyzed, or reused.

The goal is not to preserve every event, but to preserve the minimum information necessary to reconstruct meaningful history.

---

# Core Concepts

## Root

Every entity begins with a root state.

Examples:

* A business profile
* A Git repository
* A customer profile
* A conversation
* A digital assistant

The root acts as the anchor for all future memory.

```
Root
```

---

## Trace

Every interaction produces traces.

Examples:

* Customer submitted a request
* AI generated a draft
* Employee completed a task
* Sensor produced a reading

Most traces are temporary.

---

## Semantic Delta

Incoming traces are compared against the current reconstructed state.

The system estimates whether the trace creates a meaningful state transition.

Examples:

* Customer accepted a quote
* Business changed operating hours
* Employee joined the company
* AI received new long-term instructions

Minor or reversible events are typically discarded.

---

## Witness

Before becoming permanent memory, a semantic delta should be verified.

Possible witnesses include:

* Human confirmation
* Multiple AI agreement
* Digital signature
* Successful transaction
* Trusted sensor

The witness mechanism improves trust and reduces noise.

---

## Branch

A verified semantic delta becomes a branch.

```
Root
 │
 ├── Branch 1
 ├── Branch 2
 └── Branch 3
```

Each branch represents an irreversible or significant change in history.

---

## Reconstruction

Current state is reconstructed by applying branches to the root.

```
Current State

=
Root
+ Branch 1
+ Branch 2
+ Branch 3
```

AI does not need every intermediate event.

It only needs the root and the meaningful branches.

---

## Compression

Branches may be compressed.

Examples:

* Merge repeated identical updates
* Aggregate repetitive sensor readings
* Replace thousands of temporary edits with one confirmed outcome

Compression should never destroy reconstructable history.

---

## Recombination

Stored branches remain reusable.

Branches may be:

* replayed
* forked
* merged
* compared
* simulated

This allows AI to explore alternative futures without modifying historical memory.

---

# Algorithm

```
Incoming Trace
        │
        ▼
Reconstruct Current State
        │
        ▼
Compute Semantic Delta
        │
        ▼
Significant?
        │
   ┌────┴────┐
   │         │
 No          Yes
   │         │
Discard   Verify Witness
              │
              ▼
      Create Branch
              │
              ▼
 Compress + Store Metadata
              │
              ▼
 Available for Reconstruction
```

---

# Example

Restaurant:

```
Root
Hours: 9–5
Menu: Version 1
Employees: 3
```

Customer places an order.

No permanent state change.

Discard.

Owner changes hours.

```
Branch A

Hours:
9–5

↓

10–8
```

Store.

Owner hires a new employee.

```
Branch B

Employees:
+1
```

Store.

Current restaurant state becomes:

```
Root
+ Branch A
+ Branch B
```

---

# Relationship to Semut

Semut Layer Model describes **what emerges**:

Trace → Memory → Knowledge → Norm → Institution

Semut Memory defines **how the Memory layer operates**.

It determines which traces become durable memory through semantic state transitions, branching, reconstruction, and recombination.
