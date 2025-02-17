# Advanced Package Tool (APT)

The Advanced Package Tool (APT) is a high-level package management system used in Debian-based Linux distributions, including Ubuntu, Kali Linux, and Raspberry Pi OS. It provides an easy interface to interact with the dpkg package manager and handles dependency resolution automatically.

-------------------------------------------------------------------------------
## Common apt Commands

1. Update the Package List

   ```
   apt update
   ```
   Before installing or upgrading packages, always update the package list. This fetches the latest package information from the repositories.

2. Upgrade Installed Packages

   To upgrade all installed packages to their latest versions:
   ```
   apt list --upgradable
   ```
   ```
   apt upgrade -y
   ```
   To perform a full upgrade (includes removing obsolete packages if necessary):
   ```
   apt full-upgrade -y
   ```
   To upgrade the entire system, similar to apt upgrade, but with the added ability to handle dependency changes and remove obsolete packages:
   ```
   apt dist-upgrade -y
   ```

3. Install a Package

   ```
   apt install package_name -y
   ```
   Example:
   ```
   apt install nginx
   ```

4. Remove a Package

   To remove a package but keep its configuration files:
   ```
   apt remove package_name -y
   ```
   Example:
   ```
   apt remove nginx
   ```
   To remove a package along with its configuration files:
   ```
   apt remove --purge package_name -y
   ```

5. Remove Unused Packages

   ```
   apt autoremove -y
   ```
   Removes packages that were automatically installed as dependencies but are no longer needed.

6. Search for a Package

   If you don't know the exact package name, you can search for it:
   ```
   apt search package_name
   ```
   Example:
   ```
   apt search nginx
   ```

7. Show Package Information

   To display detailed information about a package:
   ```
   apt show package_name
   ```
   Example:
   ```
   apt show nginx
   ```

8. List Installed Packages

   ```
   apt list
   ```
   ```
   apt list | wc -l
   ```
   ```
   apt list --installed
   ```
   ```
   apt list --installed | wc -l
   ```

9. Clean the Cache (/var/cache/apt/archives/)

   ```
   apt autoclean
   ```

10. Reinstall a Package

   ```
   apt reinstall package_name
   ```
   Reinstalls a package without removing its dependencies. This is useful when a package is corrupted or misconfigured.

11. Download a Package

   ```
   apt download <package-name>
   ```
   Saves the .deb package file in the current directory for manual installation or offline use.  
   Example:
   ```
   apt download nmap
   ```

12. Check Package Dependencies

   ```
   apt depends <package-name>
   ```
   Lists the dependencies required for a package. This helps understand which additional packages need to be installed for proper functionality.  
   Example:
   ```
   apt depends nmap
   ```

13. Check Reverse Dependencies

   ```
   apt rdepends <package-name>
   ```
   Shows which other packages depend on a specific package. Useful before removing a package.  
   Example:
   ```
   apt rdepends nmap
   ```

14. View Package Source Information

   ```
   apt showsrc <package-name>
   ```
   Retrieves source package details (metadata and upstream source).  
   Example:
   ```
   apt showsrc nmap
   ```

15. Download the Source Code of a Package

   ```
   apt source <package-name>
   ```
   Fetches the package source into the current directory for modification or compilation.  
   Example:
   ```
   apt source nmap
   ```

16. View Package Changelog

   ```
   apt changelog <package-name>
   ```
   Checks the recent updates and fixes applied to the package.  
   Example:
   ```
   apt changelog nmap
   ```

-------------------------------------------------------------------------------
## Fixing Common apt Errors

1. Fix Broken Dependencies

   ```
   apt --fix-broken install
   ```

2. Force Reconfiguration of Packages

   ```
   dpkg --configure
   ```

3. Unlock apt When Another Process Is Using It

   ```
   rm /var/lib/dpkg/lock
   ```
   ```
   rm /var/lib/dpkg/lock-frontend
   ```

-------------------------------------------------------------------------------
## Other APT Tools

1. Search for a Package

   To search for a package in the available repositories via apt-cache:
   ```
   apt-cache search <package-name>
   ```
   Returns a list of packages related to the given keyword.

2. Display Package Details

   ```
   apt show <package-name>
   ```
   Shows metadata such as version, description, and dependencies.

3. Check Package Dependencies

   ```
   apt-cache depends <package-name>
   ```
   Lists the dependencies for a package.  
   To see which packages depend on the given package:
   ```
   apt-cache rdepends <package-name>
   ```

4. View Source Package Information

   ```
   apt-cache showsrc <package-name>
   ```
   Useful when working with package source code.

5. List Available Packages

   ```
   apt-cache pkgnames
   ```
   Outputs a list of all packages known to the system.

6. Check Package Policy

   ```
   apt-cache policy <package-name>
   ```
   Shows the installed and available versions of the package, including repository sources.

7. Update and Upgrade Packages

   ```
   apt-get update
   ```
   Updates the package list.

   ```
   apt-get upgrade -y
   ```
   Upgrades all installed packages.

   ```
   apt-get full-upgrade
   ```
   Performs a full system upgrade.

8. Install and Remove Packages

   ```
   apt-get install <package-name>
   ```
   Installs a package.

   ```
   apt-get remove <package-name>
   ```
   Removes a package.

   ```
   apt-get purge <package-name>
   ```
   Completely removes a package along with configuration files.

   ```
   apt-get autoremove
   ```
   Removes unnecessary dependencies.

9. Download and Manage Source Packages

   ```
   apt-get download <package-name>
   ```
   Downloads a package without installing it.

   ```
   apt-get source <package-name>
   ```
   Fetches the source code of a package.

   ```
   apt-get changelog <package-name>
   ```
   Checks the package changelog.

   ```
   apt-get check
   ```
   Verifies package integrity.

   ```
   apt-get clean
   ```
   Cleans cached packages.

10. Additional Package Management Tools

   ```
   pip install <package-name>
   ```
   Installs Python packages via pip.

   ```
   npm install <package-name>
   ```
   Installs Node.js packages.

   ```
   gem install <package-name>
   ```
   Installs Ruby gems.
