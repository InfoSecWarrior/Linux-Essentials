# Working with Debian Packages Using dpkg

Debian-based distributions (e.g., Debian, Ubuntu, Kali Linux, Raspberry Pi OS) rely on the dpkg tool for low-level package management of .deb files. While Debian can also install RPM packages, dpkg is the native and most reliable approach for installing and managing Debian packages. This guide consolidates various dpkg commands, example outputs, and best practices.

-------------------------------------------------------------------------------
## Verifying You’re on Debian

  Using dpkg or rpm alone doesn’t guarantee you’re on Debian. Check release files:
  
  ```
  ls -lh /etc/*-release
  ```
  
  ```
  cat /etc/os-release
  ```

  Typical output might be:
  ```
  PRETTY_NAME="Debian GNU/Linux 12 (bookworm)"
  NAME="Debian GNU/Linux"
  VERSION_ID="12"
  VERSION="12 (bookworm)"
  VERSION_CODENAME=bookworm
  ID=debian
  HOME_URL="https://www.debian.org/"
  SUPPORT_URL="https://www.debian.org/support"
  BUG_REPORT_URL="https://bugs.debian.org/"
  ```

  Key fields:
  - NAME: OS Name (Debian GNU/Linux)  
  - VERSION_ID: Version number (e.g., 12)  
  - VERSION_CODENAME: Codename (e.g., bookworm)  
  - PRETTY_NAME: Human-readable name (e.g., Debian GNU/Linux 12 (bookworm))  
  - ID: OS identifier (debian)
  
  Debian has a version/codename cycle (buster, bullseye, bookworm, trixie…).

-------------------------------------------------------------------------------
## Check System Architecture

  ```
  dpkg --print-architecture
  ```
  
  Displays your system’s architecture (e.g., amd64), ensuring you download and install matching .deb packages.

-------------------------------------------------------------------------------
## Command Reference Overview

  In the Debian ecosystem, several commands/tools exist for package management:
  
  - **dpkg**: Install, remove, and manage .deb packages at a low level.  
  - **dpkg-deb**: Work with `.deb` files (list or extract) without installing them.  
  - **dpkg-query**: Query package databases for information.  
  - **dpkg-reconfigure**: Reconfigure installed packages.  
  - **dpkg-divert**: Prevent files from being overwritten by a package.  
  - **dpkg-statoverride**: Override file ownership/permissions set by packages.  
  - **apt / apt-get**: Higher-level package management tools that provide dependency resolution.  
  - **apt-cache**: Query package metadata (e.g., searching or listing versions).  
  - **aptitude**: A full-featured package management interface (text-based UI).
  
  (Note: This guide primarily focuses on dpkg and dpkg-deb, with references to apt/apt-get for dependency resolution.)

-------------------------------------------------------------------------------
## dpkg

  dpkg is the core tool for managing installed packages on Debian-based systems.
  
### Key dpkg Commands

- Install a .deb Package

```
dpkg -i package-name.deb
```

- Remove a Package (Keep Config Files)

```
dpkg -r package-name
```

Uninstalls the package but keeps configuration files. We can also use `--remove`

- Purge a Package (Remove Everything)

```
dpkg -P package-name
```

Completely removes a package, including config files.

- List Installed Packages

```
dpkg -l
```

Shows installed packages with two-letter status codes.

Example output:
```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Configured/Unpacked/Failed-Config/Half-Installed
|/ Error?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                   Version                Architecture            Description
+++-======================-======================-======================-=======================================================
ii  bash                   5.0-6ubuntu1.1         amd64                  GNU Bourne Again SHell
ii  libc6                  2.31-0ubuntu9.9        amd64                  GNU C Library: Shared libraries
```

#### Understanding the Two-Letter Status Codes
- First Letter (Desired State / User Action):
  - i → Installed (The package should be installed)
  - r → Removed (Package removed, config files remain)
  - p → Purged (Package completely removed, no configs left)
  - u → Unknown (Never installed)
  - h → Half-installed (Installation interrupted)

- Second Letter (Current State / System Status):
  - i → Installed (Package is properly installed)
  - U → Unpacked (Not yet configured)
  - F → Failed (Install/Configure failed)
  - C → Config-files (Only config files remain)
  - n → Not-installed (Package is not on the system)


- Check if a Package is Installed
  
  ```
  dpkg -s package-name
  ```
    Displays status and details of a package.

  Output:
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

- Get Details of an Installed Package

  ```
  dpkg -p package-name
  ```
  
  Fetches metadata from the APT/dpkg database (even if not installed).

- List Files Installed by a Package

  ```
  dpkg -L package-name
  ```
  
  Shows which files were placed by that package.

- Find the Package Owning a File
  
  ```
  dpkg -S /usr/bin/groups
  ```
  
  Identifies the installed package providing the file.

  Output:
  ```
  coreutils: /usr/bin/groups
  ```
  
- Reconfigure a Package

  ```
  dpkg-reconfigure package-name
  ```
  
  Re-runs the package’s configuration scripts to change settings without reinstalling.
  
- Handle Partially Installed or Broken Packages

  ```
  dpkg --configure -a
  ```
  
  Completes the configuration of packages left unconfigured.
  
- Verify Installed Package Files
  
  ```
  dpkg --verify package-name
  ```
  
  Checks if installed files differ from the package’s metadata.
  
- Check the status of the package database:

  ```
  dpkg --audit
  ```
  
-------------------------------------------------------------------------------
## dpkg-deb

dpkg-deb operates on `.deb` files directly, letting you list or extract contents without installing them.

### Inspecting a .deb File

- List Contents
  
  ```
  dpkg-deb -c package-name.deb
  ```
  or
  ```
  dpkg --contents package-name.deb
  ```
  
  Displays file paths within the package.

- Extracting a .deb Without Installing
  
  ```
  dpkg-deb -xv package-name.deb /destination
  ```
  
  - -x extracts package files  
  - -v verbose output
  
  Example:
  ```
  dpkg-deb -xv google-chrome-stable_current_amd64.deb /chrome-data
  ```
  
  Unpacks files into `/chrome-data`, leaving the system unaffected.
  
-------------------------------------------------------------------------------
## dpkg-query

  An alternative tool for querying installed packages:
  
  ```
  dpkg-query --search /path/to/file
  ```
  
  Finds which package owns a given file (similar to dpkg -S).
  
  ```
  dpkg-query --list
  ```
  
  Equivalent to `dpkg -l`, listing installed packages.

-------------------------------------------------------------------------------
## Additional Commands

### dpkg-divert
  
  Prevents certain files from being overwritten by a package installation or upgrade, by diverting them to different paths.
  
  ```
  dpkg-divert --add /usr/bin/example
  ```

### dpkg-statoverride

  Allows overriding the ownership or permissions of files handled by packages.
  
  ```
  dpkg-statoverride --add root root 0755 /usr/bin/example
  ```
