# APT (Advanced Package Tool)

A comprehensive guide to using APT (Advanced Package Tool) for package management on Debian-based systems. This repository serves as a quick reference for common and advanced APT commands.

## Table of Contents
1. [Basic Package Management](#basic-package-management)
2. [Package Search and Information](#package-search-and-information)
3. [Package Upgrades](#package-upgrades)
4. [Package Removal](#package-removal)
5. [Source and Dependency Management](#source-and-dependency-management)

---

## Basic Package Management

Update all installed packages.
```bash
apt update
```

Install a package.
```bash
apt install ssh
```

Install multiple packages.
```bash
apt install vim nmap openssh
```

Install package with wildcard.
```bash
apt install zsh*
```

Reinstall a package.
```bash
apt reinstall
```

---

## Package Search and Information

Search for a package.
```bash
apt search vim
```

Show package details.
```bash
apt show vim
```

List all available packages.
```bash
apt list
```

Show all upgradable packages.
```bash
apt list --upgradable
```

Upgrade all installed packages.
```bash
apt list upgrade
```

---

## Package Upgrades 

Upgrade all installed packages.
```bash
apt upgrade
```

Perform a Full Upgrade (Including Dependencies).
```bash
apt full-upgrade
```

Upgrade to latest distribution.
```bash
apt dist-upgrade
```

Upgrade specific package.
```bash
apt install --only-upgrade vim
```

---

## Package Removal

Remove a package.
```bash
apt remove zsh
```

Remove package with wildcard.
```bash
apt remove zsh*
```

Completely Remove a Package (Including Configuration Files)
```bash
apt purge zsh
```

Remove unused packages.
```bash
apt autoremove
```

Remove unused packages in cache.
```bash
apt autoclean
```

Remove & purge a package.
```bash
apt remove --purge zsh
```

Clean package cache.
```bash
apt clean
```

---

## Source and Dependency Management

Download a package.
```bash
apt download vim
```

Show package dependencies.
```bash
apt depends vim
```

SHow Reverse dependencies of the package.
```bash
apt rdepends vim
```

Source packet info of the package.
```bash
apt showsrc vim
```

Download source of the package.
```bash
apt source vim
```

Show changelog of the package.
```bash
apt changelog vim
```

Fix broken packages.
```bash
apt --fix-broken install
```

---
