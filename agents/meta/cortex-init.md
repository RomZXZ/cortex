---
name: cortex-init
version: 1.1.0
phase: meta
type: component
description: >
  Initialise l'état d'un nouveau projet (cortex-state.md) pour 
  l'orchestration des workflows.
intent: >
  Créer la mémoire partagée du projet. Ce fichier d'état servira 
  de source de vérité pour tous les autres agents Cortex, stockant 
  les placeholders, l'avancement et les décisions clés.
triggers:
  - "init cortex"
  - "nouveau projet"
  - "setup"
  - "créer l'état"
dependencies: []
related_skills:
  - full-discovery
outputs:
  - cortex-state.md
estimated_time: 5 min
best_for:
  - "Tout nouveau projet démarrant avec Cortex"
---

# 📐 Cortex Init
...
(rest of content)
