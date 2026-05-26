---
name: roadmap-generator
description: Use after docs-discovery/doc-ingest when the user asks for a Foundation Mode or Project Mode learning roadmap; creates adaptive milestone-based plans, not fixed-duration plans.
---

# Roadmap Generator

## Objective
Synthesize the technical boundaries of the ingested documentation with the user's chosen learning mode, current skill level, and available time to produce an adaptive milestone learning path. Support exactly two modes: Foundation Mode and Project Mode. Prefer mastery-based milestones over calendar weeks. Only map milestones to weeks when the user provides a time constraint.

## Instructions
1. Require or infer these inputs before planning:
   - Target technology/stack and ingested documentation snapshot path.
   - Learning mode: Foundation Mode or Project Mode.
   - Project idea and intended user-facing outcome, required only for Project Mode.
   - User skill level: beginner, intermediate, advanced, or unknown.
   - Time availability and target duration, if provided.
   - Desired depth: foundation, production-minded, or advanced internals.
2. If no timeline is provided, produce a milestone roadmap. If a timeline is provided, map milestones onto that schedule without forcing exactly 4 weeks.
3. In Foundation Mode, milestones should build a conceptual map from fundamentals to practical tiny drills. Do not require a large app idea.
4. In Project Mode, milestones should map project features to the framework concepts needed to build them.
5. Each milestone must introduce only 2-3 new core primitives from the ingested docs.
6. Enforce dependency order. Examples:
   - Project setup before routing conventions.
   - Routing/layouts before data-loading patterns.
   - Read flows before mutation flows.
   - Validation before persistence-critical mutations.
   - Auth/session boundaries before protected routes.
7. Include a Definition of Done for every milestone using observable behavior, not vague learning goals.
8. Include a checkpoint gate after each milestone that hands off to checkpoint-validator.
9. Do not generate implementation code during this phase.
10. Recommend project-scaffold only for Project Mode, or for Foundation Mode tiny-drill folders when the user explicitly wants files.

## Output Format
### Adaptive Learning Blueprint

- **Stack:** [Technology + version/snapshot]
- **Learning Mode:** [Foundation Mode | Project Mode]
- **Project:** [Project concept or none for Foundation Mode]
- **Schedule Mode:** [Milestone-based | Timeline-mapped]
- **Assumed Level:** [Beginner/Intermediate/Advanced/Unknown]
- **Docs Source:** [Local snapshot path or source summary]
- **Save Path:** `study/<project-slug>/roadmap.md`

| Milestone | Learning/Feature Objective | Core Tech Concepts | Definition of Done (DoD) | Checkpoint Gate |
| :--- | :--- | :--- | :--- | :--- |
| M1 | [Feature] | [Concept A, Concept B] | [Observable working state] | [What must be explained] |
| M2 | [Feature] | [Concept C, Concept D] | [Observable working state] | [What must be explained] |
| M3 | [Feature] | [Concept E, Concept F] | [Observable working state] | [What must be explained] |

### 🚀 First Milestone Execution Brief
Provide a strict execution brief for the first milestone. Outline files, concepts, constraints, and verification commands where appropriate, but omit implementation code.

### Scaffold Recommendation
State whether project-scaffold should be invoked now, later, or not at all, and why. In Foundation Mode, default to no scaffold unless tiny-drill files would help. In Project Mode, recommend scaffolding when starter structure reduces setup friction without solving the feature.
