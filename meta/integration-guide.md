---
name: integration-guide
version: 1.0.0
description: Comment integrer Cortex dans un nouveau projet.
---

# Guide d'Integration Cortex

## Prerequis

- Git installe
- Un repo de projet initialise
- Cortex clone localement : `~/Documents/Cortex/`

## Methode 1 : Symlink (recommande pour le dev local)

La plus simple. Tous tes projets pointent vers le meme Cortex.

```bash
# Depuis la racine de ton projet
ln -s ~/Documents/Cortex/CORTEX.md ./CORTEX.md

# Optionnel : lien vers les agents specifiques
mkdir -p .cortex
ln -s ~/Documents/Cortex/agents/ .cortex/agents
ln -s ~/Documents/Cortex/meta/ .cortex/meta
```

**Avantages** : Mise a jour instantanee, zero maintenance
**Inconvenients** : Pas versionne par projet, depend du chemin local

### .gitignore

```gitignore
# Cortex symlinks (ne pas commiter les liens locaux)
CORTEX.md
.cortex/
```

## Methode 2 : Git Submodule

```bash
git submodule add https://github.com/RomZXZ/cortex .cortex

# Mettre a jour Cortex dans un projet
cd .cortex
git pull origin main
cd ..
git add .cortex
git commit -m "chore: update cortex to latest"
```

## Methode 3 : Copier-coller selectif

```bash
cp ~/Documents/Cortex/agents/build/frontend-developer.md ./AGENTS.md
```

## Utilisation avec les outils IA

### Antigravity (IDE principal)

Reference les agents dans tes prompts :

> "En suivant les instructions de `.cortex/agents/build/frontend-developer.md`, implemente le composant Header."

### Gemini CLI

```bash
gemini -p "Lis le fichier .cortex/agents/discovery/market-researcher.md et analyse le marche pour une app de planning familial"
```

### Jules / Jules CLI

Pour deleguer des taches asynchrones a Jules :

> "En suivant les standards definis dans `.cortex/agents/build/frontend-developer.md` et `.cortex/agents/test/qa-engineer.md`, implemente et teste le composant Calendar."

Jules est particulierement utile pour :
- Les taches de build repetitives (PRs de refactoring)
- Les taches de test (audit de qualite)
- Les fixes de bugs identifies par le feedback-collector

### Cursor (optionnel)

```bash
mkdir -p .cursor/rules
cp ~/Documents/Cortex/agents/build/frontend-developer.md .cursor/rules/frontend.mdc
```

### AGENTS.md (standard ouvert)

```markdown
# Agent Instructions

## Contexte Projet
Ce projet utilise le framework Cortex pour ses instructions d'agents.
Les agents sont dans `.cortex/agents/`.

## Agents actifs sur ce projet
- `.cortex/agents/build/frontend-developer.md`
- `.cortex/agents/test/qa-engineer.md`

## Overrides specifiques a ce projet
- Stack : Vue 3 au lieu de vanilla JS
- Style : Utiliser le design system X
```

## Structure type d'un projet integre

```
mon-projet/
|-- .cortex/              # Cortex (symlink ou submodule)
|   |-- agents/
|   |-- meta/
|   |-- CORTEX.md
|-- AGENTS.md             # Instructions specifiques au projet
|-- docs/
|   |-- problem-statement.md   # Output du problem-definer
|   |-- product-brief.md       # Output du product-designer
|   |-- architecture.md        # Output du tech-architect
|   |-- project-plan.md        # Output du project-planner
|-- src/
|-- package.json
|-- README.md
```
