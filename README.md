# Coding Mastery

An agentic learning workspace for mastering technologies with AI agents as tutor, coach, reviewer, and practice designer.

Core loop:

```text
understand intention
→ ground in official sources
→ teach
→ practice
→ review/debug
→ validate mastery
→ record progress
→ next challenge
```

## What This Repo Contains

```text
AGENTS.md                 # Dev Tutor instructions
opencode.json             # opencode project configuration
.agents/skills/           # learning workflow skills
package.json              # Context7 helper scripts and dependencies
```

This repository is the reusable learning system, not a single application project.

## Setup

Install dependencies:

```bash
npm install
```

> For higher Context7 limits, copy `.env.example` to `.env` and set `CONTEXT7_API_KEY` with your Context7 API key from the [context7.com](https://context7.com).

## Learning Skill Architecture

The workspace uses seven learning skills:

| Skill | Responsibility |
| --- | --- |
| `learning-director` | Control plane for intention, routing, and next action. |
| `docs-grounding` | Official docs/current API lookup and rule extraction. |
| `curriculum-planner` | Adaptive capability paths. |
| `practice-builder` | Concrete labs, drills, and optional scaffolds. |
| `artifact-coach` | Code/error/output review as teaching. |
| `mastery-gate` | Artifact + reasoning validation before moving on. |
| `progress-ledger` | Local study progress and decisions under `study/`. |

Default workflow:

```text
learning-director
  ↓
progress-ledger        # if resuming or updating state
  ↓
docs-grounding         # for framework/library specifics
  ↓
curriculum-planner     # when a path is needed
  ↓
practice-builder       # always produces the next concrete practice block
  ↓
user implementation
  ↓
artifact-coach
  ↓
mastery-gate
  ↓
progress-ledger
```

## Learning Philosophy

State your intention:

- “I want to learn SvelteKit from scratch.”
- “I want to deeply understand databases.”
- “I want to build a finance tracker while learning.”
- “I want to become interview-ready for React.”
- “Review this code and teach me what I missed.”

The agent adapts depth, pace, artifact size, project relevance, and review strictness from your goal and latest evidence. These are adjustments, not fixed tracks.

Programming milestones should produce artifacts: runnable code, tests, route trees, debug traces, CLI/browser output, refactors, or diagrams tied to runtime behavior. Checkpoint questions validate practice; they are not the lesson.

## Local-Only Folders

Generated learning outputs are intentionally ignored by Git:

```text
.docs/  # official/current docs snapshots
study/  # learner plans, progress, labs, checkpoints, practice projects
```

Recommended local study layout:

```text
study/<learning-slug>/
├── plan.md
├── progress.md
├── decisions.md
├── labs/
├── checkpoints/
└── project/
```

## Example Prompts

```text
I want to learn SvelteKit from the beginning.
Use official docs, teach me, give me tiny coding labs, review my work, and checkpoint me before moving on.
```

```text
I want to learn SvelteKit by building a personal finance tracker.
Use official docs and keep me in the driver's seat.
```

```text
I'm stuck on this error. Review it as a tutor and give me the next action, not the full solution.
```
