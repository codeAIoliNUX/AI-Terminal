# AI-Terminal
Creating an AI terminal assistant.


## One-Click Kitty-Lumo Workstation

**Project Goal:** Transform a single click on the kitty terminal icon into an instant dual-pane workstation: a plain vanilla bash terminal on the left half of the screen, and Lumo AI (in a clean Chromium app window with no browser chrome) on the right half, ready for side-by-side command-line assistance.

**What It Does:**  
Double-click the kitty terminal icon → within seconds, you get a fully tiled, 1920×1080 workspace: terminal (left 50% × 100%) + Lumo AI assistant (right 50% × 100%), both sized and positioned automatically by KDE Window Rules, no typing required.

**Why It Works:**  
A combination of four layers working in harmony:

1. **Shell Layer** — Stripped starship theming back to vanilla bash, with custom Ctrl+c/v copy-paste mappings
2. **Launcher Layer** — A guard-wrapped script that spawns the Lumo Chromium app-window, keyed off `.bashrc` so it fires on every new kitty session
3. **Desktop Layer** — KDE Wayland Window Rules enforcing pixel-perfect half-screen placement for both kitty and Chromium at launch
4. **Safety Layer** — Duplicate prevention logic (`pgrep` check) so multiple kitty windows don't spawn multiple Lumo instances

**Unique Value:**  
Unlike generic "AI terminal" tools (Warp, Wave, etc.) that require proprietary backends or API keys, this uses Lumo's native web interface with a local automation shim — privacy-preserving (Lumo's traffic stays inside Proton's E2EE infrastructure), reversible (each layer can be disabled without breaking the rest), and fully transparent (every line of code visible in `~/.bashrc`, `~/.local/bin/`, and KDE's System Settings).

**Ideal For:**  
Bug bounty recon sessions, Nmap troubleshooting, long-form writing research, or any workflow where command-line output needs rapid iteration with AI assistance — with zero friction between the problem and the solution.

**Future Evolution:**  
When Lumo releases a public API, this architecture upgrades cleanly: the `open-lumo.sh` script becomes an integrated Lumo client with scrollback context, chat-sidebar UI, and (critically) an approval-gated command execution layer.

---

**TL;DR:** Click kitty → terminal + Lumo side-by-side, every time. No clean install, no proprietary tools, no cloud API dependency. Just configuration. 🐱🚀
