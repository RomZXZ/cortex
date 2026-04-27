---
name: crewai-evolution
version: 1.0.0
description: Roadmap et inspiration CrewAI pour l'evolution future de Cortex.
---

# Cortex x CrewAI - Feuille de Route

## Ou en est Cortex aujourd'hui

Cortex v1 est une **bibliotheque passive** : des fichiers `.md` que tu references manuellement dans tes prompts. C'est le **carburant** (les instructions), pas le **moteur** (l'execution).

## Ce qu'on peut apprendre de CrewAI

CrewAI est un framework Python d'orchestration multi-agents. Voici ce qu'on retient et comment Cortex peut evoluer :

### Concepts clefs de CrewAI

| Concept CrewAI | Equivalent Cortex | Ce qu'on peut s'inspirer |
|---------------|-------------------|-------------------------|
| **Agent** (role, goal, backstory) | Fichier agent `.md` (role, contexte, instructions) | On a deja ca |
| **Task** (description, expected_output) | Section "Format de Sortie" dans chaque agent | On a deja ca |
| **Crew** (agents + tasks + process) | `CORTEX.md` orchestrateur | A enrichir |
| **Flow** (state, routing, conditions) | Pas encore implemente | Phase 2-3 |
| **Agent Repository** (reutilisation cross-crew) | Cortex lui-meme ! | C'est notre concept de base |
| **Placeholders** (`{topic}`, `{context}`) | Variables dans les templates | A ajouter |

### Ce qu'on devrait emprunter (Phase 2)

#### 1. Variables / Placeholders dans les agents

Comme CrewAI avec `{topic}` :

```markdown
## Instructions
1. Analyse le marche pour **{project_name}**
2. Focus sur le domaine **{domain}** (cuisine, budget, jeux...)
3. Cible geographique : **{market}** (defaut: France)
```

#### 2. Dependances explicites (Flow)

```yaml
---
flow:
  after: market-researcher
  before: product-designer
  condition: "market-analysis.recommendation == 'GO'"
---
```

#### 3. State partage entre agents

Un fichier `project-state.md` qui se met a jour au fil du pipeline.

## Roadmap d'evolution

### Phase 1 : Docs-as-Agents (ACTUELLE)
- Agents = fichiers Markdown
- Orchestration = humaine (Romain choisit quel agent invoquer)
- Execution = dans l'IDE (Antigravity / Gemini CLI)
- **Valeur** : discipline, coherence, reutilisabilite

### Phase 2 : Smart Templates
- Ajouter des **placeholders** (`{project_name}`, `{domain}`)
- Ajouter un **project-state.md** auto-mis a jour
- Ajouter des **templates de sortie** pre-remplis
- Creer un script d'**init projet** qui setup Cortex + templates
- **Valeur** : moins de friction, plus de vitesse

### Phase 3 : Semi-Automation
- Script Python/Deno qui **lit le project-state** et suggere l'agent suivant
- Integration **Jules CLI** pour executer des agents en arriere-plan
- **GitHub Actions** qui invoque des agents sur certains evenements (PR, issue)
- **Valeur** : automatisation partielle, feedback loop automatique

### Phase 4 : Full CrewAI
- Migration vers un **vrai framework** (CrewAI, LangGraph, ou Google ADK)
- Les fichiers `.md` deviennent la **config YAML** des agents
- Orchestration **automatique** avec state management
- **Valeur** : pipeline de developpement produit entierement autonome

## Ressources et inspiration

- [CrewAI Documentation](https://docs.crewai.com/)
- [CrewAI Flows](https://docs.crewai.com/concepts/flows)
- [Google Agent Development Kit (ADK)](https://google.github.io/adk-docs/)
- [LangGraph](https://langchain-ai.github.io/langgraph/)
- [Anthropic Agent Patterns](https://www.anthropic.com/engineering/building-effective-agents)

## Projets similaires a surveiller

| Projet | Ce qu'il fait | Ce qu'on peut prendre |
|--------|-------------|----------------------|
| **pm-skills** | Skills de product management pour agents | Methodologies (RICE, JTBD, Impact Mapping) |
| **awesome-cursorrules** | Collection de .cursorrules | Patterns de prompts par domaine |
| **mdskills.ai** | Registry de SKILL.md reutilisables | Format de front matter, triggers |
| **CrewAI Agent Repository** | Agents reutilisables cross-projets | Pattern de composition d'agents |
