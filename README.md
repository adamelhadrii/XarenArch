# XarenArch

XarenArch is my personal Arch Linux-based distro, built and maintained solo as a learning project and daily driver. It's tailored specifically to my own hardware and workflow — not intended as a general-purpose distro for arbitrary machines.

## ⚠️ Compatibility Notice

This ISO is built and tested **only on my own hardware**. There is no guarantee it will boot, install, or run correctly on different CPUs, GPUs, or laptop/desktop configurations. Use on other hardware is at your own risk — expect to troubleshoot driver, firmware, or boot issues yourself if your setup differs from mine.

## What's Inside

- **Base**: Arch Linux
- **Window Manager**: [Hyprland](https://hyprland.org/) (Wayland)
- **Dotfiles**: [illogical-impulse](https://github.com/end-4/dots-hyprland) — provides a pre-configured, more user-friendly Hyprland setup out of the box (theming, keybinds, widgets, etc.) instead of a bare Hyprland config
- **Installer**: Calamares — supports full disk wipe, dual-boot alongside an existing OS, or trying the live environment without installing anything

## Why This Exists

This started as a way to actually learn how a Linux distro is built and how the pieces fit together — package selection, boot process, installer integration, desktop environment configuration — rather than just installing something premade. It's shaped entirely around my own preferences and hardware, so it's shared publicly mainly for reference and transparency, not as a recommended daily driver for others.

## Installing

Boot the ISO, and from the live environment you can:
1. **Try it live** — explore without touching your disk
2. **Full wipe install** — erase the target disk and install XarenArch fresh
3. **Dual-boot** — install alongside an existing operating system

## Credits

- [Arch Linux](https://archlinux.org/)
- [Hyprland](https://hyprland.org/)
- [illogical-impulse dotfiles](https://github.com/end-4/dots-hyprland) by end-4
- [Calamares](https://calamares.io/)

## License

Personal project — no warranty, no guarantee of support. Use at your own risk.
