# :simple-intellijidea: Paramétrage Complet — GitHub Copilot sur IntelliJ IDEA

<span class="badge-intellij">IntelliJ IDEA</span> <span class="badge-intermediate">Intermédiaire</span>

!!! info "Version 2025.3.4+"
    Cette documentation s'applique à **IntelliJ IDEA 2025.3.4 et versions récentes**. L'interface GitHub Copilot a été structurée avec les catégories : General, Chat, Completions, Customizations, Keymap, MCP, Network. Les paramètres des versions antérieures diffèrent.

## Accès aux paramètres

Trois façons d'accéder aux paramètres GitHub Copilot :

### 1️⃣ Via le menu principal

1. *File → Settings* (Windows/Linux) ou *IntelliJ IDEA → Preferences* (macOS)
   - Raccourci : ++ctrl+alt+s++ / ++cmd+comma++
2. Cherchez **GitHub Copilot** dans le panneau de gauche et expandez-le

### 2️⃣ Via l'icône dans la barre d'état

- Cliquez sur l'icône Copilot en bas à droite de la fenêtre
- Sélectionnez **"Open GitHub Copilot Settings"**

### 3️⃣ Via le menu Tools

- *Tools → GitHub Copilot → Settings...*

**Page d'accueil des paramètres :**

Une fois ouvert, vous voyez une page de catégorisation avec 6 catégories principales :

![Page d'accueil des paramètres GitHub Copilot](../assets/images/intellij/settings-copilot.png){ .doc-screenshot }
*Catégories des paramètres GitHub Copilot*

---

## Catégories des paramètres

Les paramètres GitHub Copilot sont organisés en 6 catégories principales. Explorez chaque section selon vos besoins :

### 🔧 General

**Authentification et gestion du plugin :**

- **GitHub Copilot account settings** — Gérez votre compte GitHub, authentification device code flow ou custom enterprise URI
- **Plugin updates** — Canal de mise à jour (Stable / Beta), vérification automatique
- **Send usage telemetry** — Optionnel ; permet à GitHub d'améliorer Copilot

![Section General - Authentification et gestion du plugin](../assets/images/intellij/general-copilot.png){ .doc-screenshot }
*Paramètres généraux : compte, mise à jour, authentification, télémétrie*

**Quand l'utiliser :** Lors de la première configuration, ou pour changer de compte GitHub.

---

### 💬 Chat

**Configuration des agents et du mode Chat :**

- **Enable Auto Model** — Sélectionne automatiquement le meilleur modèle pour votre requête
- **Natural Language** — Langue des interactions (français, anglais, etc.)
- **Diff View Mode** — Comment afficher les différences (inline, side-by-side)
- **Auto-accept Delay** — Temps avant acceptation automatique (0 = désactivé)
- **Auto-scroll to bottom** — Remonte automatiquement au dernier message
- **Show inline chat gutter icon** — Affiche l'icône du chat inline

![Section Chat > General - Configuration du mode Chat](../assets/images/intellij/chat-copilot-1.png){ .doc-screenshot }
*Paramètres généraux du Chat : auto-model, langue, affichage*

**Mode Agent (avancé) :**

- **Enable Agent mode** — Autorise Copilot à exécuter des commandes autonomes
- **Agent Max Requests** — Limite du nombre de requêtes par session (défaut 250)
- **Anthropic Thinking Budget Tokens** — Tokens alloués pour la réflexion étendue (défaut 1024)
- **Enable Custom Agent** — Active les agents personnalisés définis dans `AGENTS.md`
- **Enable Coding Agent** — Active les actions de génération/modification de code
- **Enable Subaagent** — Permet aux agents d'invoquer d'autres agents
- **Enable Skills** — Active les compétences spécialisées
- **Enable Code Review** — Active les revues de code assistées

![Section Chat > Agent - Configuration des agents](../assets/images/intellij/chat-copilot-2.png){ .doc-screenshot }
*Mode Agent : activation des agents personnalisés, skills, et code review*

**Auto-approve (expérimental) :**

- **Auto-approve** — Valide automatiquement les modifications suggérées
- **Terminal Auto-approve** — Approuve automatiquement les commandes du terminal
- **Edits Auto-approve** — Approuve les modifications de fichiers (avec patterns de confiance)
- **MCP Tool Auto-approve** — Approuve les appels d'outils MCP

![Section Chat > Auto-approve - Configuration de l'auto-approbation](../assets/images/intellij/chat-copilot-3.png){ .doc-screenshot }
*Auto-approve : automatisation des validations pour modifications, terminal, et fichiers*

**Quand l'utiliser :** Configuration personnalisée du Chat, activation des agents et de la revue de code.

---

### ✏️ Completions

**Configuration des complétions automatiques :**

- **Automatically show completions** — Active/désactive les suggestions pendant la frappe
- **Enable Next Edit Suggestions (NES)** — Propose la prochaine édition logique
- **Show IDE completions side-by-side** — Affiche les suggestions IDE et Copilot ensemble
- **Show multiple code suggestions** — Propose plusieurs variantes
- **Model for completions** — Sélectionne le modèle (GPT-4.1 Copilot par défaut)

![Section Completions - Configuration des suggestions automatiques](../assets/images/intellij/completions-copilot.png){ .doc-screenshot }
*Paramètres des complétions : auto-show, NES, affichage side-by-side, model*

**Langages :**

- **Enabled languages for completions** — Liste des langages supportés (Java, Python, C#, JavaScript, SQL, etc.)
  - Les langages cochés reçoivent les suggestions
  - Décochez pour désactiver Copilot sur des fichiers sensibles (`.env`, configuration critique)

**Quand l'utiliser :** Pour contrôler quand et où Copilot propose des suggestions.

---

### 📝 Customizations

**Instructions personnalisées pour guider Copilot :**

- **Copilot Instructions** — Directive globale (ex: "Utilise toujours les async/await en TypeScript")
- **Instruction Files** — Fichiers `.md` à appliquer par contexte (Workspace ou Global)
- **Git Commit Instructions** — Instructions pour les messages de commit
- **AGENTS.md** — Définit des agents personnalisés pour le Chat
- **CLAUDE.md** — Configuration spécifique du modèle Claude (expérimental)
- **Prompt Files** — Modèles réutilisables pour des tâches répétitives
- **Chat Agents** — Ajoute des agents personnalisés (Workspace level)

![Section Customizations - Instructions et configurations personnalisées](../assets/images/intellij/customizations-copilot.png){ .doc-screenshot }
*Customizations : instructions, AGENTS.md, CLAUDE.md, prompt files, chat agents*

**Quand l'utiliser :** Standardisation d'équipe, amélioration de la cohérence des suggestions.

---

### ⌨️ Keymap

**Raccourcis clavier GitHub Copilot :**

Vérifiez et personnalisez les raccourcis clavier en naviguant vers *Keymap → GitHub Copilot* (Windows/Linux) ou *Preferences → Keymap* (macOS).

**Raccourcis courants :**

| Action | Raccourci (défaut) | Customisable |
|--------|-------|----------------|
| Copilot Completion | ++alt+backslash++ | ✅ Oui |
| Copilot Chat | ++alt+l++ | ✅ Oui |
| Copilot Inline Chat | ++ctrl+k++ | ✅ Oui |

!!! warning "⚠️ Attention"
    Les raccourcis clavier **dépendent de votre configuration**. Si vous utilisez un clavier AZERTY ou avez personnalisé les raccourcis, les touches réelles peuvent différer. Vérifiez toujours sous *Keymap → GitHub Copilot*.

**Quand l'utiliser :** Lors de la configuration initiale ou pour adapter les raccourcis à votre workflow.

---

### 🔗 Model Context Protocol (MCP)

**Qu'est-ce que MCP ?**

Model Context Protocol est un **protocole standard** qui permet à Copilot d'intégrer et d'utiliser des **outils et des données externes** directement dans le Chat. Avec MCP, vous pouvez :

- Connecter des bases de données, APIs, et services externes
- Accéder à des documentations externalisées
- Exécuter des commandes système
- Interroger des outils comme SonarQube, Notion, Atlassian Jira, Stack Overflow, etc.

**Exemple :** Copilot peut interroger votre base de données pour optimiser une requête SQL, ou consulter la documentation Microsoft Learn directement dans le Chat.

**Installation de MCPs :**

Les serveurs MCP sont disponibles sur le **registre officiel GitHub** : https://github.com/modelcontextprotocol/servers

Les MCPs se configurent dans un fichier JSON (localisation selon l'IDE).

**Types de connexion MCP :**

| Type | Description | Exemple |
|------|-------------|---------|
| **stdio** | Communication locale via ligne de commande | npx @upstash/context7-mcp, uvx markitdown-mcp |
| **http** | Communication HTTP à distance | Services cloud (Notion, Jira, SonarQube) |
| **docker** | Exécution containerisée | SonarQube via Docker |

**MCPs officiellement disponibles :**

- **Context7** (Upstash) — Contexte et recherche étendue
- **Markitdown** (Microsoft) — Conversion de documents
- **Notion MCP** (Makenotion) — Accès aux bases Notion
- **Desktop Commander** — Contrôle du système de fichiers
- **Dependency Management** (Sonatype) — Gestion des dépendances Maven/NPM
- **SonarQube** — Analyse de qualité de code
- **Microsoft Docs** — Documentation officielle Microsoft
- **Stackoverflow MCP** — Recherche programmée Stack Overflow
- **Atlassian MCP** — Intégrations Jira, Confluence
- **DBHub** (Bytebase) — Requêtes et gestion bases de données
- **ContextStream** — Intégration de streams de contenu
- **Guru** — Base de connaissance Guru
- Et bien d'autres...

**Quand l'utiliser :** Pour des workflows spécialisés nécessitant l'intégration directe au Chat (configuration avancée).

**Ressources utiles :**
- [Registry GitHub MCP](https://github.com/modelcontextprotocol/servers) — Tous les serveurs disponibles
- Documentation officielle MCP — Pour configuration détaillée

---

### 🌐 Network

**Paramètres réseau et proxy :**

Configuration des connexions réseau, proxy, et certificats SSL (rarement nécessaire sauf en entreprise).

**Quand l'utiliser :** Environnements d'entreprise avec proxy obligatoire.



## Profils de configuration recommandés

Démarrez avec l'un de ces profils et préfinalisez-le selon vos préférences :

### 🟢 Profil Débutant

Pour ceux qui découvrent Copilot et veulent un maximum d'aide :

**Completions :**
```
✅ Automatically show completions : Activé
✅ Enable Next Edit Suggestions : Activé
✅ Show IDE completions side-by-side : Activé
✅ Model : GPT-4.1 Copilot
✅ Enabled languages : Tous (ou au moins votre langage principal)
```

**Chat :**
```
✅ Enable Auto Model : Activé
✅ Enable Coding Agent : Activé
✅ Enable Skills : Activé
```

**Customizations :**
```
⚠️  Copilot Instructions : À personnaliser selon vos préférences
```

### 🔴 Profil Expert

Pour les développeurs expérimentés qui veulent le contrôle granulaire :

**Completions :**
```
⚠️  Automatically show completions : Désactivé (déclenchement manuel avec alt+\)
✅ Enable Next Edit Suggestions : Désactivé
✅ Show multiple code suggestions : Désactivé
✅ Model : GPT-4.1 Copilot
✅ Enabled languages : Sélectifs (ex: Java, Python; désactiver .env, YAML config)
```

**Chat :**
```
✅ Enable Auto Model : Activé
✅ Enable Agent mode : Activé
✅ Enable Custom Agent : Activé
✅ Enable Code Review : Activé
✅ Auto-approve : Désactivé (approbation manuelle)
```

**Customizations :**
```
✅ Copilot Instructions : Personnalisées finement
✅ AGENTS.md : Configurés avec des agents personnalisés
✅ Prompt Files : Définis pour les tâches répétitives
```

### 👥 Profil Équipe

Pour standardiser la configuration dans une équipe :

**Completions :**
```
✅ Automatically show completions : Activé
✅ Show IDE completions side-by-side : Activé
✅ Enabled languages : Ceux du projet (désactiver .env, secrets.*, *credentials*)
```

**Chat :**
```
✅ Enable Auto Model : Activé
✅ Enable Coding Agent : Activé
✅ Enable Agent mode : Activé
```

**Customizations (IMPORTANT - Workspace level) :**
```
✅ Copilot Instructions : Instructions de l'équipe (ex: coding standards)
✅ AGENTS.md : Agents partagés
✅ CLAUDE.md : Configuration projet
✅ Prompt Files : Templates standardisés
```

!!! tip "Partage de settings en équipe"
    Committez les fichiers `.idea/copilot.xml` ou les fichiers `AGENTS.md` / `CLAUDE.md` dans votre repository pour synchroniser la config à toute l'équipe. Consultez la documentation JetBrains sur *File → Manage IDE Settings* pour les options de partage plus avancées.

---

## Configuration avancée

### Fichier de configuration XML

Pour les réglages non exposés dans l'UI, éditer directement le fichier XML :

**Localisation :**
- Windows : `%APPDATA%\JetBrains\<version>\options\github-copilot.xml`
- macOS : `~/Library/Application Support/JetBrains/<version>/options/github-copilot.xml`
- Linux : `~/.config/JetBrains/<version>/options/github-copilot.xml`

**Exemple :**

```xml
<application>
  <component name="CopilotApplicationSettings">
    <option name="isEnabled" value="true" />
    <option name="automaticCompletionsEnabled" value="true" />
    <option name="completionDelay" value="400" />
  </component>
</application>
```

!!! warning "⚠️ Édition manuelle"
    Fermez IntelliJ avant de modifier ce fichier. Une syntaxe XML incorrecte peut corrompre les paramètres.

---

## Pièges à éviter

!!! danger "Erreurs de configuration courantes"

    **1. Oublier d'activer Agent mode pour utiliser les custom agents**
    Si vous définissez un `AGENTS.md` personnalisé mais n'activez pas *Chat → Enable Agent mode*, l'agent ne sera pas disponible.
    ✅ Vérifiez que *Enable Agent mode* est coché dans Chat.

    **2. Désactiver les langages sans vouloir**
    Dans Completions → Enabled languages, tous les langages doivent être cochés par défaut. Si vous en décrochez par erreur, les suggestions seront bloquées.
    ✅ Vérifiez que votre langage principal est coché.

    **3. Utiliser des instructions personnalisées conflictuelles**
    Si vous avez des instructions dans Copilot Instructions ET dans `CLAUDE.md`, elles peuvent entrer en conflit.
    ✅ Préférez `CLAUDE.md` pour les configurations projet (plus spécifiques).

    **4. Auto-approve trop agressif**
    Activer *Auto-approve* + *Edits Auto-approve* peut appliquer des modifications non vérifiées.
    ✅ En équipe, gardez Auto-approve désactivé ou très restrictif.

---

## Prochaines étapes

- [Contexte projet IntelliJ](../chapitre-3-contexte/intellij-contexte.md) — Optimiser le contexte pour de meilleures suggestions
- [Paramétrage VS Code](vscode-parametrage.md) — Pour comparer avec d'autres IDEs (documentation à venir pour 2025.x)
