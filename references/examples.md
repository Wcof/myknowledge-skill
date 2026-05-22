# Examples

These examples are generic. Adapt names, domains, and paths to the user's knowledge base.

## Raw Meeting Transcript To Wiki Note

Raw source:

```text
raw/meetings/2026-05-22-product-review.txt
```

Wiki result:

```markdown
---
title: Product Review Meeting
domain: Work
scope: Product Project
topic: Review Meeting
primary_entry: Product review decisions
secondary_entries:
  - Meeting notes
  - Action items
status: current
date: 2026-05-22
objects:
  - Product Project
---

# Product Review Meeting

## Context

Short summary of why the meeting happened.

## Decisions

- Decision one.
- Decision two.

## Action Items

- [ ] Owner: prepare revised scope, due: 2026-05-29
```

## Topic Overview / MOC

```markdown
# Product Project

## What This Topic Covers

Planning, decisions, research, and delivery notes for the product project.

## Where To Find Things

- Current plan: [[Product Project Plan]]
- Meeting decisions: [[Product Review Meeting]]
- Research notes: [[Customer Interview Digest]]

## Current Important Pages

- [[Product Project Plan]] - current project direction
- [[Product Review Meeting]] - latest decisions and action items
```

## Metadata Example

```yaml
---
title: Reading Note Example
domain: Learning
scope: Books
topic: Reading Notes
primary_entry: Book insights
secondary_entries:
  - Source digest
  - Writing material
status: draft
date: 2026-05-22
objects:
  - Example Book
---
```

## Action Items

```markdown
- [ ] Owner: draft project outline, due: 2026-05-25
- [ ] 负责人：整理会议结论，截止：2026-05-26
```

## Governance Log Entry

```markdown
## 2026-05-22

- Initialized knowledge base with `raw/`, `wiki/`, and `system/`.
- Added first topic overview for `Product Project`.
- Open issue: several imported notes still need metadata review.
```
