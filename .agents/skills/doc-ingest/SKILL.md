---
name: doc-ingest
description: Use when official docs, docs-discovery snapshots, llms.txt outputs, markdown files, or framework specs need to become the ground-truth technical rules for learning and review.
---

# Doc Ingest

## Objective
Parse and index the structural layer of official documentation or a docs-discovery snapshot to establish the ground-truth technical rules for the conversation. Override pre-existing model knowledge whenever the ingested source conflicts with memory, tutorials, or older API patterns.

## Instructions
1. Accept any of these inputs:
   - User-pasted documentation.
   - Local markdown snapshots under `.docs/<technology>/`.
   - Official website documentation fetched by the agent.
   - Context7 documentation excerpts.
   - `llms.txt` or `llms-full.txt` documentation bundles from an official site.
2. Analyze the content to isolate:
   - Primary framework version numbers.
   - Core API boundaries and structural primitives.
   - Configuration requirements.
   - Runtime/server/client boundaries.
   - 3-7 prominent architectural breaking changes, pitfalls, or version-specific gotchas noted in the text.
3. Generate an ASCII flowchart visualization showing how data flows through the technology based strictly on the source.
4. Explicitly list the precise version/configuration rules the user must adopt.
5. Produce rules that can be reused by socratic-review and checkpoint-validator.
6. If the source is incomplete, stale, ambiguous, or non-official, stop and request docs-discovery refresh or user confirmation.

## Output Format
### Ingestion Report: [Stack Name] [Version]
- **Source Snapshot:** [Path/URL/Context7 ID]
- **Core Paradigm Identified:** [e.g., file-based routing, server-first rendering, client/server component boundary]
- **Critical Configuration Rules:** [Bullet points of absolute non-negotiables]

### Architectural Blueprint
```text
[Insert clean ASCII system architecture map here]
```

### Documentation Pitfalls & Gotchas
1. [Pitfall 1]
2. [Pitfall 2]
3. [Pitfall 3]

### Review Rules Export
- [Rule usable during socratic-review]
- [Rule usable during checkpoint-validator]
