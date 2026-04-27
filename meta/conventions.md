---
name: conventions
version: 1.1.0
description: Format standard et conventions pour tous les agents Cortex
---

# 📐 Conventions Cortex

Ce document définit le format standard que chaque agent doit respecter.

## Format d'un fichier agent

Chaque agent `.md` se compose de deux parties :

### 1. Front Matter YAML (obligatoire)

```yaml
---
name: nom-de-l-agent          # Identifiant unique, kebab-case
version: 1.0.0                # Semantic versioning
phase: discovery               # discovery | solutioning | build | test | launch | feedback
type: component                # component | interactive | workflow (voir section Types)
description: >                # Description courte trigger-friendly (1-2 lignes)
  Ce que fait cet agent en une phrase.
intent: >                     # (optionnel) Explication approfondie du "pourquoi" de cet agent
  Raison d'être et contexte intellectuel de cet agent.
triggers:                      # Mots-clés qui déclenchent cet agent
  - "mot clé 1"
  - "mot clé 2"
dependencies:                  # Autres agents dont celui-ci dépend
  - agent-name
related_skills:                # Agents liés (pas de dépendance directe)
  - agent-name
outputs:                       # Artefacts produits par cet agent
  - output-file.md
estimated_time: 15-30 min      # Durée estimée d'exécution
best_for:                      # (optionnel) Scénarios concrets d'utilisation
  - "Validation produit"
  - "Early-stage discovery"
---
```

### 2. Corps Markdown (obligatoire)

```markdown
# {Emoji} {Nom de l'Agent}

## Rôle
Qui es-tu ? Quelle est ta mission ? (2-3 phrases max)

## Contexte
Dans quel cadre cet agent est utilisé. Informations de base
sur l'utilisateur et ses projets.

## Instructions
Étapes numérotées que l'agent doit suivre.
1. Première étape
2. Deuxième étape
3. ...

## Contraintes
Ce que l'agent ne doit PAS faire. Limites et garde-fous.

## Ce que cet agent NE FAIT PAS
Liste explicite de ce qui est hors scope pour cet agent.
Empêche les dérives de périmètre et clarifie les responsabilités.
- {Hors scope 1}
- {Hors scope 2}

## Anti-patterns
Erreurs courantes à éviter quand on utilise cet agent.
- ❌ {Anti-pattern 1} — {Pourquoi c'est un problème}
- ❌ {Anti-pattern 2} — {Pourquoi c'est un problème}

## Format de Sortie
Structure attendue du livrable produit par l'agent.

## Exemples (optionnel)
Exemples concrets pour calibrer la qualité de sortie.
```

## Types d'agents

Cortex distingue trois niveaux d'agents, inspirés des meilleures pratiques communautaires :

```
┌──────────────────────────────────────────────┐
│       WORKFLOW (orchestrateurs)               │
│  Processus complets de bout en bout           │
│  Durée : jours/semaines                       │
│  Orchestre plusieurs Interactive + Component   │
└──────────────────────────────────────────────┘
         ↓ orchestre
┌──────────────────────────────────────────────┐
│       INTERACTIVE (guides)                    │
│  Discovery guidée avec questions adaptatives  │
│  Durée : 30-90 minutes                        │
│  Pose des questions, recommande, décide        │
└──────────────────────────────────────────────┘
         ↓ utilise
┌──────────────────────────────────────────────┐
│       COMPONENT (exécutants)                  │
│  Templates et exécution rapide                │
│  Durée : 10-30 minutes                        │
│  Produit un livrable concret                   │
└──────────────────────────────────────────────┘
```

| Type | Quand l'utiliser | Exemples |
|------|-----------------|----------|
| `component` | Template ou exécution d'un livrable précis | user-story, market-analysis |
| `interactive` | Besoin de guidance, choix entre options | prioritization-advisor |
| `workflow` | Processus multi-étapes sur plusieurs jours | full-discovery, feature-lifecycle |
| `meta` | Gestion du framework et des états | cortex-init |

## Gestion d'État (State Management)

Pour fonctionner comme un Crew (équipage), Cortex utilise la notion d'état partagé.
Chaque projet intégré doit posséder un fichier `cortex-state.md` à sa racine ou dans `.cortex/`.

Ce fichier agit comme la **mémoire** des agents :
- Il traque les phases terminées et les livrables produits.
- Les agents Workflow le lisent pour savoir quelle étape déclencher ensuite.
- Les agents Component le lisent pour trouver les dépendances.
- **Règle absolue** : À la fin de sa tâche, chaque agent DOIT mettre à jour le fichier `cortex-state.md`.

## Placeholders (Variables)

Les agents peuvent utiliser des "placeholders" dans leurs instructions pour être plus génériques. Ces variables sont généralement définies dans le `cortex-state.md`.

| Placeholder | Utilisation |
|-------------|-------------|
| `{project_name}` | Le nom du projet (ex: le-chef-app) |
| `{domain}` | Le domaine cible (ex: cuisine, budget) |
| `{target_audience}`| L'utilisateur final visé |
| `{current_phase}` | La phase du cycle produit actuelle |

## Règles de nommage

| Élément | Convention | Exemple |
|---------|-----------|---------|
| Fichier agent | `kebab-case.md` | `market-researcher.md` |
| Nom (front matter) | `kebab-case` | `market-researcher` |
| Dossier phase | `lowercase` | `discovery/` |
| Version | `semver` | `1.0.0` |
| Outputs | `kebab-case.md` | `market-analysis.md` |

## Règles de contenu

1. **Langue** — Le contenu des agents est en **français**. Les noms de fichiers, champs YAML, et identifiants sont en **anglais**.
2. **Concision** — Un agent tient idéalement sur **1 page** (max 2). S'il est trop long, il faut le découper en sous-agents.
3. **Autonomie** — Chaque agent doit être compréhensible **seul**, sans avoir lu les autres.
4. **Actionnable** — Les instructions doivent être des **actions concrètes**, pas des principes vagues.
5. **Testable** — Le format de sortie doit être assez précis pour qu'on puisse **vérifier** si l'agent a bien fait son travail.
6. **Pédagogique** — Chaque agent doit non seulement exécuter, mais **expliquer** la méthode utilisée. ABC : Always Be Coaching.
7. **Anti-patterns** — Nommer explicitement les erreurs courantes aide l'utilisateur ET le modèle IA à éviter les pièges.

## Versioning

- **Patch** (`1.0.x`) : Corrections de typos, clarifications mineures
- **Minor** (`1.x.0`) : Ajout d'instructions, nouveaux exemples, améliorations
- **Major** (`x.0.0`) : Changement de structure, de rôle, ou de format de sortie

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
| Workflow | 🔀 |

## 🤖 Protocole d'Auto-Amélioration (Self-Improvement)

Chaque agent Cortex a le devoir de s'améliorer. À la fin de chaque tâche complexe ou si un point de friction est identifié :

1. **Auto-Critique** : L'agent doit se demander : "Mes instructions m'ont-elles permis d'être efficace ?".
2. **Signalement Proactif** : Si une ambiguïté est trouvée, l'agent doit proposer une entrée pour `meta/learnings.md` à Romain.
3. **Information Utilisateur** : L'agent doit informer Romain : "J'ai identifié une amélioration potentielle pour mon rôle. Veux-tu que je l'ajoute au journal des apprentissages ?".
