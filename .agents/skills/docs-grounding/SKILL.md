---
name: docs-grounding
description: Use for official documentation discovery, current library/framework/API/CLI/config lookup, docs snapshot creation, and converting docs into source-of-truth rules for learning and review.
---

# Docs Grounding

## Purpose

Create the technical source of truth for a learning track. This skill combines documentation discovery, current API lookup, snapshot creation, and rule extraction.

Use it before making framework/library-specific claims about setup commands, file conventions, configuration, APIs, version behavior, or library-specific debugging.

## Source Hierarchy

1. User-provided official docs URL.
2. Official docs site, prefer `llms.txt` / `llms-full.txt` when available.
3. Context7 for current library/framework docs.
4. Official repository docs if the project points there.
5. Package registry metadata only to confirm official homepage/repository.

Reject random blogs, tutorials, forum posts, scraped mirrors, and outdated third-party examples as authority.

## `llms.txt` / `llms-full.txt` Rule

For broad learning-track grounding, try official `llms.txt` sources before Context7.

1. Identify the official domain. If ambiguous, ask.
2. Directly try common paths first:

   ```text
   https://<domain>/llms.txt
   https://<domain>/docs/llms.txt
   https://<domain>/llms-full.txt
   https://<domain>/docs/llms-full.txt
   ```

3. If those fail, do web search but only within the official domain:

   ```text
   site:<domain> llms.txt
   site:<domain> llms-full.txt
   ```

4. If still unavailable, use official docs navigation or Context7 for focused current lookup. Record what was tried.

## Context7 Rule

For current API syntax, setup commands, CLI usage, config options, version migration, or library-specific debugging, resolve the library first, then query docs. Do not silently fall back to memory if lookup fails; explain the limitation and ask whether the user accepts a potentially outdated answer.

Preferred local commands in this repo:

```bash
npm run ctx7 -- <commands>
npm run ctx7:library -- "Library Name" "specific user question"
npm run ctx7:docs -- /org/project "specific user question"
```

## Snapshot Policy

For learning tracks, write focused snapshots under:

```text
.docs/<technology-slug>/
├── manifest.md
├── sources.md
├── rules.md
├── architecture.md
├── pitfalls.md
└── sections/
```

Keep snapshots learning-relevant. Do not ingest an entire docs site unless necessary.

## Rule Extraction

Extract:

- official version/source date;
- setup path and commands;
- core primitives;
- file/folder conventions;
- runtime boundaries;
- configuration rules;
- security constraints;
- common pitfalls;
- first safe artifacts/labs;
- concepts to defer.

## Output Format

### Docs Grounding Report: [Technology]

- **Canonical Source:** [URL / Context7 ID]
- **Version/Freshness:** [version/date/unknown]
- **Snapshot Path:** `.docs/<technology-slug>/` or `none`
- **Accepted Sources:** [bullets]
- **Rejected Sources:** [bullets]

### Source-of-Truth Rules

- [non-negotiable rule]
- [non-negotiable rule]

### Architecture / Mental Model

```text
[ASCII flow or structure]
```

### Learning Extraction

- **First concept to teach:** [concept]
- **First safe artifact:** [artifact]
- **Early labs:** [2-4 lab ideas]
- **Defer:** [advanced topics]

### Next Handoff

- `learning-director`, `curriculum-planner`, or `practice-builder` depending on state.
