---
name: feature-lifecycle
version: 1.1.0
phase: build
type: workflow
description: >
  Orchestre le cycle de vie complet d'une nouvelle fonctionnalité, du design 
  jusqu'au QA.
intent: >
  Agir comme un "Crew Manager" pour la phase d'implémentation. Réduit la charge
  mentale en s'assurant que l'architecture, le planning, le code et les tests 
  sont enchaînés logiquement.
triggers:
  - "créer cette feature"
  - "workflow feature"
  - "ajouter la fonctionnalité"
dependencies:
  - product-designer
  - tech-architect
  - project-planner
  - frontend-developer
  - qa-engineer
related_skills:
  - code-reviewer
outputs:
  - cortex-state.md (updated)
  - (Outputs de tous les sous-agents)
estimated_time: 1-5 jours (asynchrone)
best_for:
  - "Développement d'une nouvelle Epic ou grosse feature"
---

# 🔀 Workflow : Feature Lifecycle
...
(rest of content)
