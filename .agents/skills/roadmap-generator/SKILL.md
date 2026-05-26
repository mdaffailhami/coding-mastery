---
name: roadmap-generator
description: Use after docs-discovery/doc-ingest when the user provides a project idea, target skill level, timeline, or asks for a learning roadmap; creates adaptive milestone-based plans, not fixed-duration plans.
---

# Roadmap Generator

## Objective
Synthesize the technical boundaries of the ingested documentation with the user's project concept, current skill level, and available time to produce an adaptive milestone learning path. Prefer mastery-based milestones over calendar weeks. Only map milestones to weeks when the user provides a time constraint.

## Instructions
1. Require or infer these inputs before planning:
   - Target technology/stack and ingested documentation snapshot path.
   - Project idea and intended user-facing outcome.
   - User skill level: beginner, intermediate, advanced, or unknown.
   - Time availability and target duration, if provided.
   - Desired depth: foundation, production-minded, or advanced internals.
2. If no timeline is provided, produce a milestone roadmap. If a timeline is provided, map milestones onto that schedule without forcing exactly 4 weeks.
3. Each milestone must introduce only 2-3 new core primitives from the ingested docs.
4. Enforce dependency order. Examples:
   - Project setup before routing conventions.
   - Routing/layouts before data-loading patterns.
   - Read flows before mutation flows.
   - Validation before persistence-critical mutations.
   - Auth/session boundaries before protected routes.
5. Include a Definition of Done for every milestone using observable behavior, not vague learning goals.
6. Include a checkpoint gate after each milestone that hands off to checkpoint-validator.
7. Do not generate implementation code during this phase.
8. If a project skeleton would help, recommend invoking project-scaffold after the first milestone is approved.

## Output Format
### Adaptive Learning Blueprint

- **Stack:** [Technology + version/snapshot]
- **Project:** [Project concept]
- **Mode:** [Milestone-based | Timeline-mapped]
- **Assumed Level:** [Beginner/Intermediate/Advanced/Unknown]
- **Docs Source:** [Local snapshot path or source summary]
- **Save Path:** `study/<project-slug>/roadmap.md`

| Milestone | Feature Objective | Core Tech Concepts | Definition of Done (DoD) | Checkpoint Gate |
| :--- | :--- | :--- | :--- | :--- |
| M1 | [Feature] | [Concept A, Concept B] | [Observable working state] | [What must be explained] |
| M2 | [Feature] | [Concept C, Concept D] | [Observable working state] | [What must be explained] |
| M3 | [Feature] | [Concept E, Concept F] | [Observable working state] | [What must be explained] |

### 🚀 First Milestone Execution Brief
Provide a strict execution brief for the first milestone. Outline files, concepts, constraints, and verification commands where appropriate, but omit implementation code.

### Scaffold Recommendation
State whether project-scaffold should be invoked now, later, or not at all, and why.
