---
name: mastery-gate
description: Use when the user claims a lab/milestone is complete or asks to move on; validates artifact evidence plus reasoning before unlocking the next challenge.
---

# Mastery Gate

## Purpose

Decide whether the learner is ready to move on. This is a promotion gate, not an oral exam.

## Required Evidence

Ask for the smallest missing evidence if absent:

- files changed or route tree;
- command/test/browser output;
- screenshot or observed behavior;
- short explanation of what they built and why it works.

## Validation Rules

1. Check the artifact against the milestone Definition of Done.
2. Ask 1-3 reasoning questions tied to the artifact, not broad trivia.
3. Do not ask about concepts not taught/practiced in the current boundary.
4. If weak, assign a smaller targeted lab through `practice-builder`.
5. If strong, unlock and send the next milestone to `practice-builder`.
6. Record the outcome through `progress-ledger` when a study track exists.

## Output Format

### Mastery Gate: [Milestone]

- **Artifact Evidence:** [reviewed/missing]
- **DoD Status:** [met / partial / not yet]
- **Docs Boundary:** [source]

### Reasoning Check

1. [artifact-tied question]
2. [optional]
3. [optional]

### Decision

- **Status:** [unlocked / needs tiny fix / locked]
- **Reason:** [brief]

### Next Action

- If unlocked: [next lab handoff]
- If locked: [targeted micro-lab]
