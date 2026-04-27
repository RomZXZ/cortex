---
name: conventions
version: 1.0.0
description: Format standard et conventions pour tous les agents Cortex
---

# Conventions Cortex

Ce document definit le format standard que chaque agent doit respecter.

## Format d'un fichier agent

Chaque agent `.md` se compose de deux parties :

### 1. Front Matter YAML (obligatoire)

```yaml
---
name: nom-de-l-agent          # Identifiant unique, kebab-case
version: 1.0.0                # Semantic versioning
phase: discovery               # discovery | solutioning | build | test | launch | feedback
description: >                # Description courte (1-2 lignes)
  Ce que fait cet agent en une phrase.
triggers:                      # Mots-cles qui declenchent cet agent
  - "mot cle 1"
  - "mot cle 2"
dependencies:                  # Autres agents dont celui-ci depend
  - agent-name
outputs:                       # Artefacts produits par cet agent
  - output-file.md
---
```

### 2. Corps Markdown (obligatoire)

```markdown
# {Emoji} {Nom de l'Agent}

## Role
Qui es-tu ? Quelle est ta mission ? (2-3 phrases max)

## Contexte
Dans quel cadre cet agent est utilise.

## Instructions
Etapes numerotees que l'agent doit suivre.

## Contraintes
Ce que l'agent ne doit PAS faire.

## Format de Sortie
Structure attendue du livrable produit par l'agent.

## Exemples (optionnel)
Exemples concrets pour calibrer la qualite de sortie.
```

## Regles de nommage

| Element | Convention | Exemple |
|---------|-----------|---------|
| Fichier agent | `kebab-case.md` | `market-researcher.md` |
| Nom (front matter) | `kebab-case` | `market-researcher` |
| Dossier phase | `lowercase` | `discovery/` |
| Version | `semver` | `1.0.0` |
| Outputs | `kebab-case.md` | `market-analysis.md` |

## Regles de contenu

1. **Langue** - Le contenu des agents est en **francais**. Les noms de fichiers, champs YAML, et identifiants sont en **anglais**.
2. **Concision** - Un agent tient idealement sur **1 page** (max 2). S'il est trop long, il faut le decouper en sous-agents.
3. **Autonomie** - Chaque agent doit etre comprehensible **seul**, sans avoir lu les autres.
4. **Actionnable** - Les instructions doivent etre des **actions concretes**, pas des principes vagues.
5. **Testable** - Le format de sortie doit etre assez precis pour qu'on puisse **verifier** si l'agent a bien fait son travail.

## Versioning

- **Patch** (`1.0.x`) : Corrections de typos, clarifications mineures
- **Minor** (`1.x.0`) : Ajout d'instructions, nouveaux exemples, ameliorations
- **Major** (`x.0.0`) : Changement de structure, de role, ou de format de sortie

## Emojis par phase

| Phase | Emoji |
|-------|-------|
| Discovery | 🔍 |
| Solutioning | 💡 |
| Build | 🏗️ |
| Test | 🧪 |
| Launch | 🚀 |
| Feedback | 🔄 |
| Skill | ⚡ |
| Meta | 📐 |
