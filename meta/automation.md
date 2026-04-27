# 🤖 Automatisation & Travail de Fond (Jules)

Ce guide définit comment utiliser **Jules** (ou tout agent asynchrone) pour les tâches lentes, répétitives ou qui nécessitent un travail de fond sans bloquer ta session de chat interactive.

## Pourquoi déléguer à Jules ?

Certaines tâches prennent du temps (analyse de 50 fichiers, exécution de tests, refactoring complet). Au lieu d'attendre devant ton écran, tu peux déléguer ces tâches à Jules.

## 🛠️ Catalogue de Workflows Jules

### 🔍 Le "Deep Review"
**Quand** : Avant de merger une PR complexe.
**Commande** : `jules run "En utilisant agents/build/code-reviewer.md, fais une revue complète de la branche feature/xyz et propose des correctifs."`

### 🧪 Le "QA Stress Test"
**Quand** : Après un gros changement UI ou logique.
**Commande** : `jules run "En utilisant agents/test/qa-engineer.md, teste tous les scénarios de l'app et génère un test-report.md détaillé."`

### 📓 La "Mise à jour Documentaire"
**Quand** : Quand le code a beaucoup évolué et que les docs sont en retard.
**Commande** : `jules run "Analyse les derniers commits et mets à jour CORTEX.md, README.md et meta/learnings.md."`

### 🌱 Le "Curateur de Connaissances"
**Quand** : Pour traiter les leçons apprises.
**Commande** : `jules run "Utilise agents/meta/knowledge-curator.md pour traiter toutes les entrées de l'inbox dans meta/learnings.md."`

---

## ⏭️ Comment déléguer (Workflow)

1. **Identification** : L'assistant (moi) identifie une tâche "Jules-friendly" et te propose la commande.
2. **Lancement** : Tu copies-colles la commande dans ton terminal : `jules run "..."`.
3. **Notification** : Jules travaillera en arrière-plan et créera une PR ou un fichier de rapport quand il aura fini.
4. **Validation** : Tu reviens vers moi pour analyser le travail de Jules.

---

## ⚠️ Précautions
- Toujours vérifier que Jules travaille sur une branche dédiée (via `github-manager`).
- Ne pas lancer deux tâches Jules conflictuelles sur le même fichier.
