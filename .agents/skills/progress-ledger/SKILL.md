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

When a new track is created, ensure `plan.md` contains the canonical plan itself, not a pointer to chat.

## File Roles

- `progress.md`: current milestone, completed milestones, blocker, next driver action.
- `decisions.md`: why the path, emphasis, scope, or evidence standard changed.
- `checkpoints/<milestone>.md`: evidence, reasoning summary, decision.
- `notes/`: concise concept notes and recurring gotchas.

## Output Format

### Progress Ledger Update

- **Track:** [slug]
- **Read:** [files]
- **Updated:** [files]
- **Current State:** [one line]
- **Next Driver Action:** [one action]
