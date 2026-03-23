# Screenshot Capture Template — Visual Studio Code

> Template pour captureurs de screenshots — VS Code

---

## Pre-Capture Checklist

- [ ] VS Code latest version installed
- [ ] GitHub Copilot extension installed and authenticated
- [ ] Workspace open with minimal files (1-2 JS/TS files only)
- [ ] VS Code window maximized to 1920×1080
- [ ] All notifications disabled
- [ ] Display scale at 100% (no zoom)
- [ ] Theme: Dark (défaut)
- [ ] Font size: Default (14px)

---

## Installation Screenshots

### vscode-marketplace-01.png

#### Goal

Show GitHub Copilot in Extensions Marketplace

#### Steps

1. Open Extensions view (Ctrl+Shift+X)
2. Search "GitHub Copilot"
3. Screenshot the extension card
4. Crop to show: Search box + extension card + Install button

#### Key Details
- ✅ Search box shows "GitHub Copilot"
- ✅ Extension icon visible (GitHub Copilot logo)
- ✅ Extension name "GitHub Copilot" in title
- ✅ Description visible (first line)
- ✅ Install button (blue) prominent
- ✅ Rating/downloads visible if shown

---

### vscode-install-button-01.png

#### Goal

Show Install button action state

#### Steps

1. From marketplace extension card
2. Show cursor hovering over Install button OR
3. Show Install button in hovered/active state
4. Crop to show: Extension card + Install button state

#### Key Details
- ✅ Install button visible (blue, hovered or highlighted)
- ✅ Extension name and icon visible
- ✅ Button text "Install" clearly readable
- ✅ Version number visible

---

### vscode-auth-github-01.png

#### Goal

Show GitHub authentication (Device Flow)

#### Steps

1. Click Install
2. Wait for authentication prompt
3. Device Flow browser/dialog opens
4. Screenshot showing: Device code + GitHub link
5. Crop to show: Auth prompt + device code + instructions

#### Key Details
- ✅ "Sign in with GitHub" title visible
- ✅ Device code visible (8-character code like XXXX-XXXX)
- ✅ Link "https://github.com/login/device" visible
- ✅ Instructions text visible
- ✅ "Authorize" button visible

---

## Settings Screenshots

### vscode-settings-search-01.png

#### Goal

Show Settings search for Copilot options

#### Steps

1. Open Settings (Ctrl+,)
2. Search "copilot"
3. Screenshot showing search results
4. Crop to show: Search box + Copilot settings list

#### Key Details
- ✅ Settings search box with "copilot" text
- ✅ Multiple copilot settings visible in results
- ✅ "Copilot" appears in setting names
- ✅ Setting descriptions visible

---

### vscode-copilot-settings-01.png

#### Goal

Show Copilot settings with toggles

#### Steps

1. In Settings, search "copilot"
2. Expand main Copilot settings section
3. Screenshot showing toggle options
4. Crop to show: All toggles + descriptions

#### Key Details

- ✅ "Enable Copilot" toggle visible (ON position, blue)
- ✅ "Enable Inline Suggestions" toggle visible
- ✅ "Enable Chat" toggle visible
- ✅ Toggle descriptions visible
- ✅ Setting knobs/toggles clearly shown

---

### vscode-keybindings-01.png

#### Goal

Show Copilot keyboard shortcuts

#### Steps

1. Open Keyboard Shortcuts (Ctrl+K Ctrl+S)
2. Search "copilot"
3. Screenshot showing keybindings
4. Crop to show: Keybindings list with shortcuts

#### Key Details
- ✅ Search box shows "copilot"
- ✅ At least 3-4 keybindings visible:
  - Ctrl+I for Chat (or Cmd+I on Mac)
  - Tab for Accept Suggestion
  - Esc for Dismiss
- ✅ Command names visible (e.g., "copilot.openSymbolFromReferences")
- ✅ Shortcut keys clearly shown

---

## Features Screenshots

### vscode-inline-suggestion-01.png

#### Goal

Show inline suggestion (grayed out)

#### Steps

1. Open a JavaScript/TypeScript file
2. Start typing: `function getUserName`
3. Wait for Copilot to show gray suggestion
4. Screenshot WITHOUT accepting (Esc first if needed)
5. Crop to show: Code + gray suggestion text

#### Key Details
- ✅ Typed code visible (e.g., `function getUserName`)
- ✅ Suggestion in gray/dimmed text (e.g., `() {`)
- ✅ Cursor at end of typed text
- ✅ Line number visible

---

### vscode-inline-accept-01.png

#### Goal

Show suggestion acceptance (Tab key)

#### Steps

1. From previous state with suggestion visible
2. Show suggestion with Tab key hint/label visible
3. Screenshot showing acceptance UI
4. Crop to show: Code + suggestion + Tab indicator

#### Key Details

- ✅ Suggestion visible in gray
- ✅ Tab key indicator/label visible (if VS Code shows it)
- ✅ Code context clear
- ✅ Cursor position clear

---

### vscode-chat-sidebar-01.png

#### Goal

Show Chat Copilot sidebar panel

#### Steps

1. Open Chat panel (Ctrl+I or Cmd+I on Mac)
2. Chat sidebar appears on right side
3. Type example question: "How do I fetch data in React?"
4. Screenshot with chat panel fully visible
5. Crop to show: Chat header + message area + input

#### Key Details
- ✅ Chat panel visible (right sidebar)
- ✅ "Copilot" title/header visible
- ✅ Chat message history visible (at least 2 messages: user + assistant)
- ✅ Input field at bottom visible
- ✅ Send button (arrow) visible

---

### vscode-chat-input-01.png

#### Goal

Show chat input with /commands visible

#### Steps

1. Chat panel open
2. Click in input field
3. Type "/" to show available commands
4. Screenshot showing command suggestions
5. Crop to show: Input field + command list (/explain, /fix, /generate, etc.)

#### Key Details
- ✅ Input field has focus (cursor visible)
- ✅ "/" character typed
- ✅ Command suggestions dropdown visible:
  - /explain
  - /fix
  - /generate
  - /doc
  - etc.
- ✅ Command descriptions visible

---

### vscode-quick-fix-01.png

#### Goal

Show Copilot in Quick Fix (lightbulb) menu

#### Steps

1. Open a file with code
2. Select some problematic code (or hover over error)
3. Lightbulb appears (or press Ctrl+.)
4. Screenshot showing lightbulb menu with Copilot options
5. Crop to show: Code + lightbulb menu + Copilot actions

#### Key Details
- ✅ Lightbulb icon visible (💡)
- ✅ Menu dropdown showing "Ask Copilot" or similar option
- ✅ Other quick fix actions visible (if applicable)
- ✅ Code context visible
- ✅ Line number visible

---

## Troubleshooting Screenshots

### vscode-output-logs-01.png

#### Goal

Show GitHub Copilot logs in Output panel

#### Steps

1. Open Output panel (View → Output or Ctrl+` then Output tab)
2. Select "GitHub Copilot" from dropdown
3. Screenshot showing log output
4. Crop to show: Output panel + log messages

#### Key Details
- ✅ Output dropdown shows "GitHub Copilot" selected
- ✅ Log messages visible (INFO, DEBUG, ERROR lines)
- ✅ Timestamps visible on log entries
- ✅ At least 3-4 log lines visible
- ✅ Message content readable

---

### vscode-extension-disabled-01.png

#### Goal

Show disabled extension state

#### Steps

1. Open Extensions (Ctrl+Shift+X)
2. Find GitHub Copilot
3. Click settings → Disable
4. Screenshot showing disabled badge
5. Crop to show: Extension card + disabled indicator

#### Key Details
- ✅ Extension card visible
- ✅ "Disabled" badge/label visible (often grayed out)
- ✅ "Enable" button visible (instead of "Uninstall")
- ✅ Extension icon/name visible
- ✅ Disabled state clear

---

## File Naming & Organization

```
vscode/
├── 01-installation/
│   ├── vscode-marketplace-01.png
│   ├── vscode-install-button-01.png
│   └── vscode-auth-github-01.png
├── 02-parametrage/
│   ├── vscode-settings-search-01.png
│   ├── vscode-copilot-settings-01.png
│   └── vscode-keybindings-01.png
├── 03-features/
│   ├── vscode-inline-suggestion-01.png
│   ├── vscode-inline-accept-01.png
│   ├── vscode-chat-sidebar-01.png
│   ├── vscode-chat-input-01.png
│   └── vscode-quick-fix-01.png
└── 04-troubleshooting/
    ├── vscode-output-logs-01.png
    └── vscode-extension-disabled-01.png
```

---

## Optimization Tips

1. **Crop carefully**: Leave ~30px padding around UI elements
2. **Size**: Aim for 1400-1600px width (scales down for web)
3. **Compression**: Use PNGCrush, ImageOptim, or TinyPNG
4. **Clarity**: Ensure text is readable at 80% scale
5. **Consistency**: All screenshots same theme (Dark mode), same font size
6. **Avoid**: Cursor, notifications, irrelevant toolbars

