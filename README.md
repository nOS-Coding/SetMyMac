# MacSetup

<img width="100" height="100" alt="MAC Background Removed" src="https://github.com/user-attachments/assets/6507f732-2581-4fe1-bb2f-87ae5966e66f" />

Got a Mac, installed MacOS and ready to go? Not quite... You need to install apps, packages, tools and need to spend hours on this. Have you ever thought: Why not automate? Here it is, a full-auto setup assistant for your Mac.

---

## How It Works

1. Choose a profile on the start screen. Each profile preselects a relevant set of installable software.
2. Step through the selection screens. Pick your browser, writing tools, office suite, AI assistants, social apps, IDEs, gaming tools, emulators, and DAWs.
3. Review your selections on the final screen and hit Install.
4. The app downloads and installs everything, reporting progress along the way.
5. When it finishes, you are free to close the app and start using your machine.

The app resets to the start screen every time you launch it. Nothing is persisted between sessions.

---

## Profiles

There are eight profiles. Each one tailors the flow and default selections.

### Writer
Distraction-free writing tools, an office suite, and AI assistance. Covers iA Writer, Ulysses, and Living Writer alongside Microsoft 365 or LibreOffice.

### Artist / Graphic Designer
Design tools and creative suites. Affinity Suite, Canva, Pixelmator Pro, and Adobe Creative Cloud.

### Office
A productivity-focused setup for workplace and administrative use. Browser, office suite, and communication tools.

### Developer
A full development toolchain -- Xcode CLT, Homebrew, Git, Node.js, Python 3.12, OpenJDK, core CLI tools, Oh My Zsh, Docker, and Rectangle -- followed by IDE selection and standard picks.

### General User
A clean, simple setup for everyday browsing, communication, and AI assistance.

### Gamer
Gaming tools, emulators, and performance tweaks. Steam, CrossOver, Whiskey, PlayCover, MetalHUD, and emulators (Ryujinx, RPCS3, PCSX2, Delta, DuckStation).

### Composer
Digital audio workstations and music production tools. GarageBand, Tracktion Waveform Free, LMMS, Ardour, FL Studio, and Logic Pro.

### All
Everything in one pass. All dev tools, all selection screens, all installables.

---

## What It Can Install

### Browsers
- Firefox
- Vivaldi
- Brave
- Chrome
- Opera GX

### Writing Apps
- iA Writer
- Ulysses (Mac App Store)
- Living Writer

### Office Suites
- Microsoft 365
- LibreOffice

### AI Assistants
- Claude (desktop app)
- Gemini (desktop app)
- ChatGPT (desktop app)

### Social & Communication
- WhatsApp
- Telegram
- Discord
- Slack
- Zoom
- Signal

### Design Tools
- Affinity Suite
- Canva
- Pixelmator Pro (Mac App Store)
- Adobe Creative Cloud

### IDEs
- VS Code
- Xcode (Mac App Store)
- Thonny
- Cursor
- Zed
- Nova
- IntelliJ IDEA CE
- PyCharm CE

### Dev AI Tools
- Claude Code (npm)
- Gemini CLI (npm)
- OpenCode (npm)
- Goose AI (install script)
- Ollama (Homebrew)

### Gaming Tools
- Steam
- CrossOver
- Whiskey
- PlayCover
- MetalHUD overlay (defaults write)

### Emulators
- Ryujinx (Nintendo Switch)
- RPCS3 (PlayStation 3)
- PCSX2 (PlayStation 2)
- Delta (multi-system, Mac App Store)
- DuckStation (PlayStation 1)

### DAWs
- GarageBand (Mac App Store)
- Tracktion Waveform Free
- LMMS
- Ardour
- FL Studio
- Logic Pro (Mac App Store)

### Dev Toolchain (Only for Developer and All profiles)

- Xcode Command Line Tools
- Homebrew
- Git (via Homebrew)
- Node.js and npm
- Python 3.14
- OpenJDK (java)
- Core CLI tools (wget, curl, tree, htop, jq, gh, mas) 
- Oh My Zsh

---

## Screenshots

<img width="1059" height="727" alt="Screenshot 2026-05-13 at 23 47 52" src="https://github.com/user-attachments/assets/2093ec68-9a77-4be8-9d95-fef5118e93f0" />
<img width="1059" height="727" alt="Screenshot 2026-05-13 at 23 47 20" src="https://github.com/user-attachments/assets/461636c8-25be-4e5e-bca5-8e7d9314441c" />
<img width="1059" height="727" alt="Screenshot 2026-05-13 at 23 47 32" src="https://github.com/user-attachments/assets/3c8fe5cc-5a3d-4a95-9f7b-53641591e567" />

---

### Requirements

- macOS 13 Ventura or later
- Apple Silicon (arm64)
- Xcode 15+ or Command Line Tools (for building)

---

### !IMPORTANT!

- All downloads come from official sources. App Store titles (Xcode, Pixelmator Pro, Delta, GarageBand, Logic Pro, Ulysses) are installed via the `mas` CLI and require you to be signed into the Mac App Store.
- The app does not phone home, collect telemetry, or contact any server other than the download URLs listed in AppCatalog.swift.
- The Developer and All profiles install Homebrew and CLI tools as part of the setup step. This may take a few minutes depending on your internet connection.
