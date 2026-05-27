---
name: practice-builder
description: Use when a learner needs a concrete lab, coding drill, debugging exercise, prediction task, or optional scaffold that produces an artifact without solving the exercise for them.
---

# Practice Builder

## Purpose

Turn a milestone or concept into a doable practice block. This skill owns lab design and optional scaffold planning/creation.

Practice should be small enough to start now and real enough to review.

## Lab Rules

1. Start with a concise **Tiny Teach** section.
2. State the **Docs Boundary**.
3. Define exactly one primary artifact.
4. Give TODO-style tasks, not finished solutions.
5. Include prediction prompts before running/changing code.
6. Include verification: command, browser check, test, or observation.
7. Include checkpoint evidence to send back.
8. Keep normal labs to 15-60 minutes unless the user asks for a larger challenge.
9. For framework setup/API details, use `docs-grounding` first if not already grounded.
10. If files/folders would help, ask consent before creating them.

## Scaffold Boundaries

Allowed:

- directories;
- empty/near-empty files;
- TODO comments;
- README/LEARNING_TASKS;
- official generator commands;
- minimal boot placeholders.

Forbidden:

- finished business logic;
- full feature implementations;
- full auth/database systems;
- production-ready copy-paste solutions;
- framework trees invented against official setup guidance.

## Difficulty Ladder

1. Inspect generated files.
2. Modify one thing and observe.
3. Create one file/route/component/test.
4. Break/fix intentionally.
5. Compare two approaches.
6. Refactor while preserving behavior.
7. Combine primitives in a capstone slice.

## Output Format

### Practice Lab: [Concept/Milestone]

#### Tiny Teach

[3-8 sentence explanation or small ASCII diagram]

#### Docs Boundary

- [snapshot / Context7 source]

#### Artifact

[single concrete artifact]

#### Setup / Files

```text
[commands or file tree]
```

#### TODOs

1. [learner task]
2. [learner task]
3. [learner task]

#### Predictions

1. [what should happen?]
2. [what changes if...?]

#### Verification

- [command/check]

#### Send Back

- [artifact evidence]
- [observation]
- [short explanation]

#### Optional Stretch

[one stretch only]
