# Advanced Package Tool (APT)

## Overview
The Advanced Package Tool (APT) is a high-level package management system used in Debian-based Linux distributions, including Ubuntu, Kali Linux, and Raspberry Pi OS. It provides an easy interface to interact with the `dpkg` package manager and handles dependency resolution automatically.

## Common APT Commands

### 1. Update the Package List
Before installing or upgrading packages, always update the package list:
```sh
apt update
```
This fetches the latest package information from the repositories.

### 2. Upgrade Installed Packages
To upgrade all installed packages to their latest versions:
```sh
apt list --upgradable
apt upgrade -y
```
To perform a full upgrade (includes removing obsolete packages if necessary):
```sh
apt full-upgrade -y
```
To upgrade the entire system while handling dependency changes and removing obsolete packages:
```sh
apt dist-upgrade -y
```

### 3. Install a Package
To install a package:
```sh
apt install package_name
```
Example:
```sh
apt install nginx
```

### 4. Remove a Package
To remove a package but keep its configuration files:
```sh
apt remove package_name
```
Example:
```sh
apt remove nginx
```
To completely remove a package along with its configuration files:
```sh
apt purge package_name
```
Example:
```sh
apt purge nginx
```

### 5. Search for a Package
If you don't know the exact package name, you can search for it:
```sh
apt search package_name
```
Example:
```sh
apt search nginx
```

### 6. Show Package Information
To display detailed information about a package:
```sh
apt show package_name
```
Example:
```sh
apt show nginx
```

### 7. List Installed Packages
To list all installed packages:
```sh
apt list
```
To count the installed packages:
```sh
apt list | wc -l
```
To list only installed packages:
```sh
apt list --installed
```
To count installed packages:
```sh
apt list --installed | wc -l
```

### 8. Find Dependencies of a Package
To check dependencies of a package:
```sh
apt depends package_name
```
Examples:
```sh
apt depends vlc
apt depends nginx
```

### 9. Remove Unused Packages
To remove packages that were automatically installed as dependencies but are no longer needed:
```sh
apt autoremove -y
```

### 10. Clean Up Package Cache
APT caches downloaded package files in `/var/cache/apt/archives/`. To clear them and free up space:
```sh
apt clean
```
To remove only outdated package files:
```sh
apt autoclean
```

### 11. Reinstall a Package
To reinstall a package without removing its dependencies (useful for fixing corrupted or misconfigured packages):
```sh
apt reinstall package_name
```
Example:
```sh
apt reinstall nginx
```

## Managing APT Repositories (/etc/apt/sources.list)

### Overview
The `/etc/apt/sources.list` file contains a list of software repositories from which APT fetches packages. It can be edited to add or modify repositories.

### Useful Sources List Generators
- [SimplyLinux Debian Generator](https://debgen.simplylinux.ch/)
- [Debian Sources Generator (GitHub)](https://debgen.github.io/) [(Alternative)](https://debgen.xyz/)
- [Debian Wiki on Sources List](https://wiki.debian.org/SourcesList)

### Editing the sources.list File
To edit the sources list:
```sh
vim /etc/apt/sources.list
```
Example: Default Debian 12 (Bookworm) Sources List:
```sh
deb http://deb.debian.org/debian bookworm main contrib non-free non-free-firmware
deb http://security.debian.org/debian-security bookworm-security main contrib non-free non-free-firmware
deb http://deb.debian.org/debian bookworm-updates main contrib non-free non-free-firmware
```

### Fixing Issues with sources.list
Ensure the correct Debian version is in `/etc/os-release`:
```sh
cat /etc/os-release
```
Replace `bookworm` with the correct version (e.g., `bullseye`, `buster`) in `sources.list`.

#### If GPG Signature Errors Appear
Add missing keys:
```sh
apt install debian-archive-keyring
```

