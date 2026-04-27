# 🧠 Cortex

**Bibliothèque d'agents IA réutilisables pour le développement de produits personnels.**

Cortex est un ensemble structuré d'instructions d'agents IA (fichiers Markdown) couvrant tout le cycle de vie d'un produit : de la découverte utilisateur au déploiement, en passant par le design, le build et le feedback.

## Pourquoi Cortex ?

- 🔁 **Réutilisable** — Importe Cortex dans n'importe quel projet via symlink ou git submodule
- 📐 **Structuré** — Chaque agent a un rôle clair, des inputs/outputs définis, et un format standard
- 🧩 **Modulaire** — Utilise un seul agent ou toute la chaîne
- 📝 **Versionné** — Chaque agent est versionné, chaque changement est tracé
- 🤖 **Compatible** — Fonctionne avec Antigravity, Gemini CLI, Jules, et tout outil supportant `AGENTS.md`

## Structure

```
cortex/
├── CORTEX.md                    # 🧠 Orchestrateur — point d'entrée
├── meta/                        # Conventions et guides
│   ├── conventions.md
│   └── integration-guide.md
├── agents/                      # Agents spécialisés par phase
│   ├── discovery/               # 🔍 Recherche & compréhension
│   ├── solutioning/             # 💡 Conception de la solution
│   ├── build/                   # 🏗️ Développement
│   ├── test/                    # 🧪 Qualité & sécurité
│   ├── launch/                  # 🚀 Déploiement & GTM
│   └── feedback/                # 🔄 Feedback & itération
├── skills/                      # Capacités transversales (Phase 2)
└── templates/                   # Templates réutilisables (Phase 2)
```

## Utilisation rapide

### Dans un nouveau projet

```bash
# Option 1 : Symlink (dev local)
ln -s ~/Documents/Cortex/CORTEX.md ./CORTEX.md

# Option 2 : Git Submodule (versioned)
git submodule add https://github.com/RomZXZ/cortex .cortex
```

### Invoquer un agent

Référence le fichier agent dans ton prompt :

> "En suivant les instructions de `agents/discovery/market-researcher.md`, analyse le marché pour une app de gestion de budget personnel."

Ou utilise l'orchestrateur :

> "Cortex, je veux créer une app de gestion de budget. Par quoi on commence ?"

## Phases du cycle produit

| Phase | Emoji | Agents | Description |
|-------|-------|--------|-------------|
| **Discovery** | 🔍 | market-researcher, problem-definer | Comprendre le marché et le problème |
| **Solutioning** | 💡 | product-designer, tech-architect | Concevoir la solution |
| **Build** | 🏗️ | project-planner, frontend-developer | Construire le produit |
| **Test** | 🧪 | qa-engineer | Valider la qualité |
| **Launch** | 🚀 | deployer, gtm-strategist | Mettre en production |
| **Feedback** | 🔄 | feedback-collector | Itérer sur les retours |
| **Learning** | 🌱 | knowledge-curator | Faire évoluer le framework |

## Projets utilisant Cortex

- [`le-chef-app`](https://github.com/RomZXZ/le-chef-app) — App de cuisine / batch cooking
- *Prochains : planning familial & budget, petits jeux, outils*

## Contribuer

Ce repo est personnel mais les PRs sont bienvenues si tu trouves ça utile.
Chaque agent suit le format défini dans [`meta/conventions.md`](meta/conventions.md).

## Licence

MIT
