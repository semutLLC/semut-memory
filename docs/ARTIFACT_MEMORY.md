# Artifact Memory

## Overview

Artifact Memory preserves the content created during coordination.

Unlike the Action Graph, which records meaningful action transitions, Artifact Memory stores the underlying artifacts such as:

* documents
* source code
* emails
* images
* conversations
* configuration files
* datasets

Its primary goal is efficient preservation and reconstruction rather than coordination.

---

# Relationship to Semut Memory

Semut Memory consists of two complementary subsystems.

```text
Trace
   │
   ├── Action Memory
   │      │
   │      └── Action Graph
   │
   └── Artifact Memory
          │
          └── Root + Delta Storage
```

Action Memory answers:

> What happened next?

Artifact Memory answers:

> What exactly changed?

---

# Root Artifact

Every artifact begins with a Root.

Examples:

* Initial document
* Initial source code
* First image
* Original contract

```text
Root Artifact
```

The Root acts as the reconstruction anchor.

---

# Artifact Delta

Subsequent changes are stored as deltas.

Example:

```text
Proposal.md

Root
```

Revision:

```text
Δ1

Added pricing section
```

Revision:

```text
Δ2

Corrected customer name
```

Revision:

```text
Δ3

Inserted company logo
```

Current artifact becomes:

```text
Root

+

Δ1

+

Δ2

+

Δ3
```

---

# Reconstruction

Any version may be reconstructed by replaying deltas from the Root.

Example:

```text
Version 3

=

Root

+

Δ1

+

Δ2

+

Δ3
```

No duplicate copies are required.

---

# Compression

Artifact Memory may optimize storage by:

* merging repetitive changes
* compressing identical regions
* removing redundant intermediate states
* grouping small edits

Compression must never prevent reconstruction.

---

# Significance

Not every artifact modification must become a permanent revision.

Possible heuristics include:

* user save
* user approval
* completed transaction
* information gain
* semantic importance
* configurable thresholds

The exact policy depends on the application.

---

# Relationship to Action Memory

Example:

Action:

```text
Quote Sent
```

Artifact:

```text
quote.pdf
```

The Action Graph records:

```text
Quote Sent

↓

Customer Accepted
```

Artifact Memory records:

```text
Root Quote

+

Pricing Update

+

Signature Added

+

Final Version
```

Both memories reference each other while serving different purposes.

---

# Design Principles

* Preserve artifacts independently from coordination.
* Store roots and meaningful revisions.
* Support efficient reconstruction.
* Optimize storage without losing history.
* Action Memory references artifacts but does not duplicate them.
* Artifact Memory does not determine workflow or recommendations.

---

# Relationship to Knowledge

Artifact Memory preserves content.

Action Memory preserves coordination.

Knowledge analyzes both.

Artifacts provide detailed context.

Action Graphs provide historical transitions.

Together they enable AI systems to understand both *what was created* and *how work progressed*.
