The `dpkg` command in Linux is the low-level package manager for Debian-based distributions like Ubuntu. It is used to install, remove, and manage `.deb` packages. Here's a list of common `dpkg` commands, along with example outputs:

### 1. **Install a `.deb` package:**
   ```bash
   sudo dpkg -i <package_name>.deb
   ```

   Example:
   ```bash
   sudo dpkg -i mypackage.deb
   ```

   **Output:**
   ```
   Selecting previously unselected package mypackage.
   (Reading database ... 12345 files and directories currently installed.)
   Preparing to unpack mypackage.deb ...
   Unpacking mypackage (1.0) ...
   Setting up mypackage (1.0) ...
   ```

---

### 2. **Remove an installed package:**
   ```bash
   sudo dpkg -r <package_name>
   ```

   Example:
   ```bash
   sudo dpkg -r mypackage
   ```

   **Output:**
   ```
   (Reading database ... 12345 files and directories currently installed.)
   Removing mypackage (1.0) ...
   ```

---

### 3. **Purge (remove) an installed package and its configuration files:**
   ```bash
   sudo dpkg -P <package_name>
   ```

   Example:
   ```bash
   sudo dpkg -P mypackage
   ```

   **Output:**
   ```
   (Reading database ... 12345 files and directories currently installed.)
   Purging mypackage (1.0) ...
   ```

---

### 4. **List all installed packages:**
   ```bash
   dpkg -l
   ```

   Example:
   ```bash
   dpkg -l
   ```

   **Output:**
   ```
   Desired=Unknown/Install/Remove/Purge/Hold
   | Status=Not/Installed/Configured/Unpacked/Failed-Config/Half-Installed
   |/ Error?=(none)/Reinst-required (Status,Err: uppercase=bad)
   ||/ Name                   Version                Architecture            Description
   +++-======================-======================-======================-=======================================================
   ii  bash                   5.0-6ubuntu1.1         amd64                  GNU Bourne Again SHell
   ii  libc6                  2.31-0ubuntu9.9        amd64                  GNU C Library: Shared libraries
   ```

---

### 5. **Show information about a specific package:**
   ```bash
   dpkg -s <package_name>
   ```

   Example:
   ```bash
   dpkg -s bash
   ```

   **Output:**
   ```
   Package: bash
   Status: install ok installed
   Priority: important
   Section: shells
   Installed-Size: 1168
   Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
   Architecture: amd64
   Version: 5.0-6ubuntu1.1
   Depends: libc6 (>= 2.17)
   Description: GNU Bourne Again SHell
   ```

---

### 6. **List files installed by a specific package:**
   ```bash
   dpkg -L <package_name>
   ```

   Example:
   ```bash
   dpkg -L bash
   ```

   **Output:**
   ```
   /.
   /usr
   /usr/bin
   /usr/bin/bash
   /usr/share
   /usr/share/man
   /usr/share/man/man1
   /usr/share/man/man1/bash.1.gz
   ```

---

### 7. **List the package that installed a specific file:**
   ```bash
   dpkg -S <file_name>
   ```

   Example:
   ```bash
   dpkg -S /usr/bin/bash
   ```

   **Output:**
   ```
   bash: /usr/bin/bash
   ```

---

### 8. **Check for missing dependencies (after using dpkg -i to install a package):**
   ```bash
   sudo dpkg --configure -a
   ```

   Example:
   ```bash
   sudo dpkg --configure -a
   ```

   **Output:**
   ```
   (Reading database ... 12345 files and directories currently installed.)
   Setting up mypackage (1.0) ...
   ```

---

### 9. **Fix broken dependencies:**
   ```bash
   sudo apt-get install -f
   ```

   (Although `apt-get` is not a `dpkg` command, it can be used to fix broken dependencies after `dpkg` operations.)

---

### 10. **Check the status of the package database:**
   ```bash
   dpkg --audit
   ```

   Example:
   ```bash
   dpkg --audit
   ```

   **Output:**
   ```
   dpkg: error: could not open package info file '/var/lib/dpkg/status': No such file or directory
   ```

---

### 11. **List all available `dpkg` options (help):**
   ```bash
   dpkg --help
   ```

   **Output:**
   ```
   Usage: dpkg [option...] <package_file...>
   Options:
     -?, --help            Show this help message
     -D, --debug           Enable debugging output
     -i, --install         Install the package(s)
     -r, --remove          Remove the package(s)
     -P, --purge           Purge the package(s)
     -L, --listfiles       List files installed by package
     -S, --search          Search for a package owning a file
     -s, --status          Show package information
   ```

---
