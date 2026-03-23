# Contributing Screenshots — Guidelines

> Guide complet pour capturer et contribuer des screenshots à la documentation

---

## 🎯 Scope

This document explains how to capture and contribute screenshots for the GitHub Copilot documentation (IntelliJ IDEA and VS Code).

**Target Audience**: Contributors, documentation maintainers, IDE power users

**Expected Effort**: 30-60 minutes total for all 26 screenshots

---

## 📋 Prerequisites

### System Requirements
- **IntelliJ IDEA** users:
  - Version 2024.1 or newer
  - GitHub Copilot extension installed
  - Authenticated with GitHub account
  
- **VS Code** users:
  - Latest version (1.85+)
  - GitHub Copilot extension installed
  - Authenticated with GitHub account

### Screen Setup
- Display: **1920×1080 minimum** (Full HD recommended)
- Scale: **100%** (no zoom/zoom-in)
- Display all extension features clearly

---

## 📸 Preparation Steps

### 1. Clean IDE Environment

Before capturing ANY screenshot:

```bash
# Option A: Create fresh workspace
# Create new empty project
# File → New → Project → Empty Project

# Option B: Use existing minimal project
# But close all unrelated files
# Keep only 1-2 sample files visible
```

**Why?** Clean environment = focused screenshots, no distraction

### 2. Verify Settings Consistency

**IntelliJ IDEA**:
- Theme: ☑ Darcula (Settings → Appearance → Theme)
- Font: ☑ JetBrains Mono, 14px (Settings → Editor → Font)
- All notifications disabled (Settings → Appearance → Notifications)

**VS Code**:
- Theme: ☑ Dark (Modern) (Settings → Theme)
- Font: ☑ Monospace/Fira Code, 14px
- Extensions sidebar visible by default (Cmd+Shift+X)

### 3. Test Copilot Features

Before capturing, verify:
- ☑ Inline suggestions working (type code snippet)
- ☑ Chat panel opens (Ctrl+Alt+I or Ctrl+I)
- ☑ Authentication valid (no "Sign In" prompts)

---

## 🎬 Capture Procedure

### Step-by-Step Workflow

1. **Select Template**
   - Open `CAPTURE-TEMPLATE.md` in your IDE repo
   - Choose one screenshot to capture (e.g., `intellij-marketplace-01.png`)

2. **Follow Instructions**
   - Read "Goal", "Steps", "Key Details" sections
   - Perform each step in your IDE
   - Do NOT deviate from steps

3. **Capture Screenshot**
   - **IntelliJ**: Help → Take Screenshot (built-in)
   - **VS Code**: `Win+Shift+S` or Screenshot tool
   - **Mac**: `Cmd+Shift+4` (then click area)

4. **Crop Image**
   - Use Screenshot Editor or external tool (Preview, GIMP)
   - Crop to focus on main UI element
   - Leave ~20-30px padding around element
   - Remove sensitive info (usernames, API Keys)

5. **Optimize File Size**
   - **Windows**: Use PNGCrush:
     ```powershell
     pngcrush -brute input.png output_optimized.png
     ```
   - **Mac**: Use ImageOptim (GUI)
   - **Online**: Use TinyPNG (tinypng.com)
   - Target: < 150 KB per file

6. **Name & Save**
   - Filename: `{ide}-{feature}-{number}.png`
   - Examples:
     - `intellij-marketplace-01.png`
     - `vscode-settings-search-01.png`
   - Save to correct subdirectory:
     - `docs/assets/images/intellij/01-installation/`
     - `docs/assets/images/vscode/02-parametrage/`

7. **Verify**
   - Open file in image viewer
   - Confirm: clarity, focus, no artifacts
   - Confirm filename matches template

---

## 🤝 Submission Process

### Option 1: Pull Request (GitHub Recommended)

```bash
# Clone repo
git clone https://github.com/yourusername/doc-utilisation-ia.git
cd doc-utilisation-ia

# Create feature branch
git checkout -b docs/screenshots-intellij

# Add screenshot(s)
cp ~/Desktop/intellij-marketplace-01.png docs/assets/images/intellij/01-installation/

# Commit with descriptive message
git add docs/assets/images/
git commit -m "Add IntelliJ marketplace screenshot for installation phase"

# Push to your fork
git push origin docs/screenshots-intellij

# Create Pull Request on GitHub
# Title: "Add IntelliJ IDEA screenshots (Phase 1: Installation)"
# Description: "Captures 3 screenshots: marketplace, install dialog, restart prompt"
```

### Option 2: Direct Upload (if GH not available)

1. Email screenshots to `docs@example.com` (or team channel)
2. Include:
   - IDE version (e.g., "IntelliJ 2024.1")
   - Copilot version (shown in Help → About → Plugins)
   - Notes on capture environment
   - Filenames matching convention

### Option 3: Shared Drive/Folder

1. Upload to shared Google Drive / Dropbox folder
2. Notify maintainers
3. Maintainers integrate into docs folder

---

## ✅ Quality Checklist

Before submitting, verify each screenshot:

- [ ] **Naming**: Matches `{ide}-{feature}-{number}.png` pattern
- [ ] **Location**: In correct subdirectory (`01-installation/`, `02-parametrage/`, etc.)
- [ ] **Size**: < 150 KB (file size optimized)
- [ ] **Resolution**: 1920×1080 or higher captured
- [ ] **Clarity**: Text readable, UI elements visible
- [ ] **Consistency**: Same theme, font, zoom as other screenshots
- [ ] **Focus**: Main UI element in center, properly cropped
- [ ] **Sanitized**: No sensitive info (API keys, personal data)
- [ ] **Format**: PNG (not JPG, WebP, or other formats)

---

## 📊 Progress Tracking

As you capture, update the README.md checklist:

**IntelliJ** (`docs/assets/images/intellij/README.md`):
```markdown
- [x] intellij-marketplace-01.png ✅ 2026-03-22
- [x] intellij-install-dialog-01.png ✅ 2026-03-22
- [ ] intellij-restart-prompt-01.png 
```

**VS Code** (`docs/assets/images/vscode/README.md`):
```markdown
- [x] vscode-marketplace-01.png ✅ 2026-03-22
- [ ] vscode-install-button-01.png
```

---

## 🐛 Troubleshooting

### "Screenshot looks blurry"
- Check: Display scale = 100%
- Check: Font size at default (14px)
- Recapture with screenshot tool (not Snipping Tool)

### "Copilot feature not working"
- Restart IDE
- Re-authenticate GitHub (Settings → Sign Out, then Sign In)
- Check extension version (Settings → Extensions → GitHub Copilot)

### "Screenshot size > 150 KB"
- Use PNGCrush with `--brute` flag (slow but effective)
- Try online optimizer: TinyPNG
- Reduce width to 1400px (scales down for web anyway)

### "Theme doesn't match other screenshots"
- Verify theme in Settings
- If different theme, capture entire new set with that theme
- Don't mix themes in same folder

---

## 🎓 Examples

### Good Screenshot 👍
- ✅ 1920×1080 capture
- ✅ Darcula theme (IntelliJ) / Dark theme (VS Code)
- ✅ Single focused UI element (e.g., Marketplace card)
- ✅ Text clearly readable
- ✅ 80-120 KB file size
- ✅ Properly cropped with padding

### Bad Screenshot 👎
- ❌ Blurry or pixelated
- ❌ Mixed themes or inconsistent styling
- ❌ Multiple unrelated UI elements in frame
- ❌ Notifications or dialogs visible
- ❌ > 200 KB file size
- ❌ Cropped too tightly (no context)

---

## 📞 Support

**Questions?** Open an issue on GitHub:
- Title: "[Screenshot] Question about capturing {feature}"
- Description: Your question + context
- Assignee: Docs team

**Stuck?** Reach out:
- Slack/Discord: #docs-contributors
- Email: docs-team@example.com

---

## 🙏 Thank You!

Screenshots make documentation 10x better. Your contribution helps thousands of developers use Copilot more effectively. **Merci!** 🇫🇷

