# Alacritty Config — tez's terminal setup

My personal [Alacritty](https://alacritty.org/) terminal configuration.

## Features

- **JetBrains Mono Nerd Font** at size 12 — crisp, with icons/glyphs
- **Transparent window** (opacity 0.85) — shines with a compositor like picom on X11
- **Custom clean dark theme** — GitHub-dark inspired palette (`#0d1117` base)
- **Beam cursor** — non-blinking, high-visibility green (`#7ee787`)
- **50,000 lines of scrollback** (5x the default)
- **Dynamic padding & resize increments** — content stays centered, resizes snap to character cells
- **Mouse hides while typing**, selections auto-copy to clipboard
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
git clone https://github.com/sillytez/alacritty-config.git
mkdir -p ~/.config/alacritty
cp alacritty-config/alacritty.toml ~/.config/alacritty/

# 6. Run picom once (or add it to your WM autostart), then launch
picom &
alacritty
```

Alacritty live-reloads its config, so edits apply the moment you save the file.

## My setup

This config is tuned for my daily driver:

- **Arch Linux** (rolling, X11)
- **[oxwm](https://aur.archlinux.org/packages/oxwm-git)** — a lightweight tiling window manager, from the AUR (`paru -S oxwm-git`), config lives at `~/.config/oxwm/config.lua`
- **picom** compositor — started by oxwm on login, which is what makes the window transparency work
- **SDDM** display manager, no DE

In oxwm, picom (and the wallpaper) are started via autostart in `~/.config/oxwm/config.lua`:

```lua
oxwm.autostart("picom")
oxwm.autostart("xwallpaper --center ~/walls/whysoetude247.jpg")
```

## Autostart on other window managers / desktops

The terminal itself doesn't care about your WM — the only WM-specific part is
making sure a compositor runs so the transparency shows. Pick your setup:

### i3 / sway

```bash
# i3 — add to ~/.config/i3/config
exec --no-startup-id picom

# sway (Wayland) — no picom needed, sway composits itself.
# Add to ~/.config/sway/config (foot is a native Wayland alternative,
# but alacritty runs fine under XWayland):
exec_always alacritty
```

### bspwm

```bash
# Add to ~/.config/bspwm/bspwmrc
picom &
```

### dwm

```bash
# Add to ~/.xinitrc, before exec dwm
picom &
exec dwm
```

### AwesomeWM

```lua
-- Add to ~/.config/awesome/rc.lua
awful.spawn.with_shell("picom")
```

### Herbstluftwm

```bash
# Add to ~/.config/herbstluftwm/autostart
picom &
```

### Xfce

```bash
# Xfce has its own compositor — enable it instead of picom:
xfconf-query -c xfwm4 -p /general/use_compositing -s true
```

### KDE Plasma

```bash
# System Settings → Display and Monitor → Compositor → ensure enabled
# (kwin composits by default; transparency just works)
```

### GNOME (Wayland)

```bash
# Mutter composits by default — transparency works out of the box
# (alacritty runs via XWayland, or use the Wayland-native build)
```

## Uninstall

```bash
rm -rf ~/.config/alacritty
```

## Files

- `alacritty.toml` — the entire configuration, heavily commented
