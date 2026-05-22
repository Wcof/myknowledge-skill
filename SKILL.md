---
name: myknowledge-skill
description: Use when creating, organizing, migrating, auditing, or maintaining a local Markdown or Obsidian-style knowledge base with Raw/Wiki/System layers, metadata, MOC retrieval maps, governance logs, lightweight templates, and presentation outputs generated from governed wiki source pages.
---

# MyKnowledge Skill

This skill helps an agent initialize and maintain a local Markdown knowledge base that can be searched, governed, migrated, and optionally rendered for human presentation.

## Use This Skill When

- The user wants to create a local Markdown or Obsidian-style knowledge base.
- The user wants to initialize a MyKnowledge-style knowledge base skeleton.
- The user wants to ingest raw notes, transcripts, clips, screenshots, article summaries, or meeting notes.
- The user wants to promote raw material into structured wiki pages.
- The user wants metadata, MOC pages, index pages, governance logs, or health checks.
- The user wants to reorganize a knowledge base without losing retrieval paths.
- The user explicitly asks for HTML, deck, PPT, report, or presentation output generated from governed wiki source pages.

## Do Not Use This Skill When

- The request is only about application code, unrelated documents, or general writing.
- The user only wants a one-off answer and does not want to update a knowledge base.
- The target repository has stronger local rules that conflict with this skill. In that case, obey the target repository rules.

## Rule Priority

1. If the target knowledge base already has `system/wiki-harness.md`, read it first and obey it.
2. If the target knowledge base has a governance rule file such as `system/wiki-governance.md`, read it for Raw/Wiki promotion, MOC, PARA, templates, action items, and health checks.
3. Use this skill's references only when the target knowledge base has no local rule for the same topic.
4. If the user asks for presentation output, read `references/presentation-extension.md` only after confirming the wiki source page, output intent, mode, and style constraints.

## Core Workflow

1. Identify the target knowledge base root and check whether local rules exist.
2. Classify input as raw capture, wiki-ready knowledge, governance work, health check, or presentation request.
3. When initializing a new MyKnowledge-style skeleton, read `references/structure-template.md` and create only `raw/`, `wiki/`, `system/`, root `AGENTS.md`, root `CLAUDE.md`, `system/AGENTS.md`, `system/CLAUDE.md`, `system/wiki-harness.md`, `system/wiki-governance.md`, `wiki/log.md`, `wiki/governance-log.md`, and `raw/llm-wiki.md`.
4. Preserve original material in `raw/` when it is unprocessed, ambiguous, externally sourced, or not yet validated.
5. Promote material into `wiki/` only when it has been summarized, structured, linked, and given retrieval metadata.
6. Add or repair metadata for edited wiki pages:

```yaml
---
title: Page title
domain: Top-level domain
scope: Mid-level scope
topic: Topic
primary_entry: Main retrieval entry
secondary_entries:
  - Secondary retrieval entry
status: current
date: YYYY-MM-DD
objects:
  - Object/module/person/system/event
---
```

7. Keep MOC or topic overview pages as retrieval maps. Do not copy full page bodies into maps.
8. Treat topic directories and `wiki/index.md` as derived outputs. Do not create them during initialization unless the user explicitly asks or real content already requires them.
9. Update `wiki/log.md` for structural changes.
10. Update `wiki/governance-log.md` for governance history, health checks, unresolved issues, and maintenance decisions.

Allowed `status` values are only `draft`, `current`, `archive`, and `unknown`.

## Progressive References

- For initializing a new knowledge base, read `references/structure-template.md`.
- For creating or adapting local harness rules, read `references/harness-template.md`.
- For Raw/Wiki promotion, MOC, PARA, lightweight templates, action items, and health checks, read `references/governance-template.md`.
- For examples, read `references/examples.md`.
- For HTML, deck, PPT, report, presentation, or export requests, read `references/presentation-extension.md`.

## Guardrails

- Do not mechanically force every page into the same template.
- Do not invent a deep taxonomy before reading the user's real material and retrieval needs.
- Do not hardcode a user's current topic directory tree into a generic knowledge-base initialization.
- Do not create topic directories, `wiki/index.md`, presentation directories, or editor/agent environment directories during minimal MyKnowledge initialization unless explicitly requested.
- Do not add system scripts such as `.py`, `.js`, `.sh`, or build tools unless the user explicitly approves a separate automation design.
- Do not treat `presentation/` or exported files as knowledge sources.
- Do not perform broad moves, renames, merges, or deletions without first making a structure plan.
- Do not create empty directories only for aesthetic symmetry.
- Do not duplicate full content across multiple wiki pages. Use links and MOC maps.
- Do not hide discovered governance problems. Report them, and log them when they affect future retrieval or maintenance.
