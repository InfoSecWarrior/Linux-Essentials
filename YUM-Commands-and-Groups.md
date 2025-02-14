# YUM Command Reference

**YUM** (Yellowdog Updater, Modified) is a package manager for RPM-based Linux distributions like CentOS, RHEL, and Fedora. It simplifies the process of installing, updating, and managing software packages.

---

## Syntax

```
yum [options] <subcommand> [arguments]
```

---

## Common Subcommands

| **Subcommand**    | **Description**                                       | **Common Options/Arguments**                             |
|-------------------|-------------------------------------------------------|----------------------------------------------------------|
| `install`         | Installs one or more packages                         | `<package_name>`, `--nogpgcheck`                         |
| `update`          | Updates packages                                      | `[<package_name>]`, `-y`                                 |
| `upgrade`         | Updates packages and handles obsoletes                | `[<package_name>]`                                       |
| `remove`          | Removes one or more packages                          | `<package_name>`                                         |
| `list`            | Lists packages                                        | `installed`, `available`, `updates`, `<package_name>`    |
| `info`            | Displays package information                          | `<package_name>`                                         |
| `search`          | Searches packages by keyword                          | `<keyword>`                                              |
| `provides`        | Finds which package provides a file                   | `<file_name>`                                            |
| `repolist`        | Lists repositories                                    | `all`, `enabled`, `disabled`                             |
| `clean`           | Cleans cached data                                    | `all`, `packages`, `metadata`                            |
| `groupinstall`    | Installs a group of packages                          | `"<group_name>"`                                         |
| `groupremove`     | Removes a group of packages                           | `"<group_name>"`                                         |
| `grouplist`       | Lists available package groups                        | `hidden`, `groups`                                       |
| `groupinfo`       | Displays information about a package group            | `"<group_name>"`                                         |
| `history`         | Displays transaction history                          | `list`, `info`, `undo`, `redo`, `rollback`               |
| `check-update`    | Checks for available package updates                  | None                                                     |
| `makecache`       | Downloads and caches repository data                  | None                                                     |
| `downgrade`       | Downgrades a package to an earlier version            | `<package_name>`                                         |
| `deplist`         | Displays dependencies of a package                    | `<package_name>`                                         |
| `reinstall`       | Reinstalls a package                                  | `<package_name>`                                         |
| `distrosync`      | Synchronizes installed packages to the latest versions| None                                                     |

---

## Viewing YUM Version

To see the version of YUM installed:

```
yum --version
```

---

## Managing Repositories

### List Enabled Repositories

Lists all currently enabled repositories:

```
yum repolist
```

### List All Repositories

Lists all repositories configured on your system, including both enabled and disabled ones:

```
yum repolist all
```

### Enable a Repository

You can enable a repository by:

1. Manually editing the repository file in `/etc/yum.repos.d/` and setting `enabled=1`.

2. Using the command:

   ```
   yum config-manager --enable <repo-id>
   ```

---

## Listing Packages

### List All Packages

Shows all packages (installed and available):

```
yum list
```

### List Installed Packages Only

```
yum list installed
```

### List Available Packages Only

```
yum list available
```

### List Recently Added Packages

```
yum list recent
```

### List Extras

Lists installed packages that are not available from any enabled repository (orphaned or manually installed packages):

```
yum list extras
```

---

## Checking for Updates

### Check for Available Updates

Checks for available updates for installed packages without installing them:

```
yum check-update
```

---

## Updating Packages

### Update All Packages

Updates existing packages without changing or replacing any packages:

```
yum update
```

- Does not replace or remove obsolete packages.

### Update a Specific Package

Updates a specified package only:

```
yum update <package-name>
```

### Upgrade Packages

Performs all actions of `yum update` and also handles obsolete packages by replacing them with their updated counterparts:

```
yum upgrade
```

### Upgrade a Specific Package

```
yum upgrade <package-name>
```

---

## Searching and Getting Information

### Search for Packages

Searches for packages related to a specified string in all enabled YUM repositories:

```
yum search <string>
```

### Get Information About a Package

Provides all information about a package:

```
yum info <package-name>
```

---

## Installing and Removing Packages

### Install Packages

Installs one or more packages:

```
yum install <package-name>
```

- Example:

  ```
  yum install nmap
  ```

- To install multiple packages matching a pattern:

  ```
  yum install bash*
  ```

### Remove Packages

Uninstalls a package:

```
yum remove <package-name>
```

- **Note**: Do not use wildcards when removing packages, as it may remove necessary dependencies leading to system instability.

---

## Finding Which Package Provides a File

Searches for packages that provide a file or capability matching the specified keyword:

```
yum provides <string>
```

- Example:

  ```
  yum provides ifconfig
  ```

---

## Downgrading, Reinstalling, and Checking Dependencies

### Downgrade a Package

Reverts or downgrades an installed package to an earlier version:

```
yum downgrade <package-name>
```

- Automatically handles dependencies, ensuring required packages are also downgraded if necessary.

### Reinstall a Package

Reinstalls a package:

```
yum reinstall <package-name>
```

### Display Dependencies of a Package

Shows dependencies of a package and providers of it:

```
yum deplist <package-name>
```

---

## Cleaning YUM Cache

### Clean All Cache

Clears the YUM cache:

```
yum clean all
```

- Removes:

  - **Package Cache** (`/var/cache/yum/`): Removes all cached `.rpm` packages.
  - **Metadata Cache** (`/var/cache/yum/*`): Clears repository metadata to force re-download.
  - **Headers and XML Data** (`/var/lib/yum/`): Removes old repository data and `repomd.xml` files.

### Generate Cache

Rebuilds the YUM cache:

```
yum makecache
```

- Cache location: `/var/cache/dnf` (depending on system configuration).
- If issues persist, manually remove files from the cache directory and regenerate the cache:

  ```
  rm -rf /var/cache/dnf/*
  yum makecache
  ```

---

## Viewing YUM Transaction History

Displays the transaction history of YUM (installations, updates, removals):

```
yum history
```

---

## Synchronizing Packages

Synchronizes installed packages to match the latest available versions in the repository, updating, downgrading, or reinstalling packages as needed:

```
yum distrosync
```

---

## Using Package Groups

A group in YUM is a collection of related software packages bundled together for easier management.

### List All Groups

Lists all package groups (installed and available):

```
yum grouplist
```

### Install a Package Group

Installs a group of packages:

```
yum groupinstall "<group-name>"
```

- Example:

  ```
  yum groupinstall "Development Tools"
  ```

- Important groups:

  - Minimal Install
  - Server with GUI
  - Development Tools
  - Security Tools
  - System Tools
  - GNOME Desktop Environment

### Remove a Package Group

Removes a group of packages:

```
yum groupremove "<group-name>"
```

### Get Information About a Package Group

Shows group info, including the packages it contains:

```
yum groupinfo "<group-name>"
```
