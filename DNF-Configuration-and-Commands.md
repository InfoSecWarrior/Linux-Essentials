# DNF Configuration on CentOS 9

DNF (Dandified YUM) is the modern package manager for RPM-based systems, replacing YUM with improved performance, enhanced dependency management, and modular support. Below is a quick-reference guide for basic and advanced DNF usage on CentOS 9.

-------------------------------------------------------------------------------
# Using DNF

DNF improves upon YUM with better performance, enhanced dependency resolution, and support for modular content. Below are DNF commands organized by category.

-------------------------------------------------------------------------------
## DNF Configuration Files

"DNF configuration (both online and offline) follows the same approach as YUM. For more details, please refer to [YUM-Configure-Offline.md](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/YUM-Configure-Offline.md) and [YUM-Configure-Online.md](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/YUM-Configure-Online.md)."

DNF uses two primary types of configuration files:

1. Global Configuration ( /etc/dnf/dnf.conf )  
   - Defines overall DNF settings such as GPG signature checks, kernel package retention limits, and whether to remove unused dependencies automatically.
   
2. Repository Configuration ( /etc/yum.repos.d/*.repo )  
   - Each .repo file describes one or more software repositories, including their base URL, GPG settings, and whether they are enabled.

---

## Basic DNF Commands

• Install a Package:
```
dnf install package-name
```
Installs the specified package (plus any required dependencies).

• Remove a Package:
```
dnf remove package-name
```
Uninstalls the specified package from your system.

• Update Packages:
```
dnf update
```
Checks for available updates and installs them for packages currently installed.

• Search for Packages:
```
dnf search keyword
```
Finds packages whose names or descriptions match the specified keyword.

• List Installed Packages:
```
dnf list installed
```
Displays all packages currently installed on the system.

• Get Package Information:
```
dnf info package-name
```
Shows detailed metadata (version, repository, size) about a specified package.

---

## Advanced DNF Commands

• List Package Dependencies:
```
dnf deplist package-name
```
Shows all dependencies required by the package.

• Download a Package without Installing:
```
dnf download package-name
```
Retrieves the RPM file locally without installing it.

• Reinstall a Package:
```
dnf reinstall package-name
```
Reinstalls a package to restore missing or corrupted files.

• Clean DNF Cache:
```
dnf clean all
```
Removes cached package data and metadata.

• Distribution Synchronization:
```
dnf distro-sync
```
Ensures installed packages match versions in the repositories; can upgrade, downgrade, or reinstall as needed.

• Automatic Removal of Unused Dependencies:
```
dnf autoremove
```
Removes previously installed packages no longer required by any installed software.

---

## DNF Groups

DNF can install groups of packages categorized under a common purpose.

• List Available Groups:
```
dnf group list
```
Displays all package groups available for installation.

• Install a Group:
```
dnf groupinstall "Group Name"
```
Installs all packages in a specified group.

• Remove a Group:
```
dnf groupremove "Group Name"
```
Removes packages associated with that group.

---

## Modular Content Management

DNF supports module streams, allowing multiple versions of the same software to coexist.

• List Available Modules:
```
dnf module list
```
Displays modules and their available streams.

• Enable a Module Stream:
```
dnf module enable module-name:stream
```
Activates a particular stream version for a module.

• Install a Module:
```
dnf module install module-name
```
Installs module content from the chosen stream.

• Disable a Module:
```
dnf module disable module-name
```
Deactivates the currently enabled stream for a module.

• Reset a Module:
```
dnf module reset module-name
```
Clears any enable/disable state, returning the module to its default settings.

---

## DNF Plugins

Plugins extend DNF’s functionality.

• List Installed Plugins:
```
dnf debuginfo-status
```
(Actual output may vary based on installed packages.)

• Install a Plugin:
```
dnf install dnf-plugins-core
```
Installs a collection of core plugins for DNF.

Some useful plugins include:  
- dnf-automatic: Automate updates.  
- dnf-versionlock: Lock specific package versions.  
- dnf-download: Download packages without installing.

---

## Transaction History and Rollback

DNF maintains a history of transactions, allowing you to view past actions and undo them if needed.

• View Transaction History:
```
dnf history
```
Displays a chronological list of installs, updates, and removals.

• View Details of a Transaction:
```
dnf history info transaction-id
```
Shows the actions taken in a specific transaction.

• Undo a Transaction:
```
dnf history undo transaction-id
```
Attempts to revert changes from a specific transaction (limited by dependency complexities).

---

## Troubleshooting DNF

### Clearing Cache and Metadata

• Clean Cache:
```
dnf clean all
```
Removes cached package and metadata files.

• Rebuild Metadata Cache:
```
dnf makecache
```
Downloads fresh metadata from enabled repositories.

### Resolving Dependency Issues

• Check for Broken Dependencies:
```
dnf check
```
Verifies installed packages for unsatisfied dependencies.

• Attempt to List Unsatisfied Dependencies:
```
dnf repoquery --unsatisfied
```
Shows packages that have missing dependencies.

### Verifying Package Integrity

• Verify Installed Packages:
```
rpm -Va
```
Checks installed files for discrepancies like size, MD5 sums, and permissions.

• Reinstall Corrupted Packages:
```
dnf reinstall package-name
```
Restores missing or altered package files.

### Network and Repository Connectivity

• Temporarily Disable a Slow or Unresponsive Repository:
```
dnf --disablerepo=repo-id ...
```
Skips specified repository(ies) for the current command.

• Importing GPG Keys:
```
rpm --import /path/to/RPM-GPG-KEY
```
Adds a GPG public key to verify package signatures.
