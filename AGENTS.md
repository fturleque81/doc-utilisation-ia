<!--
Fichier d'aide décrivant les agents recommandés pour ce dépôt.
Ce document est destiné aux contributeurs et aux intégrations Copilot/agents.
-->

# AGENTS — recommandations pour ce dépôt

But
- Fournir des agents et des scénarios d'utilisation pour accélérer les tâches de documentation (rédaction, relecture, synthèse).

ApplyTo
- Dossier principal de documentation : `docs/`

Agents suggérés
- `docs-editor` : agent pour rédiger et restructurer des pages Markdown dans `docs/`.
  - Tâches : proposer sommaires, adapter le niveau (débutant/intermédiaire), reformuler des sections.

- `docs-linter` : agent focalisé sur la relecture (orthographe, style, liens cassés, métadonnées).
  - Tâches : vérifier front-matter, s'assurer que les liens internes existent.

- `site-builder` : agent pour exécuter les commandes de build/déploiement.
  - Tâches : `pip install -r requirements.txt`, `mkdocs build`, `mkdocs gh-deploy`.

Exemples d'utilisation rapide
- "docs-editor: Améliore l'introduction de `docs/index.md` pour un public débutant."
- "docs-linter: Vérifie les liens relatifs dans `docs/bonnes-pratiques/` et propose les corrections." 

Prochaine étape
- Créer des prompts modèles dans `prompts/` pour ces agents (gabarits réutilisables).
