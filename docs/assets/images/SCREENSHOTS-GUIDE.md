# Guide Capture Screenshots — GitHub Copilot Documentation

> **Pour les contributeurs** : Guide complet pour capturer et organiser les screenshots dans cette documentation.

---

## Conventions de Capture

### Résolution & Format
- **Résolution** : 1920×1080 (Full HD) — scale 100%
- **Format** : PNG (compression lossless)
- **Fond** : Thème par défaut IDE (pas de modifications UI)
- **Éléments visibles** : Toute toolbar, statusbar, panels relevant

### Nommage des Fichiers
```
{ide}-{feature}-{number}.png

Exemples:
- intellij-settings-01.png (Paramètres généraux)
- vscode-chat-panel-01.png (Chat panel Copilot)
- intellij-inline-completion-02.png (Suggestion inline)
- vscode-keybindings-01.png (Raccourcis configurés)
```

### Organisation Répertoires

```
docs/assets/images/
├── intellij/
│   ├── 01-installation/
│   ├── 02-parametrage/
│   ├── 03-features/
│   ├── 04-troubleshooting/
│   └── README.md (checklist)
└── vscode/
    ├── 01-installation/
    ├── 02-parametrage/
    ├── 03-features/
    ├── 04-troubleshooting/
    └── README.md (checklist)
```

---

## IntelliJ IDEA — Screenshots Prioritaires

### Installation (01-installation/)
| # | Screenshot | Description | État |
|----|-----------|-------------|------|
| 01 | intellij-marketplace-01.png | Recherche "GitHub Copilot" dans Marketplace | ![status-todo] |
| 02 | intellij-install-dialog-01.png | Dialog installation + bouton Install | ![status-todo] |
| 03 | intellij-restart-prompt-01.png | Prompt redémarrage IDE après install | ![status-todo] |

### Paramétrage (02-parametrage/)
| # | Screenshot | Description | État |
|----|-----------|-------------|------|
| 04 | intellij-settings-copilot-01.png | Settings → Tools → GitHub Copilot | ![status-todo] |
| 05 | intellij-auth-login-01.png | Dialog authentification GitHub | ![status-todo] |
| 06 | intellij-inline-settings-01.png | Inline suggestions ON/OFF toggle | ![status-todo] |

### Features (03-features/)
| # | Screenshot | Description | État |
|----|-----------|-------------|------|
| 07 | intellij-inline-completion-01.png | Suggestion inline grisée (hover) | ![status-todo] |
| 08 | intellij-inline-accept-01.png | Appui Tab pour accepter suggestion | ![status-todo] |
| 09 | intellij-chat-panel-01.png | Chat Copilot panel (sidebar droit) | ![status-todo] |
| 10 | intellij-chat-context-01.png | Contexte fichier transmis au chat | ![status-todo] |
| 11 | intellij-action-menu-01.png | Menu actions Copilot (Cmd+Shift+A) | ![status-todo] |

### Troubleshooting (04-troubleshooting/)
| # | Screenshot | Description | État |
|----|-----------|-------------|------|
| 12 | intellij-logs-location-01.png | Help → Show Log in Explorer | ![status-todo] |
| 13 | intellij-plugin-disabled-01.png | Extension désactivée (Settings) | ![status-todo] |

---

## Visual Studio Code — Screenshots Prioritaires

### Installation (01-installation/)
| # | Screenshot | Description | État |
|----|-----------|-------------|------|
| 01 | vscode-marketplace-01.png | Extension "GitHub Copilot" dans Marketplace | ![status-todo] |
| 02 | vscode-install-button-01.png | Bouton Install dans panel extension | ![status-todo] |
| 03 | vscode-auth-github-01.png | Authentification GitHub (Device Flow) | ![status-todo] |

### Paramétrage (02-parametrage/)
| # | Screenshot | Description | État |
|----|-----------|-------------|------|
| 04 | vscode-settings-search-01.png | Settings search "copilot" | ![status-todo] |
| 05 | vscode-copilot-settings-01.png | Copilot settings panel (Inline enable/disable) | ![status-todo] |
| 06 | vscode-keybindings-01.png | Keybindings pour Copilot (Ctrl+I, etc) | ![status-todo] |

### Features (03-features/)
| # | Screenshot | Description | État |
|----|-----------|-------------|------|
| 07 | vscode-inline-suggestion-01.png | Suggestion inline grisée (hover) | ![status-todo] |
| 08 | vscode-inline-accept-01.png | Appui Tab pour accepter suggestion | ![status-todo] |
| 09 | vscode-chat-sidebar-01.png | Chat Copilot sidebar panel | ![status-todo] |
| 10 | vscode-chat-input-01.png | Input chat avec /commands visibles | ![status-todo] |
| 11 | vscode-quick-fix-01.png | Lightbulb menu avec Copilot suggestions | ![status-todo] |

### Troubleshooting (04-troubleshooting/)
| # | Screenshot | Description | État |
|----|-----------|-------------|------|
| 12 | vscode-output-logs-01.png | Output → GitHub Copilot logs | ![status-todo] |
| 13 | vscode-extension-disabled-01.png | Extension disabled state | ![status-todo] |

---

## Procédure Capture

### Avant de capturer
1. Redémarrer IDE avec **profil défaut** (pas de custom themes)
2. **Maximiser** la fenêtre IDE (1920×1080 native si possible)
3. **Désactiver** les notifications persistantes
4. **Nettoyer** l'écran (fermer dialogs inutiles)

### Capture
- Utiliser **Capture de Windows** (Win+Shift+S) ou **Screenshot tool** IDE
- Recadrer si nécessaire (laisser context utile visible)
- **Exporter PNG** dans répertoire approprié

### Après capture
1. Renommer fichier selon convention `{ide}-{feature}-{number}.png`
2. Réduire taille PNG avec **ImageOptim** (Mac) ou **PNGCrush** (Windows)
3. Vérifier fichier dans le bon répertoire `/docs/assets/images/{ide}/`

---

## Intégration dans Documentation

### Syntaxe Markdown
```markdown
![Description courte](../../assets/images/intellij/intellij-settings-01.png)

Avec caption:
::: code-block markdown
![IntelliJ Settings Panel](../../assets/images/intellij/intellij-settings-01.png "Accès Settings → Tools → GitHub Copilot")
:::
```

### Validation Après Ajout
```bash
# Vérifier liens images
grep -r "!\[" docs/ | grep assets
```

---

## Checklist Complétude

- [ ] Tous fichiers répertoire `/intellij/` remplis
- [ ] Tous fichiers répertoire `/vscode/` remplis
- [ ] Nommage consistent `{ide}-{feature}-{number}.png`
- [ ] README.md dans chaque répertoire maintenu
- [ ] Tailles fichiers PNG optimisées (<500KB total)
- [ ] `mkdocs build` passe sans erreur

