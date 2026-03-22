# Conventions de Structure — Documentation IA

## Arborescence et nommage

```
docs/
├── index.md                             ← Hero banner, page d'accueil
├── chapitre-N-slug/                     ← N = numéro (1-6+), slug = kebab-case
│   ├── index.md                         ← Intro du chapitre (obligatoire)
│   ├── page-de-contenu.md               ← Pages thématiques
│   ├── comparaison.md                   ← Pattern: comparaison IntelliJ / VS Code
│   ├── intellij/                        ← Sous-dossier si contenu IDE volumineux
│   │   ├── tutoriel.md
│   │   └── reference.md
│   └── vscode/
│       ├── tutoriel.md
│       └── reference.md
└── appendices/
    ├── faq.md
    ├── raccourcis-clavier.md
    ├── ressources-externes.md
    └── templates-configuration.md
```

## Règles mkdocs.yml (nav)

```yaml
nav:
  - Accueil: index.md
  - "Titre du Chapitre":           # Guillemets si accent
    - Introduction: chapitre-N-slug/index.md
    - "Page de contenu": chapitre-N-slug/page.md
    - "IntelliJ IDEA":
      - "Tutoriel pas à pas": chapitre-N-slug/intellij/tutoriel.md
    - "Visual Studio Code":
      - "Tutoriel pas à pas": chapitre-N-slug/vscode/tutoriel.md
    - "Comparaison": chapitre-N-slug/comparaison.md  # Toujours en dernier
```

## Structure d'une page standard

```markdown
# Titre de la Page

<span class="badge-beginner">Débutant</span> <span class="badge-vscode">VS Code</span>

Paragraphe d'introduction : 2-3 phrases décrivant ce que cette page explique.

---

## Première section majeure

Contenu...

### Sous-section si nécessaire

...

!!! tip "Astuce pratique"
    Conseil actionnable en lien direct avec la section.

---

## Deuxième section (avec comparaison IDE)

=== "IntelliJ IDEA"
    Spécificités IntelliJ...

    ```java
    // Exemple de code IntelliJ
    ```

=== "Visual Studio Code"
    Spécificités VS Code...

    ```typescript
    // Exemple de code VS Code
    ```

---

## Résumé

- Point clé 1
- Point clé 2
- Point clé 3
```

## Chapitres existants

| N° | Dossier | Contenu |
|----|---------|---------|
| 1 | `chapitre-1-installation` | Installation Copilot par IDE |
| 2 | `chapitre-2-parametrage` | Réglages et paramètres |
| 3 | `chapitre-3-contexte` | Personnalisation, instructions, agents, prompts, skills |
| 4 | `chapitre-4-bonnes-pratiques` | Performance, sécurité, productivité |
| 5 | `chapitre-5-troubleshooting` | Diagnostic, problèmes courants |
| 6 | `chapitre-6-cas-usage` | Java, Python, Node.js/React |

## Conventions de labels dans la nav

| Type de page | Label |
|---|---|
| Index de chapitre | "Introduction" |
| Page thématique | Nom explicite en français |
| Page IntelliJ seule | "IntelliJ — [Sujet]" |
| Page VS Code seule | "VS Code — [Sujet]" |
| Tutoriel | "Tutoriel pas à pas" |
| Référence rapide | "Guide de référence" |
| Comparaison | "Comparaison IntelliJ / VS Code" |
