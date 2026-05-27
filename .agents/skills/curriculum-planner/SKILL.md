---
name: curriculum-planner
description: Use after docs grounding when the user needs an adaptive learning path, mastery sequence, capability map, or project-shaped progression with artifact-based gates.
---

# Curriculum Planner

## Purpose

Design the learning path. Convert the user's intention and docs-grounded primitives into a sequence of capability milestones.

A curriculum is not a calendar dump. It is a dependency-aware path from current ability to target capability.

## Inputs

- User goal/intention.
- Starting level or assumption.
- Docs-grounded rules and primitives.
- Desired artifact direction: tiny labs, project, interview drills, production readiness, etc.
- Time constraints only if the user provides them.

## Planning Rules

1. Prefer milestones over weeks unless the user gives a timeline.
2. Each milestone introduces only 2-3 new primitives.
3. Each milestone has a concrete practice artifact.
4. Programming milestones must not be question-only.
5. First or second milestone for app/framework learning should involve a real starter project, file inspection, or runnable tiny app.
6. Dependency order matters: setup/structure → routing/composition → data read → mutation → integration → security/runtime → capstone.
7. Every milestone includes a checkpoint standard tied to artifact evidence.
8. Hand off the current milestone to `practice-builder`; do not leave the user with only a table.
9. For durable learning tracks, the full detailed plan belongs in `study/<learning-slug>/plan.md`.
10. Prefer readable sectioned milestones over dense table-only plans. A summary table is optional; the canonical plan should include milestone sections with capability, primitives, artifact, and gate.
11. Chat output should be a concise summary: created/updated file paths, active milestone, and next driver action. Do not paste the full milestone plan in chat unless the user asks to preview it.

## Output Format

### File Output

Write the canonical curriculum to:

```text
study/<learning-slug>/plan.md
```

The file must include the full detailed milestone sequence and current milestone handoff. Avoid making the table the only source of detail.

### Chat Output

Keep chat brief:

- **Updated:** `study/<learning-slug>/plan.md`
- **Active:** [current milestone]
- **Next:** [one driver action]

Only include the full table in chat if the user explicitly asks for it.

### Adaptive Curriculum: [Track]

- **Goal:** [intention]
- **Tutoring Emphasis:** [depth, pace, artifact type, review strictness]
- **Docs Source:** [snapshot/Context7]
- **Artifact Strategy:** [tiny labs / project / mixed]
- **Schedule:** [milestone-based or timeline-mapped]

#### M1 — [Name]

- **Capability:** [capability]
- **Primitives:** [2-3 new primitives]
- **Practice artifact:** [artifact]
- **Done means:** [observable result]
- **Gate:** [reasoning standard]

Sub-milestones may be used when a concept naturally splits into smaller gates, e.g. M3a native forms, M3b named actions, M3c validation.

### Current Milestone Handoff

- **Milestone:** [Mx]
- **Why now:** [dependency reason]
- **Practice-builder brief:** [what lab should be created next]
