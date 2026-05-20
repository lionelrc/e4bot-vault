# CLAUDE.md — e4bot vault

Rules for any LLM (Claude Code or other) working on this vault.
Read this file before touching anything.

## Vault path

/Users/lionel-e4/Code/e4bot/e4bot-vault

## Structure
e4bot-vault/
├── inbox/          # Manual capture — read-only
├── raw/            # Immutable source material
│   ├── articles/
│   ├── assets/
│   ├── companions/ # Only folder in raw/ where LLMs may create files
│   ├── podcasts/
│   ├── reports/
│   └── videos/
├── discussions/    # LLM and Telegram discussions
├── draft/          # Intermediate writing — promote to wiki/ after review
├── seeds/          # Ideas and starting points
├── outputs/        # Final content outputs
├── wiki/           # Long-term knowledge base — source of truth
│   ├── notes/      # Thematic and factual notes
│   ├── entities/   # People, organisations, products, places
│   └── concepts/   # Ideas, frameworks, technologies
└── system/         # Reference documents — read-only

## Folder permissions

| Folder          | Read | Write | Notes                              |
|-----------------|------|-------|------------------------------------|
| inbox/          | yes  | no    | Manual capture only                |
| raw/*           | yes  | no    | Immutable — never modify or delete |
| raw/companions/ | yes  | yes   | Create only — no overwrites        |
| discussions/    | yes  | yes   |                                    |
| draft/          | yes  | yes   |                                    |
| seeds/          | yes  | yes   |                                    |
| outputs/        | yes  | yes   |                                    |
| wiki/           | yes  | yes   | Never delete without confirmation  |
| system/         | yes  | no    | Read-only reference                |

## Frontmatter standard

Every file in wiki/ or draft/ must include:

```yaml
title:
type: note | entity | concept | companion
status: draft | stable | archived
created: YYYY-MM-DD
updated: YYYY-MM-DD
source:
tags: []
```

Additional fields by type:
- entity   -> aliases: []
- concept  -> learn: true|false
- companion -> source_url:, ingested:, sha256:

Templates are in system/templates/.

## Note types

- wiki/notes/     — thematic notes, connective tissue, link to entities and concepts
- wiki/entities/  — one page per identifiable actor (person, org, product, place)
- wiki/concepts/  — one page per durable idea, framework, or technology
- raw/companions/ — one companion per ingested source, named <slug>.comp.md

## Tags

All authorised tags are defined in system/vocabulary-tags.md.
Three tag families:
1. Domain tags       — ia/agents, politique/democratie, etc.
2. Claim tags        — [SOURCE — ...], [NON VERIFIE — ...], [LACUNE]
3. Contradiction tags — [CONTRADICTION FACTUELLE], [CONTRADICTION INTERPRETATIVE], [TENSION NON RESOLUE]

Never use a tag not defined in vocabulary-tags.md.
Never combine a parent tag with its child from the same domain.

## Editorial discipline

Full rules in system/editorial-values.md. Essential constraints:

- The companion contains no analysis. The note does not duplicate the source.
- Max 15 words quoted verbatim from any source.
- One direct quote per source maximum — paraphrase everything else.
- Never invent attributions — use [NON VERIFIE] if uncertain.
- Never fill a [LACUNE] with speculation. Use explicit inference markers instead.
- Never smooth over contradictions — tag them.
- On contested topics, represent all positions in good faith.

## Absolute safety rules

- Never delete any file without explicit user confirmation.
- Never overwrite an existing note without explicit user confirmation.
- Never modify files in raw/ (except creating new files in raw/companions/).
- Never modify .obsidian/ configuration files.
- Always preserve YAML frontmatter when editing notes.
- Always preserve Obsidian [[wikilinks]].
- Never restructure folders without a confirmed plan.
- When in doubt, ask LRC before writing.
