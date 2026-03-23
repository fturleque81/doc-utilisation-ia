# Screenshot Capture Template — IntelliJ IDEA

> Template pour captureurs de screenshots — IntelliJ IDEA

---

## Pre-Capture Checklist

- [ ] IntelliJ IDEA version 2024.1+ installed
- [ ] GitHub Copilot extension installed and authenticated
- [ ] Project open with minimal workspace (1-2 Java files only)
- [ ] IDE window maximized to 1920×1080
- [ ] All notifications disabled
- [ ] Display scale at 100% (no zoom)
- [ ] Thème: Darcula (défaut)

---

## Installation Screenshots

### intellij-marketplace-01.png

#### Goal

Show GitHub Copilot in Marketplace

#### Steps

1. Open Settings → Plugins
2. Search "GitHub Copilot"
3. Screenshot the search result card with Install button visible
4. Crop to show: Search box + extension card (name, description, Install button)

#### Key Details
- ✅ Search box shows "GitHub Copilot" text
- ✅ Extension card visible with icon
- ✅ Install button prominent
- ✅ Description/rating visible

---

### intellij-install-dialog-01.png

#### Goal

Show installation progress dialog

#### Steps

1. Click Install button
2. Wait for dialog to appear
3. Screenshot the installation dialog
4. Crop to show: Dialog title + progress + buttons

#### Key Details

- ✅ Dialog title "Installing GitHub Copilot"
- ✅ Progress indicator visible
- ✅ Cancel/OK buttons visible
- ✅ Version number visible if shown

---

### intellij-restart-prompt-01.png

#### Goal

Show restart requirement prompt

#### Steps

1. Wait for installation to complete
2. Screenshot restart prompt dialog
3. Crop to show: Prompt text + Restart/Cancel buttons

#### Key Details
- ✅ Prompt text "IDE restart required"
- ✅ Restart button (primary) prominent
- ✅ Cancel button visible
- ✅ Explanation text visible

---

## Settings Screenshots

### intellij-settings-copilot-01.png

#### Goal

Show Copilot settings panel

#### Steps

1. Open Settings → Tools → GitHub Copilot
2. Expand all sections
3. Screenshot full settings panel
4. Crop to show: All toggle options + explanations

#### Key Details

- ✅ "Enable inline suggestions" toggle visible
- ✅ "Chat enabled" toggle visible
- ✅ Organization settings if applicable
- ✅ Left sidebar "GitHub Copilot" item highlighted

---

### intellij-auth-login-01.png

#### Goal

Show authentication dialog

#### Steps

1. Open Settings → Tools → GitHub Copilot
2. Click "Sign In" or "Login" button (if logged-out state)
3. Screenshot the Device Flow dialog
4. Crop to show: Instructions + device code + link

#### Key Details
- ✅ "Authenticate with GitHub" title visible
- ✅ Device code visible (can be fake: XXXX-XXXX)
- ✅ Link to github.com/login/device visible
- ✅ Instructions text clear

---

### intellij-inline-settings-01.png

#### Goal

Show inline suggestions toggle OFF/ON

#### Steps

1. Open Settings → Tools → GitHub Copilot
2. Find "Enable inline suggestions" toggle
3. Screenshot with toggle in ON position
4. Crop to show: Toggle + label + description

#### Key Details

- ✅ Toggle switch clearly visible (blue = ON)
- ✅ Label "Enable inline suggestions" visible
- ✅ Description text visible
- ✅ Other settings visible for context

---

## Features Screenshots

### intellij-inline-completion-01.png

#### Goal

Show inline suggestion preview (grayed out)

#### Steps

1. Open a Java file (or Kotlin)
2. Start typing a method call: `public String get`
3. Wait for Copilot suggestion (gray text)
4. Screenshot without accepting
5. Crop to show: Code + grayed suggestion

#### Key Details
- ✅ Typed code visible (e.g., `public String get`)
- ✅ Suggestion in gray text (e.g., `User()` or similar)
- ✅ Cursor at end of typed text
- ✅ Line number visible

---

### intellij-inline-accept-01.png

#### Goal

Show suggestion acceptance (Tab key)

#### Steps

1. From previous screenshot state
2. Show Copilot suggestion still visible
3. Add visual indicator or tooltip showing "Press Tab to accept"
4. Screenshot the acceptance moment
5. Crop to show: Code + suggestion + Tab hint

#### Key Details

- ✅ Suggestion visible in gray
- ✅ Tab key label/indicator visible
- ✅ Cursor ready to accept
- ✅ Context clear

---

### intellij-chat-panel-01.png

#### Goal

Show Chat panel open in sidebar

#### Steps

1. Open Chat panel (Ctrl+Alt+I or menu)
2. Ensure chat is visible on right sidebar
3. Type example question: "How do I create a Spring Boot REST API?"
4. Screenshot with chat panel visible
5. Crop to show: Chat input + message history + sidebar

#### Key Details
- ✅ Chat panel open (right sidebar)
- ✅ Input field visible at bottom
- ✅ Message history (at least 1 message pair)
- ✅ Action buttons visible

---

### intellij-chat-context-01.png
**Goal**: Show chat with file context attached

**Steps**:
1. Open chat panel
2. Select a code file (Java class)
3. Right-click → "Ask Copilot about this file"
4. Chat opens with file context
5. Screenshot showing context indicator
6. Crop to show: Chat + file reference + context indicator

**Key Details**:
- ✅ Chat panel visible
- ✅ File context label/indicator visible (e.g., "Analyzing UserService.java")
- ✅ Message referencing file
- ✅ Input ready for follow-up

---

### intellij-action-menu-01.png
**Goal**: Show Copilot actions menu

**Steps**:
1. Open Command Palette (Cmd+Shift+A on Mac, Ctrl+Shift+A on Windows)
2. Type "GitHub Copilot"
3. Screenshot showing filtered actions
4. Crop to show: Search box + list of Copilot actions

**Key Details**:
- ✅ Command palette search text "GitHub Copilot"
- ✅ At least 3-4 actions visible (Chat, Explain, Generate, etc.)
- ✅ Action descriptions visible
- ✅ Keyboard shortcuts shown

---

## Troubleshooting Screenshots

### intellij-logs-location-01.png
**Goal**: Show where IDE logs are located

**Steps**:
1. Open Help → Show Log in Explorer
2. File explorer opens showing log directory
3. Screenshot showing: Log folder path + log files
4. Crop to show: Directory path + file list

**Key Details**:
- ✅ Directory path visible (e.g., `C:\Users\...\AppData\Local\JetBrains\IntelliJIdea2024.1\log`)
- ✅ Log files visible (idea.log, other .log files)
- ✅ File timestamps visible
- ✅ Folder hierarchy clear

---

### intellij-plugin-disabled-01.png
**Goal**: Show disabled plugin state

**Steps**:
1. Open Settings → Plugins
2. Find "GitHub Copilot"
3. Right-click → Disable or toggle off
4. Screenshot showing disabled state
5. Crop to show: Plugin card + disabled indicator

**Key Details**:
- ✅ Plugin name visible
- ✅ Disabled/enabled toggle visible (in OFF position)
- ✅ "X" or strikethrough indicating disabled state
- ✅ Re-enable button/option visible

---

## File Naming & Organization

```
intellij/
├── 01-installation/
│   ├── intellij-marketplace-01.png
│   ├── intellij-install-dialog-01.png
│   └── intellij-restart-prompt-01.png
├── 02-parametrage/
│   ├── intellij-settings-copilot-01.png
│   ├── intellij-auth-login-01.png
│   └── intellij-inline-settings-01.png
├── 03-features/
│   ├── intellij-inline-completion-01.png
│   ├── intellij-inline-accept-01.png
│   ├── intellij-chat-panel-01.png
│   ├── intellij-chat-context-01.png
│   └── intellij-action-menu-01.png
└── 04-troubleshooting/
    ├── intellij-logs-location-01.png
    └── intellij-plugin-disabled-01.png
```

---

## Optimization Tips

1. **Crop carefully**: Leave ~20px padding around main UI element
2. **Size**: Aim for 1400-1600px width (will scale down for web)
3. **Compression**: Use PNGCrush or ImageOptim to reduce file size
4. **Clarity**: 100% zoom on IDE; ensure text is readable
5. **Consistency**: All screenshots should use same IDE theme (Darcula)

