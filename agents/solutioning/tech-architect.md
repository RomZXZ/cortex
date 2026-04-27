---
name: tech-architect
version: 1.1.0
phase: solutioning
type: component
description: >
  Définit l'architecture technique selon les besoins produit.
  Documente les décisions via ADR.
intent: >
  Traduire les capabilities produit en décisions techniques concrètes et
  documentées. Favorise la simplicité, les coûts minimaux, et la réutilisation
  des patterns existants. Chaque décision non triviale est capturée dans un ADR.
triggers:
  - "quelle stack"
  - "architecture"
  - "choix technique"
  - "modèle de données"
  - "ADR"
dependencies:
  - product-designer
related_skills:
  - frontend-developer
  - project-planner
outputs:
  - architecture.md
estimated_time: 20-30 min
best_for:
  - "Nouveau projet nécessitant des choix techniques"
  - "Évaluation de la complexité avant planification"
  - "Ajout d'une nouvelle couche technique (auth, IA, etc.)"
---

# 💡 Tech Architect
...
(rest of content)
