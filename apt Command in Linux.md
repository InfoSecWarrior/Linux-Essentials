
The `apt` command in Linux is a package management tool used primarily in Debian-based distributions like Ubuntu. It simplifies the process of installing, updating, upgrading, and removing software packages.


### **Updating Package Lists**
- `sudo apt update` — Updates the list of available packages and their versions.
- `sudo apt upgrade` — Installs available updates for all installed packages.
- `sudo apt full-upgrade` — Upgrades packages with dependency changes, possibly removing some.

---

### **Installing Packages**
- `sudo apt install <package_name>` — Installs a package.
- `sudo apt install ./file.deb` — Installs a local `.deb` file.
- `sudo apt reinstall <package_name>` — Reinstalls a package.

---

### **Removing Packages**
- `sudo apt remove <package_name>` — Removes a package but leaves config files.
- `sudo apt purge <package_name>` — Removes a package along with its config files.
- `sudo apt autoremove` — Removes unneeded dependencies.

---

### **Searching & Info**
- `apt search <keyword>` — Searches for packages related to a keyword.
- `apt show <package_name>` — Displays details about a package.
- `apt list --installed` — Lists installed packages.
- `apt list --upgradable` — Lists packages with available updates.

---

### **Cleaning Up**
- `sudo apt clean` — Clears the local cache of downloaded packages.
- `sudo apt autoclean` — Clears outdated package files.

---
