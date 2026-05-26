---
name: docs-discovery
description: Use when the user names a technology/stack and wants the agent to find official docs automatically; resolves official docs, llms.txt, Context7 IDs, source URLs, and writes normalized markdown snapshots under .docs/.
---

# Docs Discovery

## Objective
Discover, verify, and cache official documentation for a requested technology so the learning workflow does not depend on the user manually providing docs every time. Produce normalized markdown snapshots that doc-ingest can treat as the local source of truth.

## Core Principle
Official documentation beats convenience. Do not use blog posts, tutorials, StackOverflow answers, random examples, or outdated unofficial mirrors as authoritative sources. If official sources are ambiguous, ask the user to confirm before ingestion.

## Discovery Order
Use this order unless the user explicitly provides a source:

1. **Known official URL from user input**
   - If the user gives an official docs URL, verify it and use it first.
2. **Official-site `llms.txt` discovery**
   - Once an official domain is known or strongly inferred, check likely machine-readable documentation endpoints:
     - `https://<official-domain>/llms.txt`
     - `https://<official-domain>/llms-full.txt`
     - `https://<official-domain>/docs/llms.txt`
     - `https://<official-domain>/docs/llms-full.txt`
   - Prefer `llms-full.txt` for comprehensive ingestion when available; prefer `llms.txt` for source maps or curated section lists.
3. **Official-domain web search for `llms.txt` only when probing fails**
   - If the official domain is known but the common paths do not expose `llms.txt`, search only for results constrained to the official domain or official repository.
   - Accept results only when they resolve back to the official domain/repository.
   - Reject third-party mirrors, blog reposts, and scraped copies.
4. **Context7 resolution**
   - Use the `context7` skill as the Context7 mechanism.
   - Resolve the library/framework ID using Context7 before querying docs.
   - Query focused official documentation sections from Context7.
   - Record the selected Context7 library ID in `sources.md`.
5. **Direct official docs fetch**
   - Fetch official documentation pages from the vendor/project website.
   - Follow only official docs navigation or pages directly linked from official docs.
6. **Official repository docs**
   - Use README/docs from the official GitHub/GitLab repository only if website docs are incomplete or the official site points there.
7. **Package registry metadata**
   - Use npm/PyPI/crates.io/etc. only to confirm official homepage/repository links, not as the primary docs source unless the package itself says so.
8. **Clarification gate**
   - If multiple projects share the same name, or officialness is uncertain, stop and ask the user.

## How to Find `llms.txt`
Do not web-search randomly for `llms.txt` as the first step. First identify the official domain through user input, Context7 metadata, package metadata, or the project's official repository/homepage. Then probe the standard endpoints listed above. If those fail, a constrained search is allowed only to discover an official-domain `llms.txt`/`llms-full.txt` URL. If no official domain can be identified confidently, ask the user to choose between candidates.

## Snapshot Policy
Cache only the learning-relevant normalized snapshot, not an indiscriminate copy of the entire docs site.

Write snapshots under:

```text
.docs/<technology-slug>/
├── manifest.md
├── sources.md
├── core-rules.md
├── architecture.md
├── gotchas.md
└── sections/
    ├── 01-foundations.md
    ├── 02-routing-or-core-api.md
    ├── 03-data-flow.md
    └── 04-mutations-or-side-effects.md
```

Use lowercase kebab-case for `<technology-slug>` such as `sveltekit`, `next-js`, `fastapi`, or `drizzle-orm`.

## Required Markdown Frontmatter
Every generated snapshot file must begin with:

```yaml
---
technology: "[Technology Name]"
version: "[Detected version or unknown]"
source_type: "official-url | llms.txt | llms-full.txt | context7 | official-repo | mixed"
retrieved_at: "YYYY-MM-DD"
canonical_url: "[Primary official URL]"
context7_id: "[Context7 library ID or none]"
freshness: "fresh | stale | unknown"
---
```

## Required Files

### `manifest.md`
Contains:
- Technology name and detected version.
- Snapshot date.
- Canonical docs URL.
- Selected source strategy.
- Refresh recommendation.
- Which docs sections were captured and why.

### `sources.md`
Contains:
- All URLs/Context7 IDs checked.
- Accepted sources and rejected sources.
- Reason for each decision.
- Whether `llms.txt` or `llms-full.txt` was found.

### `core-rules.md`
Contains:
- Non-negotiable API/configuration rules.
- File/folder conventions.
- Runtime boundaries.
- Version-sensitive rules.

### `architecture.md`
Contains:
- ASCII architecture/data-flow diagram.
- Explanation of major primitives and how data moves through them.

### `gotchas.md`
Contains:
- Breaking changes.
- Common traps.
- Server/client/runtime mistakes.
- Security pitfalls.

### `sections/*.md`
Contains focused sections that support the planned project. Do not capture irrelevant docs unless the roadmap needs them.

## Refresh Policy
If a snapshot already exists:

1. Read `manifest.md` first.
2. If it is older than 30 days, ask whether to refresh unless the user explicitly says to use cache.
3. If the user is starting a new serious project or production-minded roadmap, recommend refresh even if under 30 days.
4. If the user requests a specific version, refresh or create a version-specific snapshot.

## Output Format

### Docs Discovery Report: [Technology]

- **Canonical Source:** [URL]
- **Source Strategy:** [llms-full.txt | llms.txt | Context7 | direct official fetch | official repo | mixed]
- **Context7 ID:** [ID or none]
- **llms.txt Found:** [yes/no + URL]
- **llms-full.txt Found:** [yes/no + URL]
- **Snapshot Path:** `.docs/<technology-slug>/`
- **Freshness:** [fresh/stale/unknown]

### Source Decision Log
- ✅ Accepted: [source + reason]
- ❌ Rejected: [source + reason]

### Next Step
Invoke `doc-ingest` on `.docs/<technology-slug>/manifest.md` and related snapshot files.
