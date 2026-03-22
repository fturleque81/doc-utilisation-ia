---
name: doc-writer
description: "Rédiger, modifier ou enrichir des pages de documentation MkDocs Material pour ce projet GitHub Copilot. Utiliser pour : créer une nouvelle page, améliorer une page existante, ajouter des exemples, structurer du contenu technique en français."
argument-hint: "Sujet à documenter, page cible, ou amélioration demandée"
---

# Skill : Rédacteur de Documentation

## Objectif

Créer ou améliorer des pages de documentation MkDocs Material en français, conformes aux conventions de ce projet.

## Quand l'utiliser

- Créer une nouvelle page de documentation sur un sujet lié à GitHub Copilot
- Enrichir une page existante avec des exemples, admonitions, ou sections manquantes
- Restructurer du contenu mal organisé
- Ajouter de la documentation sur une fonctionnalité récente de Copilot

## Procédure

### 1. Contextualiser la demande

Avant d'écrire, lire :
- `mkdocs.yml` — pour comprendre la structure de navigation existante
- Le fichier `index.md` du chapitre concerné — pour le ton et la portée
- Une page similaire du même chapitre — comme modèle de style

### 2. Rédiger le contenu

Appliquer les conventions de structure et de syntaxe décrites dans les références :
- [Conventions de structure](./references/structure.md)
- [Syntaxe MkDocs Material](./references/mkdocs-syntax.md)
- [Exemples de patterns](./references/patterns.md)

### 3. Mettre à jour la navigation

Toujours ajouter la nouvelle page dans `mkdocs.yml` sous la bonne section `nav:`.

### 4. Valider

Confirmer que la page est bien formée : H1 présent, badges en place, admonitions correctement indentées, onglets cohérents, liens valides.

## Contraintes

- **Français obligatoire** — aucune phrase en anglais dans le contenu (sauf termes techniques non traduisibles)
- **MkDocs Material** — utiliser uniquement la syntaxe supportée par les extensions activées
- **Ne pas dupliquer** — vérifier qu'une page similaire n'existe pas déjà avant de créer
- **mkdocs.yml** — toujours mettre à jour la nav après création d'une page
