# Manjaro for WSL and Windows 11 - Easy setup!

This repository provides a ready-to-install **Manjaro Linux WSL base image** for users who want a clean Manjaro environment inside Windows Subsystem for Linux without having to build a root filesystem manually.

The current release is **Manjaro WSL Base 0.1.1**.

[Download Manjaro WSL Base 0.1.1](https://github.com/vinberg88/manjaro/releases/tag/0.1.1)

---

Here you will find diffrent desktop for MANJARO LINUX to Install for WSL and Windows 11.

Setup KDE 6 for Manjaro via Github: https://github.com/vinberg88/manjaro/blob/main/Manjaro-KDE6-2026.txt

Setup KDE 6 for Manjaro via YouTube: https://www.youtube.com/watch?v=n8cddVc5cQE

<img width="1200" height="800" alt="Manjaro-KDE6-2026" src="https://github.com/user-attachments/assets/9c7d62a5-5950-4054-84c7-5112cc1bb406" />

---

## What is Manjaro Linux?

Manjaro Linux is a free and open-source Linux distribution based on Arch Linux.

It keeps many of the strengths that make Arch popular — `pacman`, access to a huge software ecosystem, rolling updates and a highly customizable system — while adding its own repositories, tools and release process.

Manjaro is a **rolling-release distribution**. Instead of reinstalling the operating system for every major version, an installed system is continuously updated with newer packages.

Manjaro also maintains its own package branches and mirror infrastructure rather than simply pointing directly at the Arch Linux repositories.

### Manjaro package branches

Manjaro packages move through different branches before reaching normal Stable users:

- **Unstable** — receives new packages first and is closest to upstream development.
- **Testing** — packages receive additional testing before Stable.
- **Stable** — the recommended branch for normal systems and the branch used by this WSL image.

This WSL project intentionally uses the **Stable** branch.

---

# Manjaro WSL Base 0.1.1

The image is designed as a useful **rich base**, but no graphical desktop environment is installed by default.

That means you start with a clean and verified Manjaro system and can later install KDE Plasma, GNOME, XFCE, Cinnamon, Deepin, Budgie or another desktop yourself.

## Included features

- Manjaro Linux rolling-release base
- Manjaro **Stable** branch
- WSL2 support
- WSLg detection
- `systemd` enabled as PID 1
- User systemd session
- User D-Bus support
- Windows executable interoperability
- Automatic first-run user setup
- UID 1000 for the first normal user
- Hostname setup during first run
- `sudo` / `wheel` configuration
- `en_US.UTF-8` locale
- `Europe/Stockholm` timezone in the current build
- Manjaro `pacman-mirrors`
- `pacman`
- `yay`
- `pamac-cli`
- `base-devel`
- Git and common development tools
- OpenSSH installed but disabled by default
- No desktop environment preinstalled

### Useful packages already included

The base contains a selection of useful command-line and development tools, including:

```text
bash-completion
base-devel
bind
curl
fastfetch
git
htop
inetutils
iproute2
iputils
jq
less
man-db
man-pages
nano
openssh
pacman-contrib
pamac-cli
rsync
tar
tree
unzip
vim
wget
yay
zip
```

---

## Verified WSL status

Manjaro WSL Base 0.1.1 has been installed and tested on WSL2.

```text
Manjaro Linux WSL Base 0.1.1
============================================
Distribution:          Manjaro Linux
Kernel:                6.18.40.1-microsoft-standard-WSL2
WSL:                   yes
WSLg:                  yes
Windows interop:       OK
PID 1:                 systemd
systemd:               running
User systemd:          running
User D-Bus:            OK
Failed units:          0
User:                  adolf
UID:                   1000
Locale:                en_US.UTF-8
Timezone:              Europe/Stockholm
DNS:                   OK
Root filesystem:       ext4
Manjaro repositories:  OK
Branch:                stable
pacman-mirrors:        OK
yay:                   OK
pamac-cli:             OK
AUR build tools:       OK
Desktop:               not installed
Status:                READY
```

The Linux kernel shown inside WSL is the **Microsoft WSL2 kernel**, not a normal Manjaro-installed kernel. This is expected behavior under WSL2.

---

# Installation

Just download Manjaro from here - https://github.com/vinberg88/manjaro/releases/tag/0.1.1

Now press the Blue Icon that you downloaded and Manjaro will be setup user and password and hostname.

## Requirements

You need:

- Windows 11
- WSL2 enabled
- A reasonably current Microsoft WSL installation

Check WSL from PowerShell:

```powershell
wsl --version
wsl --status
```

If WSL is not installed yet:

```powershell
wsl --install
```

Restart Windows if requested.

## Download

Open the release page:

https://github.com/vinberg88/manjaro/releases/tag/0.1.1

Download:

```text
Manjaro-WSL-Base-0.1.1-x86_64.wsl
```

The compressed WSL image is approximately **600 MB**.

SHA-256 checksums and release metadata are also available in the release.

## Install the `.wsl` image

On supported WSL versions you can install the image directly from Windows, or use PowerShell:

```powershell
wsl --install --from-file .\Manjaro-WSL-Base-0.1.1-x86_64.wsl
```

After installation, start the new Manjaro distribution.

The first-run setup creates your normal Linux account and asks for the required user information.

---

# Manjaro WSL commands

This image includes a small helper utility called `manjaro-wsl`.

## System health check

```bash
manjaro-wsl doctor
```

This checks important parts of the WSL environment including systemd, D-Bus, Windows interoperability, DNS, Manjaro repositories, `pacman-mirrors`, `yay`, Pamac and AUR build tools.

## System information

```bash
manjaro-wsl info
```

## Version

```bash
manjaro-wsl version
```

## Installed tools

```bash
manjaro-wsl tools
```

## Update Manjaro

```bash
manjaro-wsl update
```

For normal package maintenance you can also use Manjaro directly:

```bash
sudo pacman -Syu
```

For AUR packages:

```bash
yay -Syu
```

Because Manjaro is rolling release, you normally **do not need to download a new WSL image every time Manjaro receives package updates**. Update the installed distribution just like a normal Manjaro system.

A new `.wsl` release is mainly useful when this project changes its WSL configuration, first-run setup, bundled tools or base-image design.

---

# pacman-mirrors

Manjaro uses its own `pacman-mirrors` utility to manage package mirrors.

Check your current branch:

```bash
pacman-mirrors --get-branch
```

Check mirror status:

```bash
pacman-mirrors --status
```

Refresh using fast up-to-date mirrors:

```bash
sudo pacman-mirrors --fasttrack
sudo pacman -Syu
```

It is important to perform a full package synchronization after changing mirrors or branches. Avoid partial upgrades on an Arch/Manjaro-based system.

---

# Pacman, Pamac and yay

## pacman

`pacman` is the native package manager used by Manjaro and Arch Linux.

Search for a package:

```bash
pacman -Ss firefox
```

Install a package:

```bash
sudo pacman -S package-name
```

Remove a package:

```bash
sudo pacman -Rns package-name
```

Update the complete system:

```bash
sudo pacman -Syu
```

## Pamac

`pamac-cli` provides Manjaro's higher-level package-management interface from the terminal.

Example:

```bash
pamac search package-name
```

## yay and the AUR

`yay` is preinstalled together with the build tools required for compiling many AUR packages.

Example:

```bash
yay -S package-name
```

The **Arch User Repository (AUR)** is community maintained. AUR packages are not official Manjaro packages, so review PKGBUILDs and use appropriate caution before installing third-party software.

---

# Desktop environments under WSL

This release intentionally contains **no desktop environment**.

The clean base makes it easier to experiment with graphical Linux desktops without mixing desktop-specific problems into the WSL base itself.

Possible environments include:

| Desktop | WSL possibility |
|---|---|
| KDE Plasma 6 | Yes |
| GNOME | Yes |
| XFCE | Yes |
| Cinnamon | Possible |
| Deepin / DDE | Experimental depending on packages/session |
| Budgie | Possible |
| Openbox and other window managers | Yes |

Graphical desktops under WSL can behave differently from a normal bare-metal Linux installation. WSLg or a third-party X server such as X410 may be required depending on the desktop and session type.

Desktop installation scripts can therefore be maintained separately from the base WSL image.

---

# Why use Manjaro in WSL?

Manjaro under WSL is useful for:

- Linux development from Windows
- Arch/Manjaro package testing
- Shell scripting
- Java, Node.js, Python and other development stacks
- Git and GitHub workflows
- Testing packages with `pacman`, Pamac and `yay`
- Learning Manjaro without repartitioning a computer
- Running Linux command-line tools beside Windows applications
- Experimenting with WSLg and Linux desktops

WSL is not a complete replacement for a native Manjaro installation. Hardware management, boot loaders, kernel installation and some low-level Linux functionality work differently because WSL2 runs Linux inside Microsoft's virtualized environment.

---

# Project philosophy

The goal of this project is simple:

> **A clean Manjaro base for WSL that installs easily, passes a useful system health check and leaves the choice of desktop and applications to the user.**

The base should remain reliable and relatively small while still containing the tools needed to start working immediately.

---

# Release 0.1.1

Release page:

https://github.com/vinberg88/manjaro/releases/tag/0.1.1

Main WSL image:

```text
Manjaro-WSL-Base-0.1.1-x86_64.wsl
```

Release files include:

```text
Manjaro-WSL-Base-0.1.1-x86_64.wsl
MANIFEST.txt
README.txt
SHA256SUMS
```

---

# Useful links

- Email me: mattiasvinberg@duck.com
- My GitHub: https://github.com/vinberg88
- More WSL/Linux projects: https://github.com/vinberg88/opensuse
- YouTube: https://www.youtube.com/@mattiasvinberg
- Page about WSL: https://vinberg88.github.io/

---

**Manjaro + WSL2 = a powerful rolling Linux development environment inside Windows.** 🚀
