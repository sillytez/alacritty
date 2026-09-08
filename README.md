# Alacritty Config — tez's terminal setup

My personal [Alacritty](https://alacritty.org/) terminal configuration.

## Features

- **JetBrains Mono Nerd Font** at size 12 — crisp, with icons/glyphs
- **Transparent window** (opacity 0.85) — shines with a compositor like picom on X11
- **Custom clean dark theme** — GitHub-dark inspired palette (`#0d1117` base)
- **Beam cursor** — non-blinking, high-visibility green (`#7ee787`)
- Hand-picked selection colors and 8px/4px window padding
- Useful key bindings included as commented suggestions (new window/tab, fullscreen, search)

## Dependencies

| Dependency | Why | Notes |
|---|---|---|
| [Alacritty](https://github.com/alacritty/alacritty) | the terminal itself | required |
| [JetBrains Mono Nerd Font](https://www.nerdfonts.com/font-downloads) | the font this config uses | required for correct rendering |
| [picom](https://github.com/yshui/picom) (or any compositor) | makes the 0.85 window opacity actually show on X11 | optional — without it the window renders opaque |
| X11 | transparency is compositor-based on X11 | on Wayland, opacity works via your compositor's own settings |

## Install

```bash
# 1. Install alacritty (Arch)
sudo pacman -S alacritty

# 2. Install the font (Arch; pick either)
sudo pacman -S ttf-jetbrains-mono-nerd        # official repos
paru -S ttf-jetbrains-mono-nerd               # or from AUR, same name

# 3. Optional: compositor for transparency (X11)
sudo pacman -S picom

# 4. Back up any existing config
mv ~/.config/alacritty ~/.config/alacritty.bak 2>/dev/null || true

# 5. Clone and link (or copy) this repo
git clone https://github.com/tez/alacritty-config.git
mkdir -p ~/.config/alacritty
cp alacritty-config/alacritty.toml ~/.config/alacritty/

# 6. Run picom once (or add it to your WM autostart), then launch
picom &
alacritty
```

Alacritty live-reloads its config, so edits apply the moment you save the file.

## Uninstall

```bash
rm -rf ~/.config/alacritty
```

## Files

- `alacritty.toml` — the entire configuration, heavily commented
