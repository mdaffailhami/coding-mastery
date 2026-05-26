---
name: project-scaffold
description: Use after roadmap-generator when a learning project needs a starter folder/file skeleton; creates minimal TODO-based scaffolds for the current milestone without solving implementation code for the user.
---

# Project Scaffold

## Objective
Create a minimal, documentation-aligned project skeleton that helps the user start a milestone while keeping them in the driver's seat. The scaffold should establish structure, placeholders, TODOs, learning prompts, and verification commands; it must not implement finished features.

## Boundaries
Allowed:
- Directory structure.
- Empty or near-empty files.
- TODO comments.
- README/LEARNING_TASKS instructions.
- Configuration files only when required by official docs or the selected toolchain.
- Minimal placeholder content needed to prove the project boots.

Forbidden:
- Complete business logic.
- Finished UI components.
- Full database schemas beyond milestone placeholders.
- Full auth/session implementation.
- Copy-pasteable production solutions.
- Hidden complexity that the learner cannot explain.

## Inputs Required
Before scaffolding, require:

1. Active docs snapshot path from docs-discovery/doc-ingest.
2. Active roadmap milestone.
3. Project name and target directory.
4. Package manager/runtime preference when relevant.
5. Whether the user wants the agent to actually create files or only print a proposed tree.

## Scaffolding Strategy
1. Start from the official setup command or file conventions in the docs snapshot.
2. Create only the files needed for the current milestone plus obvious project-level docs.
   - Default target for learner-owned projects: `study/<project-slug>/project/`.
   - Default target for learner notes/checkpoints: `study/<project-slug>/`.
   - Do not place learner-specific projects at the repository root unless the user explicitly requests it.
3. Add `LEARNING_TASKS.md` with:
   - Milestone objective.
   - Concepts to practice.
   - TODO checklist.
   - Definition of Done.
   - Reflection questions.
4. Add comments that ask questions instead of giving answers.
5. Keep generated files intentionally incomplete.
6. Provide verification commands from official docs where possible.

## Recommended Files
For every scaffold, prefer adding:

```text
README.md
LEARNING_TASKS.md
```

For app/framework projects, add only framework-required structure for the active milestone.

## Output Format

### Scaffold Plan: [Project Name]

- **Target Directory:** [path]
- **Stack:** [technology]
- **Milestone:** [milestone]
- **Docs Boundary:** [snapshot path]

### Proposed File Tree
```text
[tree]
```

### What I Will Create
- [file/folder + purpose]

### What You Must Implement Yourself
- [learning task]
- [learning task]
- [learning task]

### Verification
- [command or manual check]

### Consent Gate
Ask the user to approve file creation before writing files unless they already gave explicit permission.
