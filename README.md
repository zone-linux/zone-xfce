# zone-xfce

XFCE desktop configuration and scripts for Zone Linux. Themed around S.T.A.L.K.E.R.

## Contents

| Path | Purpose |
|---|---|
| `bin/startupsound` | Login/logout/random sound player (uses mpv) |
| `scripts/Player` | Launch ncmpcpp visualizer in xfce4-terminal |
| `scripts/zonky` | Launch Conky with Zone config |
| `scripts/neofetch` | Bundled neofetch 7.1.0 |
| `src/.config/` | XFCE4 and app configs (panels, keybindings, themes, etc.) |
| `src/.zshrc` | Base zsh config |
| `src/.zshrc-personal` | Personal aliases and functions (sourced by .zshrc) |
| `src/.mpd/` | MPD config (runtime files excluded from repo) |
| `startup-sounds/` | OGG audio assets for login/logout sounds |

## Dependencies

The following packages must be present on the live system:

| Package | Used by |
|---|---|
| `mpv` | `bin/startupsound` (audio playback) |
| `xfce4-terminal` | `scripts/Player` |
| `conky` | `scripts/zonky` |
| `ncmpcpp`, `mpd`, `mpc` | Music stack |
| `eza` | Shell aliases in `.zshrc-personal` |
| `qogir-gtk-theme`, `qogir-icon-theme` | GTK/icon theme |
| `kvantum-theme-qogir-git` | Qt theme |
| `ttf-jetbrains-mono-nerd` | Font for panel, terminal, greeter |

## Notable Changes (2022 → 2026)

- All scripts updated to `#!/usr/bin/env bash` and `set -euo pipefail`
- `mplayer` replaced by `mpv --no-video` throughout (mplayer is AUR-only and unmaintained)
- `mplayer2`, `gmplayer` references removed from `rifle.conf`
- `xfce4-terminal -x` flag fixed to `-e` (old flag was removed in newer xfce4-terminal)
- Conky `-d` daemonize flag removed (dropped in Conky 1.10+)
- `exa` aliases updated to `eza` (exa unmaintained; eza is the maintained fork)
- Committed MPD runtime files removed (`mpd.log`, `mpd.pid`, `mpd.db`, `mpdstate`)
