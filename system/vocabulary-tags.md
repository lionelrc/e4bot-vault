---

vocabulary: tags

version: 2

updated: 2026-05-20

rule: "Utiliser uniquement le tag le plus spécifique. Ne jamais combiner parent + enfant du même domaine."

---
# Vocabulary — Tags

Source de vérité pour tous les tags autorisés dans le vault.
Ajouter un nouveau tag ici avant de l'utiliser dans un fichier.
## Domaines principaux (core de ce vault)
### ia

Agents, modèles, éthique, stratégie, marché de l'IA.

- `ia/agents`
- `ia/modeles`
- `ia/ethique`
- `ia/strategie`
- `ia/marche`
### geopolitique

Relations internationales, conflits, diplomatie, rapports de puissance.
Exclut : politique interne des États.

- `geopolitique/chine-usa`
- `geopolitique/russie-ukraine`
- `geopolitique/union-europeenne`
- `geopolitique/moyen-orient`
- `geopolitique/technologie`
- `geopolitique/theories`
### politique

Institutions, idéologies, partis, politiques publiques, gouvernance interne.
Exclut : relations internationales (→ geopolitique).

- `politique/democratie`
- `politique/extreme-droite`
- `politique/gauche`
- `politique/liberalisme`
- `politique/institutions`
- `politique/elections`
### economie

Théories économiques, systèmes financiers, macro/micro, marché du travail.

- `economie/travail`
- `economie/marche`
- `economie/inegalites`
- `economie/technologie`
### business

Stratégie d'entreprise, modèles économiques, organisation, leadership.
Exclut : théories économiques macro (→ economie).

- `business/strategie`
- `business/organisation`
- `business/leadership`
- `business/innovation`
### philosophie

Épistémologie, éthique, métaphysique, pensée critique.

- `philosophie/epistemologie`
- `philosophie/ethique`
- `philosophie/politique`
- `philosophie/metaphysique`
### histoire

Événements, périodes, contextes historiques.

- `histoire/xxe-siecle`
- `histoire/guerre-froide`
- `histoire/nazisme`
- `histoire/colonialisme`
### culture

Arts, littérature, cinéma, musique, culture populaire.
(pas de sous-tags définis — ajouter selon les besoins)

---

## Domaines secondaires (disponibles, hors scope principal)

### sciences-cognitives

Psychologie, neurosciences, cognition, biais cognitifs.
Exclut : sociologie (→ sciences-sociales).

- `sciences-cognitives/biais-cognitifs`
- `sciences-cognitives/desinformation`
### sciences-sociales

Sociologie, anthropologie, dynamiques sociales.

- `sciences-sociales/anthropologie`
- `sciences-sociales/inegalites`
- `sciences-sociales/medias`
- `sciences-sociales/ecologie`
### religion

Religions, spiritualité, théologie, croyances.
(pas de sous-tags définis — ajouter selon les besoins)
### tech

Technologies et informatique générale, hors IA spécifique.
(pas de sous-tags définis — ajouter selon les besoins)
### biologie

Biologie, génétique, évolution, physiologie.
(pas de sous-tags définis — ajouter selon les besoins)
### physique

Physique, cosmologie, mécanique quantique.
(pas de sous-tags définis — ajouter selon les besoins)
### mathematiques

Mathématiques, statistiques, logique.
(pas de sous-tags définis — ajouter selon les besoins)

---
## Règles

- Utiliser le tag le plus spécifique uniquement.
- Ne jamais combiner parent + enfant du même domaine :
✅ `politique/democratie`
❌ `politique` + `politique/democratie`
- Un fichier peut porter plusieurs tags de domaines différents :
✅ `ia/strategie` + `business/innovation`
- Avant d'utiliser un nouveau tag, l'ajouter à ce fichier.
- Un tag parent seul est autorisé quand aucun sous-tag existant ne convient.
- Hermes s'arrête et signale tout tag non présent dans ce fichier
avant de l'utiliser.
---

## Tags de claims

Utilisés inline dans le corps des notes, companions, et drafts.
Format : `[TAG — attributionoptionnelle]`

- `[SOURCE — Outlet, Auteur, Date]` — fait sourcé, attribution vérifiable
- `[NON VÉRIFIÉ — <source approximative>]` — source non confirmée ou de mémoire
- `[LACUNE]` — information manquante, jamais comblée par de la spéculation

Règle absolue : une `[LACUNE]` n'est jamais remplacée par une inférence présentée comme fait.
Si l'information ne peut pas être sourcée, formuler comme inférence explicite :
"cela suggérerait…", "si cela tient, alors…" — jamais comme assertion.

---

## Tags de contradiction

Utilisés inline quand deux sources ou cadres s'opposent. Ne jamais lisser.

- `[CONTRADICTION FACTUELLE]` — deux sources affirment des faits incompatibles
- `[CONTRADICTION INTERPRÉTATIVE]` — deux sources tirent des conclusions opposées des mêmes faits
- `[TENSION NON RÉSOLUE]` — deux cadres d'analyse coexistent sans qu'on puisse trancher

Si une synthèse est demandée, la proposer marquée comme interprétation, pas comme résolution.
