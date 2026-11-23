# XarenArch

XarenArch is my own Arch-based Linux distro: a live and installable ISO with [Hyprland](https://hyprland.org/) and a macOS-style desktop ([MacShell](https://github.com/0-ss/MacShell)), my own trimmed kernel, and a graphical installer. I build and maintain it solo as a learning project and as something I actually use.

**Latest: [XarenArch V2](https://github.com/adamelhadrii/XarenArch/releases/tag/v2.0.0).** The earlier `v1.0.0-beta` build is marked *(broken)*; use V2.

## Status

V2 boots in QEMU and on real hardware, and **the Calamares installer works**: I installed it from a USB stick onto its own partition on my laptop (a Chromebook-class UEFI machine), and it's running there now.

**Tested**
- UEFI boot from USB, and the live session
- Install into free space with manual partitioning, then first boot of the installed system
- The Claude Code CLI, installed with Install Apps

**Not tested**
- BIOS (legacy) boot, "Erase disk" mode, disk encryption (LUKS), the swap-file and autologin options
- Any machine other than mine
- The other Install Apps entries (Cursor, Discord, opencode, Antigravity, WhatsApp)

**Known issues**
- On my Chromebook, audio and the touchpad needed a manual fix after installing (for audio I used [WeirdTreeThing's chromebook-linux-audio](https://github.com/WeirdTreeThing/chromebook-linux-audio)). Those fixes are not in the ISO yet.
- This is a personal project. Expect rough edges and no support guarantee.

## What's inside

- **Base:** Arch Linux packages
- **Kernel:** `linux-xarenarch` 7.3.5, a trimmed build for x86-64-v2 (about 40% smaller modules than the stock kernel). Stock `linux` is kept as a fallback boot entry.
- **Desktop:** Hyprland 0.57 with MacShell 0.5.3: menu bar, dock, Spotlight, Control Center, lock screen
- **Apps:** Chromium, Nautilus, foot, fastfetch, cmatrix
- **Keybind Changer** (`Super+K`): a small app that lists every shortcut and lets you rebind or disable any of them. It validates the config before applying and rolls back on errors.
- **Install Apps:** a deletable script on the dock that installs Cursor, Discord, Claude Code, Antigravity CLI, opencode and a WhatsApp Web launcher when you run it. Nothing proprietary is bundled in the ISO.
- **Installer:** [Calamares](https://calamares.io/), with erase-disk or manual partitioning, optional LUKS encryption, zram swap, and GRUB for UEFI and BIOS

Handy keys: `Super+Return` terminal, `Super+Q` close window, `Super+K` Keybind Changer.

## Download and boot

Grab `xarenarch-*-x86_64.iso` and `SHA256SUMS` from the [releases page](https://github.com/adamelhadrii/XarenArch/releases) and check the hash:

```
sha256sum -c SHA256SUMS
```

- **Try it in QEMU:** `qemu-system-x86_64 -enable-kvm -m 4G -cpu host -smp 4 -cdrom xarenarch-*-x86_64.iso -boot d` (add OVMF firmware to test UEFI)
- **USB stick:** write it with any image writer. Double-check the target device first, because writing to the wrong one destroys its data.

The live session logs in automatically as `live` (password `live`, passwordless sudo). Don't expose a live session to a network you don't trust. You need about 4 GB of RAM to be comfortable. Secure Boot is not supported.

## Installing

Start **Install XarenArch** from the dock. Installing **erases the disk you pick** (or whatever you set up in manual partitioning). There is no dual-boot menu support. I installed it next to another Arch system on the same disk, sharing its EFI partition, and afterwards my other system's boot entry disappeared and I had to re-add it. If you install alongside another OS, save your boot entries first (`efibootmgr -v > ~/efi-entries.txt`), back up your data, and keep a rescue USB.

The installed system boots `linux-xarenarch` by default. That kernel does **not** update through `pacman` yet (there is no hosted repo for it); the stock `linux` entry does. Until that changes, new kernel versions only arrive in new ISO builds.

## Hardware notice

It's built around my own hardware (an Intel laptop with Mediatek Wi-Fi) and virtual machines. It may not work on yours; expect to troubleshoot drivers, firmware or boot issues if your setup differs.

## Credits

- [Arch Linux](https://archlinux.org/) and its packagers
- [Hyprland](https://hyprland.org/)
- [MacShell](https://github.com/0-ss/MacShell) by 0-ss (MIT)
- [Quickshell](https://quickshell.org/)
- [Calamares](https://calamares.io/)

## License

MIT for this repository (see [LICENSE](LICENSE)). The software on the ISO keeps its own licenses. No warranty.
