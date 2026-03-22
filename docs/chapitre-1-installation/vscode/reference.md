# :material-microsoft-visual-studio-code: Guide de référence — GitHub Copilot sur VS Code

<span class="badge-vscode">VS Code</span> <span class="badge-intermediate">Intermédiaire</span>

## Présentation
Ce guide de référence rassemble toutes les informations techniques sur l'intégration de GitHub Copilot dans Visual Studio Code : localisation de `settings.json`, raccourcis clavier complets, extensions recommandées, et personnalisation des keybindings.

---

## Localisation du fichier settings.json

Le fichier `settings.json` contient tous les paramètres VS Code, y compris ceux de Copilot.

=== "Windows"

    ```
    %APPDATA%\Code\User\settings.json
    ```
    
    Chemin complet type :
    ```
    C:\Users\<username>\AppData\Roaming\Code\User\settings.json
    ```

=== "macOS"

    ```
    ~/Library/Application Support/Code/User/settings.json
    ```

=== "Linux"

    ```
    ~/.config/Code/User/settings.json
    ```

### Ouvrir settings.json directement

Méthodes d'accès rapide :

1. **Via la palette de commandes** : ++ctrl+shift+p++ → tapez *"Open User Settings (JSON)"*
2. **Via les paramètres UI** : ++ctrl+comma++ → icône `{}` en haut à droite
3. **Via le menu** : *File → Preferences → Settings* puis cliquez sur l'icône `{}` en haut à droite

!!! tip "Settings globaux vs Settings du workspace"
    - **User Settings** (`settings.json` dans le répertoire utilisateur) : s'appliquent à tous vos projets
    - **Workspace Settings** (`.vscode/settings.json` à la racine du projet) : s'appliquent uniquement au projet ouvert
    
    Les settings du workspace **ont la priorité** sur les settings utilisateur.

---

## Raccourcis clavier par défaut

### Raccourcis principaux — Suggestions inline

=== "Windows / Linux"

    | Action | Raccourci |
    |--------|-----------|
    | **Accepter la suggestion complète** | ++tab++ |
    | **Accepter mot par mot** | ++ctrl+right++ |
    | **Suggestion suivante** | ++alt+bracket-right++ |
    | **Suggestion précédente** | ++alt+bracket-left++ |
    | **Rejeter la suggestion** | ++escape++ |
    | **Déclencher manuellement** | ++alt+backslash++ |
    | **Ouvrir le panneau des 10 suggestions** | ++ctrl+enter++ |

=== "macOS"

    | Action | Raccourci |
    |--------|-----------|
    | **Accepter la suggestion complète** | ++tab++ |
    | **Accepter mot par mot** | ++option+right++ |
    | **Suggestion suivante** | ++option+bracket-right++ |
    | **Suggestion précédente** | ++option+bracket-left++ |
    | **Rejeter la suggestion** | ++escape++ |
    | **Déclencher manuellement** | ++option+backslash++ |
    | **Ouvrir le panneau des 10 suggestions** | ++ctrl+enter++ |

### Raccourcis Copilot Chat

=== "Windows / Linux"

    | Action | Raccourci |
    |--------|-----------|
    | **Ouvrir le panneau Chat** | ++ctrl+alt+i++ |
    | **Inline Chat (dans l'éditeur)** | ++ctrl+i++ |
    | **Quick Chat (fenêtre flottante)** | ++ctrl+shift+i++ |
    | **Expliquer le code sélectionné** | Clic droit → *Copilot → Explain This* |
    | **Générer des tests** | Clic droit → *Copilot → Generate Tests* |
    | **Corriger le code** | Clic droit → *Copilot → Fix This* |

=== "macOS"

    | Action | Raccourci |
    |--------|-----------|
    | **Ouvrir le panneau Chat** | ++cmd+alt+i++ |
    | **Inline Chat (dans l'éditeur)** | ++cmd+i++ |
    | **Quick Chat (fenêtre flottante)** | ++cmd+shift+i++ |
    | **Expliquer le code sélectionné** | Clic droit → *Copilot → Explain This* |

---

## Personnaliser les raccourcis (keybindings.json)

Pour modifier un raccourci Copilot :

1. Ouvrez le fichier keybindings : ++ctrl+shift+p++ → *"Open Keyboard Shortcuts (JSON)"*
2. Ajoutez une entrée au tableau JSON :

```json
[
  {
    "key": "ctrl+space",
    "command": "editor.action.inlineSuggest.trigger",
    "when": "editorTextFocus && !editorHasSelection"
  },
  {
    "key": "ctrl+tab",
    "command": "editor.action.inlineSuggest.acceptNextWord",
    "when": "inlineSuggestionVisible"
  }
]
```

### Identifiants des commandes Copilot utiles

| Commande | Identifiant |
|----------|-------------|
| Déclencher suggestion | `editor.action.inlineSuggest.trigger` |
| Accepter suggestion | `editor.action.inlineSuggest.commit` |
| Accepter mot suivant | `editor.action.inlineSuggest.acceptNextWord` |
| Suggestion suivante | `editor.action.inlineSuggest.showNext` |
| Suggestion précédente | `editor.action.inlineSuggest.showPrevious` |
| Rejeter suggestion | `editor.action.inlineSuggest.hide` |
| Ouvrir Chat | `workbench.panel.chat.view.copilot.focus` |
| Inline Chat | `inlineChat.start` |

---

## Extensions recommandées à installer avec Copilot

| Extension | Identifiant | Utilité |
|-----------|-------------|---------|
| **GitHub Copilot Chat** | `GitHub.copilot-chat` | Interface de chat avec Copilot *(indispensable)* |
| **GitHub Pull Requests** | `GitHub.vscode-pull-request-github` | Gestion des PR directement dans VS Code |
| **GitLens** | `eamodio.gitlens` | Historique Git enrichi — complémentaire à Copilot |
| **Error Lens** | `usernamehw.errorlens` | Affiche les erreurs inline — aide Copilot à cibler les corrections |
| **Auto Rename Tag** | `formulahendry.auto-rename-tag` | Complémente les suggestions HTML/JSX de Copilot |

!!! tip "Pack d'extensions"
    Vous pouvez créer un fichier `.vscode/extensions.json` dans votre projet pour recommander ces extensions à toute votre équipe :

    ```json
    {
        "recommendations": [
            "GitHub.copilot",
            "GitHub.copilot-chat",
            "GitHub.vscode-pull-request-github"
        ]
    }
    ```

---

## Exécution des paramètres Copilot dans settings.json

Exemple minimal d'un `settings.json` configuré pour Copilot :

```json
{
    "github.copilot.enable": {
        "*": true,
        "markdown": false,
        "plaintext": false
    },
    "github.copilot.editor.enableAutoCompletions": true,
    "github.copilot.chat.localeOverride": "fr"
}
```

Pour les paramètres complets avec explications détaillées, voir [Paramétrage VS Code](../../chapitre-2-parametrage/vscode-parametrage.md).

---

## Gestion des extensions

### Désactiver Copilot temporairement

- Cliquez sur l'icône Copilot dans la barre de statut (en bas)
- Sélectionnez "Disable Copilot" pour désactiver globalement ou pour le workspace courant

### Désactiver pour un langage spécifique

```json
{
    "github.copilot.enable": {
        "*": true,
        "sql": false,
        "markdown": false
    }
}
```

### Mettre à jour les extensions

VS Code met à jour automatiquement les extensions. Pour forcer une mise à jour manuelle :
1. Extensions panel → menu `...` → *"Check for Extension Updates"*
2. Ou : ++ctrl+shift+p++ → *"Extensions: Check for Extension Updates"*

