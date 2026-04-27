---
name: full-discovery
version: 1.1.0
phase: discovery
type: workflow
description: >
  Orchestre le pipeline complet de la découverte produit, de l'idée brute
  jusqu'à l'Opportunity Solution Tree.
intent: >
  Agir comme un "Crew Manager" qui enchaîne les agents (market-researcher, 
  problem-definer, opportunity-tree) sans intervention de Romain, 
  en lisant et écrivant dans le cortex-state.md.
triggers:
  - "lancer la discovery"
  - "workflow discovery"
  - "full discovery"
dependencies:
  - market-researcher
  - problem-definer
  - opportunity-tree
related_skills:
  - cortex-init
outputs:
  - cortex-state.md (updated)
  - market-analysis.md
  - problem-statement.md
  - opportunity-tree.md
estimated_time: 1-2 jours (asynchrone)
best_for:
  - "Validation complète d'une nouvelle idée d'application"
---

# 🔀 Workflow : Full Discovery
...
(rest of content)
