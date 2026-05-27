---
name: progress-ledger
description: Use when starting, resuming, completing, or redirecting a learning track to read or update local progress, decisions, checkpoints, and next actions under study/.
---

# Progress Ledger

## Purpose

Maintain durable local learning state so sessions resume intelligently and the tutor does not repeat questions or forget decisions.

## Storage

Use local-only files under `study/<learning-slug>/`:

```text
study/<learning-slug>/
├── plan.md
├── progress.md
├── decisions.md
├── labs/
├── checkpoints/
└── notes/
```

Do not store secrets, credentials, private personal data, or unrelated project data.

## When to Read

- User resumes a track.
- User asks what is next.
- User claims completion.
- Agent needs active milestone/lab context.

## When to Write

- New track created.
- Learning contract changes.
- Lab assigned.
- Artifact reviewed.
- Mastery gate result changes.
- User reports durable confusion/breakthrough.

When a new track is created, ensure `plan.md` contains the canonical detailed plan itself, not a pointer to chat and not a separate sibling file.

## File Roles

- `plan.md`: canonical detailed learning contract, milestone sequence, sub-milestones, artifact gates, and current handoff.
- `progress.md`: current state first, then active lab, then reverse-chronological recent history. Keep the latest/current milestone at the top; do not append active labs in random/changelog order.
- `decisions.md`: why the path, emphasis, scope, or evidence standard changed.
- `checkpoints/<milestone>.md`: evidence, reasoning summary, decision.
- `notes/`: concise concept notes and recurring gotchas.

## `notes/` Policy

Treat `notes/` as the learner's curated notebook.

Write or update a note when any of these happen:

- the learner asks a durable conceptual question;
- the learner shows confusion about a distinction that will recur;
- an artifact review reveals a reusable gotcha;
- a concept becomes a prerequisite for later milestones;
- the tutor gives a mental model the learner should be able to revisit.

Prefer one focused note per concept. Keep notes short, learner-facing, and reusable. Do not write notes for every interaction, and do not store transient status in notes.

## `progress.md` Structure

Prefer this order:

```markdown
# [Track] Progress

## Current State

- **Current milestone:** ...
- **Completed milestones:** ...
- **Current blocker:** ...
- **Next driver action:** ...

## Active Lab: [latest/current]

[current lab only]

## Recent History

### [most recent completed]
### [older completed]
```

Do not keep multiple sections titled `Active Lab` for completed work. Move completed lab summaries to Recent History or checkpoint files.

## Output Format

### Progress Ledger Update

- **Track:** [slug]
- **Read:** [files]
- **Updated:** [files]
- **Current State:** [one line]
- **Next Driver Action:** [one action]
