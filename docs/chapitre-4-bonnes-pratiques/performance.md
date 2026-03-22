# Performance & Ressources

<span class="badge-beginner">Débutant</span>

## Impact de Copilot sur l'IDE

GitHub Copilot envoie du contexte à un serveur distant et reçoit des suggestions — ce processus consomme des ressources locales (CPU, RAM, réseau) et peut impacter les performances de l'IDE si mal configuré.

---

## Profil de consommation par IDE

| Ressource | IntelliJ (plugin) | VS Code (extension) | Notes |
|-----------|-------------------|---------------------|-------|
| RAM supplémentaire | +150–300 MB | +80–150 MB | Dépend du contexte ouvert |
| CPU (suggestions actives) | 5–15% | 3–10% | Pics lors de l'analyse PSI |
| CPU (inactif) | <1% | <1% | Background minimal |
| Latence réseau | 200–800 ms | 200–800 ms | Même API, même infrastructure |
| Bande passante | Faible (<1 MB/h) | Faible (<1 MB/h) | Texte compressé uniquement |

!!! info "IntelliJ consomme plus de RAM"
    L'analyse PSI (Programme Structure Interface) d'IntelliJ est plus approfondie que le parsing VS Code. Elle offre plus de contexte sémantique mais coûte plus en mémoire.

---

## Causes fréquentes de ralentissement

### 1. Grands fichiers ouverts

Copilot envoie le contenu des fichiers ouverts comme contexte. Un fichier de 5000+ lignes peut saturer la fenêtre de contexte et ralentir les suggestions.

**Solutions :**

1. **Fermer les onglets non utilisés** — c'est la mesure la plus efficace. Chaque onglet ouvert est du contexte supplémentaire envoyé à Copilot.

2. **Désactiver pour les types de fichiers peu utiles** :

```json
// .vscode/settings.json
{
    "github.copilot.enable": {
        "*": true,
        "markdown": false,
        "plaintext": false,
        "xml": false,
        "log": false
    }
}
```

3. Dans IntelliJ : **Settings → GitHub Copilot → Disabled for Languages** pour désactiver les langages peu utilisés activement.

### 2. Délai de suggestion trop bas

Un délai très court (< 200 ms) déclenche beaucoup de requêtes fréquentes, surtout sur les connexions lentes.

=== ":material-microsoft-visual-studio-code: VS Code"
    ```json
    // .vscode/settings.json
    {
        "editor.quickSuggestionsDelay": 300,
        "github.copilot.editor.enableAutoCompletions": true
    }
    ```
    Il n'y a pas de paramètre `delay` direct dans Copilot VS Code — la latence dépend de `quickSuggestionsDelay`.

=== ":simple-intellijidea: IntelliJ"
    **Settings → GitHub Copilot → Completion Delay (ms)**
    
    Valeur recommandée : **300–500 ms** pour un équilibre réactivité/performance.
    
    Valeur conservative : **700–1000 ms** si l'IDE rame.

### 3. Suggestions dans des fichiers non-code

Copilot peut s'activer dans des fichiers de configuration (JSON, YAML, XML) ou de documentation (Markdown). Ces suggestions sont souvent de faible valeur et consomment des ressources.

```json
// .vscode/settings.json — Désactiver pour les types non essentiels
{
    "github.copilot.enable": {
        "*": true,
        "markdown": false,
        "plaintext": false,
        "xml": false
    }
}
```

---

## Stratégies d'optimisation

### Désactivation contextuelle

**VS Code** — Via la barre de statut :
1. Cliquez sur l'icône Copilot dans la barre bleue en bas
2. **"Disable Completions"** → Globalement ou pour le langage courant

**IntelliJ** :
1. Icône Copilot dans la status bar en bas à droite
2. **"Disable GitHub Copilot completions"**

### Optimisation mémoire pour IntelliJ

Si IntelliJ est globalement lent avec Copilot actif :

1. **Help → Edit Custom VM Options**
2. Augmentez `-Xmx` (mémoire max JVM) :
   ```
   -Xmx4096m   # si vous avez 16 GB RAM
   -Xmx6144m   # si vous avez 32 GB RAM
   ```
3. Redémarrez IntelliJ

!!! tip "RAM recommandée pour IntelliJ + Copilot"
    Minimum confortable : **16 GB RAM** total. En dessous, des ralentissements sont normaux sur de gros projets.

### Réduire le contexte envoyé

Plus les fichiers ouverts sont nombreux et grands, plus le contexte est lourd. Stratégies pratiques :

| Action | Impact sur performance |
|--------|----------------------|
| Fermer les onglets non utilisés | Élevé — réduit le contexte |
| Fermer les projets secondaires | Élevé (IntelliJ multi-projets) |
| Utiliser `.copilotignore` | Moyen — exclut les fichiers |
| Travailler par modules | Moyen — moins de fichiers actifs |

### Mode hors-ligne pour les sessions intensives

Si vous travaillez sur une nouvelle fonctionnalité et avez besoin de concentration maximale sans interruption de l'IDE, désactivez temporairement Copilot :

=== ":material-microsoft-visual-studio-code: VS Code"
    ++ctrl+shift+p++ → `GitHub Copilot: Disable Completions`
    
    Ou ++ctrl+shift+p++ → `GitHub Copilot: Toggle Completions`

=== ":simple-intellijidea: IntelliJ"
    Clic sur l'icône Copilot dans la status bar → **Disable GitHub Copilot**

---

## Surveillance de la performance

### VS Code — Outils de diagnostic

```
Help → Developer Tools (F12) → Performance tab
```

Ou dans le terminal :
```bash
# Code --prof lance VS Code en mode profilage
code --prof
```

Vérifiez dans **Output** (++ctrl+shift+u++) → sélectionnez **GitHub Copilot** dans le dropdown pour voir les logs de l'extension.

### IntelliJ — Diagnostics

```
Help → Diagnostics Tools → Record Freezes
Help → Show Log in Explorer    # Ouvre idea.log
```

Dans `idea.log`, cherchez les lignes contenant `Copilot` pour identifier les erreurs ou la latence.

---

## Configuration recommandée selon le contexte

| Contexte | IntelliJ | VS Code | Notes |
|----------|----------|---------|-------|
| Machine puissante (32 GB+) | Tout actif | Tout actif | Expérience optimale |
| Machine standard (16 GB) | Delay 400ms | Defaults | Bon équilibre |
| Machine modeste (8 GB) | Delay 700ms, auto-disabled on large files | Désactiver pour markdown/yaml | Activer à la demande |
| Réseau lent | Delay 600ms | Delay via quickSuggestionDelay | Réduire la fréquence |
| CI/CD ou build actif | Suspendre Copilot | Suspendre Copilot | Libérer CPU/RAM |

---

## En résumé

- **Fermer les onglets inutilisés** est la mesure de performance la plus simple et la plus efficace
- **16 GB RAM minimum** recommandé pour IntelliJ + Copilot sur des projets moyens
- **Désactiver pour markdown/plaintext/xml** réduit les requêtes inutiles sans impact sur le workflow
- **Augmenter `-Xmx`** dans les VM Options IntelliJ si vous avez plus de 16 GB RAM disponibles
- Consultez le **tableau de configuration** selon votre profil machine pour trouver le bon équilibre

---

## Prochaines étapes

- [Troubleshooting](../chapitre-5-troubleshooting/index.md) — Résoudre les problèmes courants
- [Cas d'Usage](../chapitre-6-cas-usage/index.md) — Exemples par technologie
