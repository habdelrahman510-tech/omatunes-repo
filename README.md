# Omatunes pacman repository

A small binary pacman repository for [Omatunes](https://github.com/habdelrahman510-tech/Omatunes-Deluxe),
the Wayland music player for Omarchy. It exists so the player can be installed
and updated with `pacman -Syu` while the AUR has new account registration
paused.

## Install

Add the repository above the Arch mirrors in `/etc/pacman.conf`:

```ini
[omatunes-bin]
SigLevel = Optional TrustAll
Server = https://habdelrahman510-tech.github.io/omatunes-repo/x86_64
```

Then install:

```bash
sudo pacman -Sy omatunes-bin
```

`yay -Syu` and `paru -Syu` pick it up too, since both wrap pacman.

## Updates

Every Omatunes release is added here as a new `pkgver-pkgrel`, so a plain
`sudo pacman -Syu` keeps the player current. Nothing else in this repository
changes.

## What `TrustAll` means

The packages and the database are not GPG-signed, so `SigLevel = Optional
TrustAll` tells pacman to install them without verifying a signature. You are
trusting this GitHub account and GitHub Pages' TLS. If that is not a trade you
want to make, build from source instead:

```bash
git clone https://github.com/habdelrahman510-tech/Omatunes-Deluxe
cd Omatunes-Deluxe/packaging/omatunes && makepkg -si
```

## Removing the repository

```bash
sudo pacman -Rns omatunes-bin
```

and delete the three lines from `/etc/pacman.conf`.
