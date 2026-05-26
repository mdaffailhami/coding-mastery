# Coding Mastery

An Agentic-powered learning workspace for mastering technologies through official documentation, adaptive roadmaps, Socratic review, and milestone checkpoints.

## What This Repo Contains

```text
AGENTS.md                 # AI Agent instructions
opencode.json             # OpenCode project configuration
.agents/skills/           # Reusable learning workflow skills
package.json              # Project metadata and dependencies
```

This repository is the reusable **learning workflow**, not a single application project.

## Setup

Install project dependencies:

```bash
npm install
```

This installs the local tooling used by the workflow, including:

- `ctx7` for Context7 documentation lookup.
- `dotenv-cli` for safely loading `.env` before running Context7 commands.

## Learning Workflow

Choose one mode for each learning track:

- **Foundation Mode:** learn the technology from first principles through concept maps, tiny drills, and checkpoints.
- **Project Mode:** learn by building a real project where each milestone introduces the concepts needed for the next feature.

```text
learning idea
  ↓
docs-discovery
  ↓
doc-ingest
  ↓
roadmap-generator
  ↓
project-scaffold, optional in Project Mode
  ↓
your implementation
  ↓
socratic-review
  ↓
checkpoint-validator
  ↓
next milestone
```

## Local-Only Folders

Generated study artifacts are intentionally ignored by Git:

```text
.docs/  # cached official documentation snapshots
study/  # learner-specific roadmaps, notes, checkpoints, and practice projects
```

Recommended local study layout:

```text
study/<project-slug>/
├── roadmap.md
├── checkpoints/
├── notes/
└── project/
```

This keeps the GitHub repository clean while allowing every cloner to learn their own stack locally.

## Context7 Setup

One of the Docs Discovery methods is using the Context7 CLI. For repeatable local usage, store the API key in `.env` and run Context7 through the provided npm scripts, which load `.env` with `dotenv-cli`.

Create a local `.env` file:

```bash
cp .env.example .env
```

Then fill in:

```dotenv
CONTEXT7_API_KEY=your_context7_api_key_here
```

**IMPORTANT**: Do not commit `.env`.

OAuth is acceptable for personal machines:

```bash
npx ctx7 login
```

But `.env` + `CONTEXT7_API_KEY` + `dotenv-cli` is the recommended project convention.

## Example Prompt

Foundation Mode:

```text
I want to learn SvelteKit from the beginning.
Use official docs and create a foundation roadmap with tiny drills.
```

Project Mode:

```text
I want to learn SvelteKit by building a personal finance tracker.
Use official docs, create a milestone roadmap, and scaffold only the first milestone.
```

The agent should discover docs, cache normalized snapshots in `.docs/`, ingest them, create an adaptive roadmap, and keep you in the driver's seat.
