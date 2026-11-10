# zone-xfce

XFCE desktop configuration and scripts for Zone Linux. Themed around S.T.A.L.K.E.R.

## Contents

| Path | Purpose |
|---|---|
| `bin/startupsound` | Login/logout/random sound player (uses mpv, waits for PipeWire) |
| `scripts/Player` | Launch ncmpcpp visualizer in xfce4-terminal |
| `scripts/zonky` | Launch Conky with the Zone config |
| `scripts/neofetch` | Bundled neofetch (Debian-only GIO path removed) |
| `scripts/xfce4-session-logout` | Play the logout sound, then call the real XFCE logout helper |
| `scripts/qbittorrent` | Launch the Qt6 app with the qt6ct platform theme |
| `src/.config/` | XFCE4 and app configs (panels, keybindings, themes, Qt5/Qt6) |
| `src/.config/systemd/` | Enables the MPD systemd user unit |
| `src/.config/ncmpcpp/` | ncmpcpp library/visualizer settings |
| `src/.gtkrc-2.0` | GTK2 theme settings |
| `src/.zshrc` | Base zsh config |
| `src/.zshrc-personal` | Aliases and functions (sourced by `.zshrc`) |
| `src/.mpd/` | MPD config and empty playlists directory (no runtime state) |
| `startup-sounds/` | OGG audio assets for login/logout sounds |

## Music

The playlist packages install music once under `/usr/share/zone/music`
(Metro and Anomaly). `mpd.conf` indexes that shared library and the user's
writable `~/Music` directory. MPD itself is enabled as a systemd user unit
(`default.target.wants/mpd.service`), so it starts with the desktop session
instead of racing an autostart entry.

## Dependencies

Packages referenced by the configuration and scripts:

| Package | Used by |
|---|---|
| `mpv` | `bin/startupsound` (audio playback) |
| `xfce4-terminal` | `scripts/Player` |
| `conky` | `scripts/zonky` |
| `ncmpcpp`, `mpd`, `mpc` | Music stack |
| `eza` | `ls`/`l` aliases |
| `bat` | `cat`/`less` aliases |
| `btop` | `g` alias |
| `ripgrep` | `rg` alias |
| `expac` | `rip`/`riplong` aliases |
| `zathura`, `zathura-pdf-mupdf` | Document viewing |
| `tty-clock` | `clock` alias |
| `unimatrix` | `matrix` alias |
| `qogir-gtk-theme-git`, `qogir-icon-theme-git` | GTK/icon theme |
| `kvantum`, `kvantum-theme-qogir-git`, `qt5ct`, `qt6ct` | Qt5/Qt6 theming |
| `ttf-jetbrains-mono-nerd` | Panel, terminal, greeter font |

The ISO package list is authoritative; `./scripts/lint.sh` checks aliases against
installed packages.

## Notable Changes (2022 → 2026)

- All scripts use `#!/usr/bin/env bash` and `set -euo pipefail`
- `mplayer` replaced by `mpv --no-video`
- `xfce4-terminal -x` fixed to `-e`
- Conky `-d` daemonize flag removed
- `exa` aliases moved to `eza`
- `cleanup` alias now uses `paru -Sc --noconfirm`
- Dead aliases removed (`moc`, `devour`, `pipes`, `pcmanfm`, `sxiv`); `sxiv` now points
  at `viewnior`
- `qt6ct` and Kvantum configuration added so Qt6 apps match the theme
- Bundled neofetch keeps its config but no longer exports the Debian multiarch
  `GIO_EXTRA_MODULES` path
