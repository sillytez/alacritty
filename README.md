# Alacritty Config — tez's terminal setup

<p align="center">
  <a href="https://github.com/alacritty/alacritty"><img alt="Alacritty" src="https://img.shields.io/badge/terminal-Alacritty-e6edf3?style=flat&labelColor=0d1117"></a>
  <img alt="Font" src="https://img.shields.io/badge/font-JetBrainsMono_Nerd_Font-7ee787?style=flat&labelColor=0d1117">
  <img alt="Theme" src="https://img.shields.io/badge/theme-GitHub_Dark-0d1117?style=flat&labelColor=0d1117&color=7ee787">
  <img alt="Opacity" src="https://img.shields.io/badge/opacity-0.85-79c0ff?style=flat&labelColor=0d1117">
</p>

> My personal [Alacritty](https://alacritty.org/) terminal configuration —
> a clean, minimal, GitHub-dark themed terminal with transparent windows,
> a bright green beam cursor, and sensible keybindings.

## ✨ Features

| | |
|---|---|
| 🔤 **Font** | JetBrainsMono Nerd Font at size 12 — crisp, with icons/glyphs |
| 🌑 **Theme** | GitHub-dark inspired palette (`#0d1117` base, `#e6edf3` text) |
| 👀 **Cursor** | Beam style, non-blinking, high-visibility green (`#7ee787`) |
| 🪟 **Opacity** | 0.85 — transparent window (needs a compositor on X11) |
| 📜 **Scrollback** | 50,000 lines (5× the default) |
| 📐 **Padding** | Dynamic padding + resize increments — content stays centered |
| 🖱️ **Mouse** | Hides while typing, selections auto-copy to clipboard |
| ⌨️ **Keybinds** | vi-mode toggle, fullscreen, new window, URL hints |
| 🎨 **Selection** | Hand-picked GitHub-dark selection colors |

## 🎨 Palette

| Color | Hex | Preview |
|---|---|---|
| background | `#0d1117` | ![](https://img.shields.io/badge/-%20-0d1117?style=flat-square) |
| foreground | `#e6edf3` | ![](https://img.shields.io/badge/-%20-e6edf3?style=flat-square) |
| black (normal) | `#161b22` | ![](https://img.shields.io/badge/-%20-161b22?style=flat-square) |
| red | `#ff7b72` | ![](https://img.shields.io/badge/-%20-ff7b72?style=flat-square) |
| green (accent) | `#7ee787` | ![](https://img.shields.io/badge/-%20-7ee787?style=flat-square) |
| yellow | `#e3b341` | ![](https://img.shields.io/badge/-%20-e3b341?style=flat-square) |
| blue | `#79c0ff` | ![](https://img.shields.io/badge/-%20-79c0ff?style=flat-square) |
| magenta | `#c0a6f0` | ![](https://img.shields.io/badge/-%20-c0a6f0?style=flat-square) |
| cyan | `#96d3e6` | ![](https://img.shields.io/badge/-%20-96d3e6?style=flat-square) |
| white | `#e6edf3` | ![](https://img.shields.io/badge/-%20-e6edf3?style=flat-square) |
| bright black | `#484f58` | ![](https://img.shields.io/badge/-%20-484f58?style=flat-square) |
| bright red | `#ff9aa2` | ![](https://img.shields.io/badge/-%20-ff9aa2?style=flat-square) |
| bright green | `#a7f0ba` | ![](https://img.shields.io/badge/-%20-a7f0ba?style=flat-square) |
| bright yellow | `#f9e48b` | ![](https://img.shields.io/badge/-%20-f9e48b?style=flat-square) |
| bright blue | `#a5d6ff` | ![](https://img.shields.io/badge/-%20-a5d6ff?style=flat-square) |
| bright magenta | `#d5b4ff` | ![](https://img.shields.io/badge/-%20-d5b4ff?style=flat-square) |
| bright cyan | `#c2e1ff` | ![](https://img.shields.io/badge/-%20-c2e1ff?style=flat-square) |
| bright white | `#ffffff` | ![](https://img.shields.io/badge/-%20-ffffff?style=flat-square) |
| selection bg | `#2d4a6e` | ![](https://img.shields.io/badge/-%20-2d4a6e?style=flat-square) |
| cursor | `#7ee787` | ![](https://img.shields.io/badge/-%20-7ee787?style=flat-square) |

## 📋 Table of contents

- [Dependencies](#dependencies)
- [Install](#install)
  - [Per-distro quick install](#per-distro-quick-install)
- [My setup](#my-setup)
- [Autostart on other WMs / DEs](#autostart-on-other-wms--des)
- [Keybindings](#keybindings)
- [Uninstall](#uninstall)
- [Files](#files)

## 📦 Dependencies

| Dependency | Why | Notes |
|---|---|---|
| [Alacritty](https://github.com/alacritty/alacritty) | the terminal itself | required |
| [JetBrains Mono Nerd Font](https://www.nerdfonts.com/font-downloads) | the font this config uses | required for correct rendering |
| [picom](https://github.com/yshui/picom) (or any compositor) | makes the 0.85 window opacity show on X11 | optional — without it the window renders opaque |
| X11 | transparency is compositor-based on X11 | on Wayland, opacity works via your compositor's own settings |

## 📥 Install

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

### Per-distro quick install

<details>
<summary>One-liner installs per distro</summary>

```bash
# Arch
sudo pacman -S alacritty ttf-jetbrains-mono-nerd picom

# Manjaro (same as Arch)
sudo pacman -S alacritty ttf-jetbrains-mono-nerd picom

# Artix (same as Arch + AUR)
sudo pacman -S alacritty ttf-jetbrains-mono-nerd picom
paru -S ttf-jetbrains-mono-nerd

# Debian / Ubuntu
sudo apt install alacritty picom fonts-jetbrains-mono
# Nerd Font glyphs — grab from nerdfonts.com/font-downloads → ~/.local/share/fonts/ → fc-cache -f

# Fedora
sudo dnf install alacritty picom jetbrains-mono-fonts
# Nerd Font glyphs — grab from nerdfonts.com/font-downloads → ~/.local/share/fonts/ → fc-cache -f

# RHEL / Rocky / Alma
sudo dnf install epel-release
sudo dnf install alacritty picom jetbrains-mono-fonts
# Nerd Font glyphs — grab from nerdfonts.com/font-downloads → ~/.local/share/fonts/ → fc-cache -f

# Void
sudo xbps-install alacritty picom
# Nerd Font — grab from nerdfonts.com/font-downloads → ~/.local/share/fonts/ → fc-cache -f

# openSUSE
sudo zypper install alacritty picom jetbrains-mono-fonts
# Nerd Font glyphs — grab from nerdfonts.com/font-downloads → ~/.local/share/fonts/ → fc-cache -f

# Gentoo
sudo emerge alacritty picom media-fonts/jetbrains-mono
# Nerd Font glyphs — sudo emerge -av media-fonts/nerd-fonts

# Alpine
sudo apk add alacritty picom font-jetbrains-mono-nerd

# NixOS (in configuration.nix or flake.nix)
# environment.systemPackages = with pkgs; [
#   alacritty picom
#   (nerdfonts.override { fonts = [ "JetBrainsMono" ]; })
# ];

# Solus
sudo eopkg install alacritty picom jetbrains-mono
```

</details>

## 🖥️ My setup

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

Full setup at [sillytez/oxwm-sddm](https://github.com/sillytez/oxwm-sddm).

## 🪟 Autostart on other WMs / DEs

The terminal itself doesn't care about your WM — the only WM-specific part is
making sure a compositor runs so the transparency shows. Pick your setup:

<details>
<summary>i3 / sway</summary>

```bash
# i3 — add to ~/.config/i3/config
exec --no-startup-id picom

# sway (Wayland) — no picom needed, sway composits itself.
# Add to ~/.config/sway/config:
exec_always alacritty
```

</details>

<details>
<summary>bspwm</summary>

```bash
# Add to ~/.config/bspwm/bspwmrc
pgrep -x picom > /dev/null || picom &
```

</details>

<details>
<summary>dwm</summary>

```bash
# Add to ~/.xinitrc, before exec dwm
picom &
exec dwm
```

</details>

<details>
<summary>AwesomeWM</summary>

```lua
-- Add to ~/.config/awesome/rc.lua
awful.spawn.with_shell("picom")
```

</details>

<details>
<summary>Hyprland (Wayland)</summary>

```bash
# Hyprland has its own compositor — no picom needed.
# Add to ~/.config/hypr/hyprland.conf:
exec-once = alacritty
```

</details>

<details>
<summary>Xfce</summary>

```bash
# Xfce has its own compositor — enable it instead of picom:
xfconf-query -c xfwm4 -p /general/use_compositing -s true
```

</details>

<details>
<summary>KDE Plasma</summary>

```bash
# System Settings → Display and Monitor → Compositor → ensure enabled
# (kwin composits by default; transparency just works)
```

</details>

<details>
<summary>GNOME (Wayland)</summary>

```bash
# Mutter composits by default — transparency works out of the box
# (alacritty runs via XWayland, or use the Wayland-native build)
```

</details>

## ⌨️ Keybindings

| Keys | Action |
|---|---|
| `Ctrl+Shift+Space` | Toggle vi mode (cursor keys + text selection) |
| `Ctrl+Shift+C` | Copy |
| `Ctrl+Shift+V` | Paste |
| `Ctrl+Enter` | Toggle fullscreen |
| `Ctrl+Shift+E` | New window |
| `Ctrl+Shift+O` | Highlight URLs (type label to open) |

> **Note:** `Ctrl+Shift+V` is paste — vi-mode toggle is on `Ctrl+Shift+Space`
> so nothing can shadow it.

## 🗑️ Uninstall

```bash
rm -rf ~/.config/alacritty
```

## 📄 Files

| File | Description |
|---|---|
| `alacritty.toml` | The entire configuration, heavily commented |
