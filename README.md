# rdr

## Keyboard-First Agent Workspace

`rdr` is a zero-bloat, keyboard-first terminal workspace designed for running, monitoring, and multiplexing AI coding agents across independent projects with real-time Writing/Sleeping telemetry in the status footer.

![rdr screenshot preview](./docs/screenshots/cockpit.png)

## What makes rdr special?

- **One terminal session** hosts multiple AI agents (agy, claude, opencode, aider) in a tmux layout
- **Real-time telemetry** in status footer: Writing/Sleeping counts, session duration, tool usage
- **No agent state leakage** — each pane is a clean shell session
- **Zero bloat** — no background daemons, no GUI frameworks, no Node.js/Electron bloat
- **Terminal-agnostic** — works with alacritty, kitty, foot, konsole, xterm, gnome-terminal
- **Keyboard-first** — all commands via tmux keybindings or simple flags

## Key Features

- **5-pane default layout**:
  - Top-left: laya-proxy logs (journalctl)
  - Top-right: tool-tracker (real-time tool usage)
  - Bottom-left: laya-stats --routing
  - Bottom-right: laya-stats --audit
  - Bottom: interactive fish shell for agent commands

- **Telemetry footer**: Writing/Sleeping counts, session duration, last command
- **Keyboard shortcuts**:
  - `Ctrl+b x`: close active pane
  - `Ctrl+b c`: new terminal tab
  - `Ctrl+b &`: close window
  - `Ctrl+b w`: window list
  - `rdr -c`: clear all panes (non-destructive)
  - `rdr -r`: rebuild full layout from template

- **Terminal-agnostic**: auto-detects alacritty, kitty, foot, xterm, konsole, gnome-terminal
- **Customizable layouts**: preset layouts (single, dual, tri, quad) with layout commands
- **Session persistence**: save/restore layouts via save_layout and load_layout commands

## Install

1. Install tmux and your preferred terminal (alacritty, kitty, etc.)
2. Clone this repo
3. Symlink `rdr` into your PATH:
   ```bash
   ln -s $PWD/rdr ~/.local/bin/rdr
   ```
4. Run: `rdr`

## Usage

```bash
rdr              # launch with default quad layout
rdr -l quad      # launch with quad layout
rdr -l telemetry # launch with telemetry layout
rdr -c           # clear all panes
rdr -r           # rebuild full layout
rdr -k           # kill session
```

## Layouts

| Layout | Panes | Description |
|--------|-------|-------------|
| single | 1 | Single pane |
| dual | 2 | Two panes side by side |
| tri | 3 | Three panes |
| quad | 4 | Four panes in grid |
| rows | 5 | Five panes in rows |
| telemetry | 5 | Telemetry cockpit with proxy logs, tool-tracker, stats, and control shell |

## Screenshots

![Cockpit overview](./docs/screenshots/cockpit.png)
![Quad layout](./docs/screenshots/quad.png)
![Telemetry view](./docs/screenshots/telemetry.png)

*Placeholder screenshots — replace with actual terminal captures.

## Optional Integration with Laya

`rdr` can optionally integrate with the `laya` secret gateway for proxy health checks (`laya-tool-tracker`, `laya-stats --routing`, `laya-stats --audit`). This is NOT required — `rdr` runs standalone with any agent that has a CLI.

## License

MIT OR Apache-2.0
