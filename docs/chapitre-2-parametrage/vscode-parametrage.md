# :material-microsoft-visual-studio-code: Paramétrage Complet — GitHub Copilot sur VS Code

<span class="badge-vscode">VS Code</span> <span class="badge-intermediate">Intermédiaire</span>

## Accès aux paramètres

### Via l'interface graphique (recommandé pour les débutants)

1. Ouvrez les paramètres : ++ctrl+comma++ (++cmd+comma++ sur macOS)
2. Tapez **"copilot"** dans la barre de recherche
3. Tous les paramètres Copilot apparaissent avec leur description

### Via le fichier JSON (recommandé pour les avancés)

1. Ouvrez la palette de commandes : ++ctrl+shift+p++
2. Tapez **"Open User Settings (JSON)"**
3. Modifiez directement le fichier `settings.json`

!!! tip "Settings UI vs JSON"
    Les deux méthodes modifient exactement les mêmes paramètres. L'interface UI est plus accessible, le JSON est plus rapide à copier-coller et à partager en équipe.

---

## Référence complète des paramètres

### `github.copilot.enable`

**Quoi :** Active ou désactive Copilot par type de langage. Vous pouvez activer globalement (`"*": true`) et désactiver sélectivement pour certains langages.

**Pourquoi :** Éviter les suggestions dans des fichiers sensibles (`.env`, mots de passe) ou dans des langages où Copilot est contre-productif.

**Exemple :**
```json
{
    "github.copilot.enable": {
        "*": true,
        "plaintext": false,
        "markdown": false,
        "dotenv": false,
        "sql": false
    }
}
```

**Avant (défaut)** : Copilot actif sur tous les fichiers, y compris `.env`
**Après** : Copilot désactivé sur les fichiers `.env`, markdown, et SQL

**Cas d'usage :** Équipe qui veut éviter que Copilot suggère des valeurs de variables d'environnement ou complete des clés API en dur dans le code.

---

### `github.copilot.editor.enableAutoCompletions`

**Quoi :** Active ou désactive les suggestions automatiques pendant la frappe. Si `false`, Copilot ne suggère rien spontanément — vous devez déclencher manuellement avec ++alt+backslash++.

**Pourquoi :** Les développeurs très expérimentés préfèrent souvent le mode manuel pour garder le contrôle complet sur le flux de travail.

```json
{
    "github.copilot.editor.enableAutoCompletions": true
}
```

| Valeur | Comportement |
|--------|-------------|
| `true` (défaut) | Suggestions automatiques |
| `false` | Mode manuel uniquement (++alt+backslash++ pour déclencher) |

---

### `github.copilot.editor.enableCodeActions`

**Quoi :** Active les actions de code Copilot dans l'éditeur (ampoule IA, suggestions contextuelles dans la gouttière).

**Pourquoi :** Ces actions permettent à Copilot de proposer des corrections, refactorings et explications directement sur les warnings et erreurs dans l'éditeur.

```json
{
    "github.copilot.editor.enableCodeActions": true
}
```

---

### `github.copilot.advanced`

**Quoi :** Paramètres avancés de Copilot regroupés dans un objet. Principalement utilisé pour le debug et les tweaks fin.

**Pourquoi :** Rarement nécessaire en usage normal, mais utile pour diagnostiquer des problèmes ou ajuster des comportements spécifiques.

```json
{
    "github.copilot.advanced": {
        "debug.overrideEngine": "",
        "debug.overrideLogLevels": {},
        "debug.useNodeFetcher": false,
        "listCount": 10,
        "inlineSuggestCount": 3
    }
}
```

| Sous-paramètre | Description |
|----------------|-------------|
| `listCount` | Nombre de suggestions dans le panneau "Copilot: Open Completions Panel" (défaut: 10) |
| `inlineSuggestCount` | Nombre de suggestions inline à précharger (défaut: 1) |

---

### `github.copilot.chat.localeOverride`

**Quoi :** Force la langue d'interface de Copilot Chat, indépendamment de la langue de VS Code.

**Pourquoi :** Si VS Code est en anglais mais que vous voulez interagir avec Chat en français (ou vice versa).

```json
{
    "github.copilot.chat.localeOverride": "fr"
}
```

**Valeurs courantes :** `"auto"` (défaut), `"fr"`, `"en"`, `"de"`, `"ja"`, `"zh-CN"`

---

### `github.copilot.chat.useProjectTemplates`

**Quoi :** Autorise Copilot Chat à utiliser les templates de projet GitHub pour les suggestions de structure de projet.

```json
{
    "github.copilot.chat.useProjectTemplates": true
}
```

---

### `github.copilot.renameSuggestions.triggerAutomatically`

**Quoi :** Active les suggestions de renommage automatiques de Copilot lorsque vous renommez un symbole.

**Pourquoi :** Copilot peut suggérer des noms cohérents avec le style du projet quand vous renommez une variable ou une fonction.

```json
{
    "github.copilot.renameSuggestions.triggerAutomatically": true
}
```

---

### `editor.inlineSuggest.enabled`

**Quoi :** Paramètre VS Code natif (pas Copilot-spécifique) qui active les suggestions inline en général. **Doit être `true`** pour que Copilot fonctionne.

**Pourquoi :** Si vous avez désactivé l'inlineSuggest globalement dans VS Code pour d'autres raisons, Copilot ne pourra pas afficher ses suggestions.

```json
{
    "editor.inlineSuggest.enabled": true
}
```

!!! danger "Paramètre critique"
    Si `editor.inlineSuggest.enabled` est `false`, Copilot ne fonctionnera pas même s'il est activé. C'est l'une des causes les plus fréquentes de "Copilot ne donne aucune suggestion".

---

### `editor.suggest.preview`

**Quoi :** Affiche un aperçu de la complétion sélectionnée directement dans l'éditeur avant acceptation.

```json
{
    "editor.suggest.preview": false
}
```

!!! info "Conflit potentiel"
    Si `editor.suggest.preview` et les suggestions Copilot sont activés simultanément, vous pouvez voir deux types de suggestions en même temps. Certains développeurs préfèrent désactiver `preview` pour ne voir que les suggestions Copilot.

---

## Profils de configuration

### 🟢 Profil Débutant

```json
{
    "github.copilot.enable": {
        "*": true
    },
    "github.copilot.editor.enableAutoCompletions": true,
    "github.copilot.editor.enableCodeActions": true,
    "github.copilot.chat.localeOverride": "fr",
    "github.copilot.renameSuggestions.triggerAutomatically": true,
    "editor.inlineSuggest.enabled": true
}
```

### 🔴 Profil Expert

```json
{
    "github.copilot.enable": {
        "*": true,
        "plaintext": false,
        "markdown": false,
        "dotenv": false,
        "sql": false,
        "yaml": false
    },
    "github.copilot.editor.enableAutoCompletions": false,
    "github.copilot.editor.enableCodeActions": true,
    "github.copilot.chat.localeOverride": "auto",
    "github.copilot.advanced": {
        "inlineSuggestCount": 1
    },
    "editor.inlineSuggest.enabled": true
}
```

### 👥 Profil Équipe

À placer dans `.vscode/settings.json` à la racine du projet (versionné avec Git) :

```json
{
    "github.copilot.enable": {
        "*": true,
        "dotenv": false,
        "plaintext": false
    },
    "github.copilot.editor.enableAutoCompletions": true,
    "github.copilot.chat.localeOverride": "fr",
    "editor.inlineSuggest.enabled": true,
    "github.copilot.editor.enableCodeActions": true
}
```

!!! warning "Ne jamais versionner des secrets"
    Le fichier `.vscode/settings.json` peut être versionné — mais assurez-vous qu'il ne contient **aucun token, clé API ou mot de passe**. Les paramètres Copilot sont sûrs à versionner.

### ⚡ Profil Minimaliste

```json
{
    "github.copilot.enable": {
        "*": true,
        "markdown": false,
        "plaintext": false,
        "yaml": false,
        "json": false,
        "xml": false,
        "dotenv": false,
        "sql": false,
        "shellscript": false
    },
    "github.copilot.editor.enableAutoCompletions": false,
    "github.copilot.editor.enableCodeActions": false,
    "github.copilot.renameSuggestions.triggerAutomatically": false,
    "editor.inlineSuggest.enabled": true
}
```

---

## Paramètres workspace spécifiques (.vscode/settings.json)

Pour surcharger les paramètres utilisateur uniquement pour un projet :

```json
// .vscode/settings.json (dans le projet)
{
    "github.copilot.enable": {
        "*": true,
        "sql": false
    }
}
```

Les settings du workspace **ont la priorité** sur les settings utilisateur. Utile pour désactiver Copilot sur un projet contenant des données sensibles.

---

## Pièges à éviter

!!! danger "Erreurs de configuration courantes"

    **1. `editor.inlineSuggest.enabled` à `false`**
    Copilot ne peut pas afficher de suggestions.
    ✅ Vérifiez ce paramètre en premier si vous n'avez aucune suggestion.

    **2. Copilot désactivé pour un langage sans s'en souvenir**
    Vous ouvrez un fichier Python, aucune suggestion → Copilot est désactivé pour `"python"` dans `github.copilot.enable`.
    ✅ Vérifiez les langages dans `github.copilot.enable`.

    **3. `settings.json` avec erreur de syntaxe JSON**
    VS Code cesse de charger les settings si le JSON est invalide.
    ✅ VS Code affiche une erreur en bas → corrigez la syntaxe JSON (accolades, virgules).

    **4. Settings workspace qui écrasent les settings utilisateur**
    Un fichier `.vscode/settings.json` dans un projet peut désactiver Copilot uniquement dans ce projet.
    ✅ Vérifiez s'il existe un `.vscode/settings.json` avec des paramètres Copilot.

---

## Prochaines étapes

- [Comparaison des paramètres](comparaison-parametres.md) — IntelliJ vs VS Code côte à côte
- [Contexte projet VS Code](../chapitre-3-contexte/vscode-contexte.md) — Fichiers `.instructions.md`, `.copilotignore`
- [Instructions & Personnalisation](../chapitre-3-contexte/instructions.md) — Aller plus loin avec les instructions Copilot
