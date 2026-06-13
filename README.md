<p align="center">
  <img width="100" height="100" src="https://github.com/user-attachments/assets/6507f732-2581-4fe1-bb2f-87ae5966e66f" alt="SetMyMac logo" />
</p>

<h1 align="center">SetMyMac</h1>

<p align="center">
  <b>A first-login macOS setup assistant — fully automated.</b><br />
  Choose a profile, pick your apps, and let SetMyMac install everything in one pass.
</p>

<p align="center">
  <a href="https://noscoding.github.io/SetMyMac/">Website</a> •
  <a href="#how-it-works">How It Works</a> •
  <a href="#profiles">Profiles</a> •
  <a href="#broken-apps--fixes">Broken Apps &amp; Fixes</a> •
  <a href="#requirements">Requirements</a>
</p>

---

## How It Works

1. **Choose a profile** on the start screen. Each profile preselects a relevant set of installable software.
2. **Step through the selection screens.** Pick your browser, writing tools, office suite, AI assistants, social apps, IDEs, gaming tools, emulators, and DAWs.
3. **Review your selections** on the final screen and hit **Install**.
4. The app downloads and installs everything, reporting progress along the way.
5. When it finishes, you are free to close the app and start using your machine.

The app resets to the start screen every time you launch it. Nothing is persisted between sessions.

---

## Profiles

| Profile | Description |
|---------|-------------|
| **Writer** | Distraction-free writing tools, office suite, AI assistance. iA Writer, Ulysses, Living Writer, Microsoft 365 or LibreOffice. |
| **Artist / Graphic Designer** | Design tools and creative suites. Affinity Suite, Canva, Pixelmator Pro, Adobe Creative Cloud. |
| **Office** | Productivity-focused. Browser, office suite, communication tools. |
| **Developer** | Full dev toolchain — Xcode CLT, Homebrew, Git, Node.js, Python 3.14, OpenJDK, Oh My Zsh — plus IDEs. |
| **General User** | Everyday browsing, communication, and AI assistance. |
| **Gamer** | Gaming tools, emulators, performance tweaks. Steam, CrossOver, Whiskey, PlayCover, MetalHUD, emulators. |
| **Composer** | Digital audio workstations. GarageBand, Tracktion Waveform Free, LMMS, Ardour, FL Studio, Logic Pro. |
| **All** | Everything in one pass. All dev tools, all selection screens, all installables. |

---

## What It Can Install

### Browsers
Firefox · Vivaldi · Brave · Chrome · Opera GX

### Writing Apps
iA Writer · Ulysses (MAS) · Living Writer

### Office Suites
Microsoft 365 · LibreOffice

### AI Assistants
Claude (desktop) · Gemini (desktop) · ChatGPT (desktop)

### Social & Communication
WhatsApp · Telegram · Discord · Slack · Zoom · Signal

### Design Tools
Affinity Suite · Canva · Pixelmator Pro (MAS) · Adobe Creative Cloud

### IDEs
VS Code · Xcode (MAS) · Thonny · Cursor · Zed · Nova · IntelliJ IDEA CE · PyCharm CE

### Dev AI Tools
Claude Code (npm) · Gemini CLI (npm) · OpenCode (npm) · Goose AI (install script) · Ollama (Homebrew)

### Gaming Tools
Steam · CrossOver · Whiskey · PlayCover · MetalHUD overlay

### Emulators
Ryubing (Nintendo Switch) · RPCS3 (PS3) · PCSX2 (PS2) · Delta (multi-system, MAS) · DuckStation (PS1)

### DAWs
GarageBand (MAS) · Tracktion Waveform Free · LMMS · Ardour · FL Studio · Logic Pro (MAS)

### Dev Toolchain (Developer & All profiles)
Xcode CLT · Homebrew · Git · Node.js & npm · Python 3.14 · OpenJDK · CLI tools (wget, curl, tree, htop, jq, gh, mas) · Oh My Zsh

### Utilities
Free Download Manager · Balena Etcher · ApplePi-Baker · The Unarchiver · AppCleaner · IINA · HandBrake · OBS Studio · Keka · Rectangle · Stats · Hidden Bar · Maccy · AltTab · MonitorControl · WinDiskWriter

---

## Broken Apps & Fixes

SetMyMac uses a **binary patching** approach. The app binary stores app metadata — display names, Homebrew cask names, and download URLs — in a struct table. For apps that have moved, rebranded, or lack a Homebrew cask, the app deliberately sets a failing URL to trigger its **fallback script** (`setmymac-fallback.sh`), which handles the installation manually.

### Currently Tracked Issues

| App | Problem | Fix | Status |
|-----|---------|-----|--------|
| **PlayCover** | Old `playcover` cask removed from Homebrew | Binary patched to use `playcover-community` | ✅ Fixed |
| **Ryujinx → Ryubing** | Project rebranded, all URLs and names stale | Binary patched (display name, key, URL, struct entry); fallback downloads from GitLab | ✅ Fixed |
| **FL Studio** | No Homebrew cask exists | Fallback downloads DMG via redirect URL | ✅ Fixed |
| **DuckStation** | Old ZIP URL broken | Fallback downloads from GitHub latest release | ✅ Fixed |
| **iA Writer** | Mac App Store only, no cask | Fallback uses `mas install 775737590` | ✅ Fixed |
| **Ardour** | No cask; officially paid | Fallback scrapes `nightly.ardour.org` for the latest free demo DMG | ✅ Fixed |
| **RPCS3** | Binary URL returns 404 | Fallback fetches latest ARM64/x64 7z from GitHub releases API, installs `unar` if needed | ✅ Fixed |

### How Patching Works

1. Locate the app metadata struct table at offset `0xb4fb0` in the `SetMyMac` binary.
2. Each entry is 23 bytes: flags (1) + App Store ID (4) + padding (2) + padding (4) + cask index (2) + display name offset (2) + lowercase key offset (2) + URL offset (2) + padding (4).
3. Strings (display name, key, URL) are stored at fixed offsets (e.g., `0xa2587` for Ryubing display name).
4. After editing, the binary must be re-signed: `codesign -fs - SetMyMac`.
5. The fallback script at `/usr/local/bin/setmymac-fallback.sh` catches apps whose cask or URL fails.

---

## Screenshots

<p align="center">
  <img width="300" src="https://github.com/user-attachments/assets/2093ec68-9a77-4be8-9d95-fef5118e93f0" alt="Screenshot 1" />
  <img width="300" src="https://github.com/user-attachments/assets/461636c8-25be-4e5e-bca5-8e7d9314441c" alt="Screenshot 2" />
  <img width="300" src="https://github.com/user-attachments/assets/3c8fe5cc-5a3d-4a95-9f7b-53641591e567" alt="Screenshot 3" />
</p>

---

## Requirements

- macOS 13 Ventura or later
- Apple Silicon (arm64)
- Xcode 15+ or Command Line Tools (for building)

---

## Important Notes

- All downloads come from **official sources**. MAS titles (Xcode, Pixelmator Pro, Delta, GarageBand, Logic Pro, Ulysses) install via `mas` and require you to be signed into the Mac App Store.
- The app **does not phone home**, collect telemetry, or contact any server other than the download URLs listed in `AppCatalog.swift`.
- The Developer and All profiles install Homebrew and CLI tools. This may take a few minutes.
- **Contributions welcome!** If an app URL or cask breaks, open an issue or PR.

---

*MIT License — © 2026 nOS_Coding*