# Structure Template

Use this reference when initializing a new local Markdown knowledge base.

## Recommended Structure

```text
knowledge-base/
├── raw/
│   └── llm-wiki.md
├── wiki/
│   ├── log.md
│   └── governance-log.md
├── system/
│   ├── AGENTS.md
│   ├── CLAUDE.md
│   ├── wiki-harness.md
│   └── wiki-governance.md
├── AGENTS.md
└── CLAUDE.md
```

This is the default MyKnowledge initialization skeleton. Do not create topic directories during initialization.

`presentation/` is optional. Create it only when the user explicitly asks for human-facing generated outputs.

## Initialization Sequence

1. Identify the root folder.
2. Create only `raw/`, `wiki/`, and `system/`.
3. Copy templates:
   - `assets/templates/log.md` to `wiki/log.md`
   - `assets/templates/governance-log.md` to `wiki/governance-log.md`
   - `assets/templates/llm-wiki.md` to `raw/llm-wiki.md`
   - `assets/templates/root-AGENTS.md` to `AGENTS.md`
   - `assets/templates/root-CLAUDE.md` to `CLAUDE.md`
   - `assets/templates/system-AGENTS.md` to `system/AGENTS.md`
   - `assets/templates/system-CLAUDE.md` to `system/CLAUDE.md`
   - `assets/templates/wiki-harness.md` to `system/wiki-harness.md`
   - `assets/templates/wiki-governance.md` to `system/wiki-governance.md`
4. Do not create domain or topic directories during initialization.
5. Do not create `wiki/index.md` by default unless the user asks for a navigation page or real content already needs one.
6. Do not create `.agents/`, `.claude/`, `.obsidian/`, `.git/`, `.pytest_cache/`, `presentation/`, or presentation registries unless the user explicitly requests those environment or output layers.

## Taxonomy Guidance

Start shallow. Prefer pages and MOC maps before directories.

Topic directories and navigation pages are derived outputs. The harness and governance rules are the source of truth.

Create a directory when:

- The topic will keep growing.
- A retrieval entry is stable.
- The category has clear boundaries.
- Several existing pages already belong there.
- The directory lowers retrieval cost compared with a topic overview page alone.

Do not create a full taxonomy from imagination. Let structure emerge from real retrieval needs.
