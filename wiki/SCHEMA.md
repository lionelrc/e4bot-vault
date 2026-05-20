---
title: Vault Schema
type: system
status: active
created: 2026-05-11
updated: 2026-05-18
---
# Vault Schema

Fichier de reference pour Hermes et le skill llm-wiki.
Definit la structure, les conventions, et les regles du vault e4bot.
Lire ce fichier en premier avant toute operation sur le vault.

---

## Folder map

| Folder           | Purpose                                 | Hermes access                  |
|------------------|-----------------------------------------|--------------------------------|
| inbox/           | Capture rapide manuelle                 | read-only                      |
| raw/             | Sources immuables                       | read only — voir regles raw    |
| raw/articles/    | Web scraping, newsletters, clippings    | read-only                      |
| raw/assets/      | PDFs, images, fichiers binaires         | read-only                      |
| raw/companions/  | Fichiers companion crees par Hermes     | read/write (creation only)     |
| raw/podcasts/    | Transcripts audio et podcasts           | read-only                      |
| raw/reports/     | Rapports, white papers                  | read-only                      |
| raw/videos/      | Transcripts YouTube                     | read-only                      |
| discussions/     | Conversations LLM et Telegram           | read/write                     |
| drafts/          | Notes intermediaires et brouillons      | read/write                     |
| wiki/            | Knowledge base — source of truth        | read/write                     |
| wiki/notes/      | Notes thematiques et factuelles         | read/write                     |
| wiki/entities/   | Personnes, organisations, produits      | read/write                     |
| wiki/concepts/   | Idees, frameworks, technologies         | read/write                     |
| system/          | Referentiels stables                    | read-only                      |

---

## Regles raw/

Les fichiers sources dans raw/ sont immuables.
Hermes ne modifie jamais et ne supprime jamais un fichier source existant.
Hermes peut uniquement creer des fichiers companion dans raw/companions/.

Convention companion :
- Un fichier companion par source ingere
- Nom : meme nom que la source avec suffixe .comp.md
- Exemple : raw/companions/strategie-ia-apple.comp.md pour raw/articles/strategie-ia-apple.md

---

## Wiki structure

Le wiki est la source de verite du vault. Trois sous-dossiers.

### wiki/notes/
Notes thematiques ou factuelles sur un sujet precis.
Exemples : strategie-ia-apple.md, levee-de-fonds-mistral-2026.md
Pointent vers des entities et des concepts via wikilinks.
Sont le tissu connectif du wiki.

### wiki/entities/
Une page par acteur identifiable : personne, organisation, produit, lieu.
Exemples : apple.md, andrej-karpathy.md, openai.md, france.md
Recoivent des liens entrants depuis les notes.
Stables dans le temps.

### wiki/concepts/
Une page par idee, framework, ou technologie durable.
Exemples : mlx.md, agentic-ai.md, data-governance.md, transformer.md
Recoivent des liens entrants depuis les notes et les entities.

---

## Modele de liens

wiki/notes/strategie-ia-apple.md
    [[apple]]       -> wiki/entities/apple.md
    [[mlx]]         -> wiki/concepts/mlx.md
    [[tim-cook]]    -> wiki/entities/tim-cook.md

Les notes sont le tissu connectif.
Les entities et concepts sont les noeuds stables du graphe.

---

## Frontmatter standard

Toute note dans wiki/ ou drafts/ doit inclure :

title:
type: note | entity | concept | companion
status: draft | review | stable
created: YYYY-MM-DD
updated: YYYY-MM-DD
source:
tags: []

Champs supplementaires par type :
- entity : relations: []
- concept : learn: false
- companion : source_url:, ingested:, sha256:

---

## Modele companion

Frontmatter :

title: Companion — nom-du-fichier-source
type: companion
status: stable
created: YYYY-MM-DD
updated: YYYY-MM-DD
source: raw/articles/nom-du-fichier-source.md
source_url: https://...
ingested: YYYY-MM-DD
sha256: abc123
tags: []

Corps :

## Source
[[nom-du-fichier-source]]

## Notes wiki creees
- [[note-1]]
- [[entity-1]]
- [[concept-1]]

## Resume d ingestion
Bref resume de ce qui a ete extrait et ou ca a atterri.

---

## Conventions

- Noms de fichiers en minuscules avec tirets : strategie-ia-apple.md
- Minimum 2 wikilinks par note wiki
- Ne pas creer de note pour une mention passagere
- Toujours verifier wiki/ avant de creer une nouvelle note
- Promouvoir drafts/ vers wiki/ apres validation humaine

---

## Mapping llm-wiki vers e4bot

| llm-wiki standard    | e4bot-vault             |
|----------------------|-------------------------|
| raw/articles/        | raw/articles/           |
| raw/papers/          | raw/reports/            |
| raw/transcripts/     | raw/videos/ ou raw/podcasts/ selon la source |
| raw/assets/          | raw/assets/             |
| entities/            | wiki/entities/          |
| concepts/            | wiki/concepts/          |
| comparisons/         | drafts/                 |
| queries/             | drafts/                 |

Notes sans type entity ou concept clair -> wiki/notes/

---

## Log

Voir wiki/log.md pour lhistorique des actions Hermes sur le vault.
