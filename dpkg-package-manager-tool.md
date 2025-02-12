# dpkg package manager tool
---
The `dpkg` command is a package management tool for Debian-based systems (including Ubuntu). It is used to install, remove, and manage `.deb` packages. Below are the main switches (options) you can use with the `dpkg` command:

### Basic Syntax
```
dpkg [options] <package_file>.deb
```

### Common `dpkg` Command Options:

1. **Install a Package**
   ```
   dpkg -i <package_file>.deb
   ```
   - **Description**: Installs the specified `.deb` package.
   - **Example**:
     ```
     dpkg -i mypackage.deb
     ```

2. **Remove a Package**
   ```
   dpkg -r <package_name>
   ```
   - **Description**: Removes the specified package, but keeps its configuration files.
   - **Example**:
     ```
     dpkg -r mypackage
     ```

3. **Purge a Package**
   ```
   dpkg -P <package_name>
   ```
   - **Description**: Removes the package along with its configuration files.
   - **Example**:
     ```
     dpkg -P mypackage
     ```

4. **List Installed Packages**
   ```
   dpkg -l
   ```
   - **Description**: Lists all installed packages on the system.
   - **Example**:
     ```
     dpkg -l
     ```

5. **List Specific Package**
   ```
   dpkg -l | grep <package_name>
   ```
   - **Description**: Lists a specific package if it is installed.
   - **Example**:
     ```
     dpkg -l | grep apache2
     ```

6. **Show Package Information**
   ```
   dpkg -s <package_name>
   ```
   - **Description**: Displays detailed information about a specific package.
   - **Example**:
     ```
     dpkg -s apache2
     ```

7. **List Package Files**
   ```
   dpkg -L <package_name>
   ```
   - **Description**: Lists all files installed by the given package.
   - **Example**:
     ```
     dpkg -L apache2
     ```

8. **Verify Package Installation**
   ```
   dpkg -V <package_name>
   ```
   - **Description**: Verifies the integrity of installed package files.
   - **Example**:
     ```
     dpkg -V apache2
     ```

9. **Configure Unpacked Packages**
   ```
   dpkg --configure <package_name>
   ```
   - **Description**: Configures a package that has been unpacked but not configured. Often used after an incomplete installation.
   - **Example**:
     ```
     dpkg --configure apache2
     ```

10. **List Available Packages**
    ```
    dpkg -p <package_name>
    ```
    - **Description**: Shows detailed information about an available package from the system's package database (not installed).
    - **Example**:
      ```
      dpkg -p apache2
      ```

11. **Check for Dependencies**
    ```
    dpkg -I <package_file>.deb
    ```
    - **Description**: Displays information about the package, including its dependencies.
    - **Example**:
      ```
      dpkg -I mypackage.deb
      ```

12. **List Files in a `.deb` Package**
    ```
    dpkg -c <package_file>.deb
    ```
    - **Description**: Lists the contents of a `.deb` package without installing it.
    - **Example**:
      ```
      dpkg -c mypackage.deb
      ```

13. **Remove a Package But Keep the Configuration Files**
    ```
    dpkg --remove <package_name>
    ```
    - **Description**: Removes the package but retains configuration files.
    - **Example**:
      ```
      dpkg --remove mypackage
      ```

14. **Force Remove a Package**
    ```
    dpkg --force-remove-reinstreq <package_name>
    ```
    - **Description**: Forces removal of a package that is in a "reinstreq" state (i.e., needs to be reinstalled).
    - **Example**:
      ```
      dpkg --force-remove-reinstreq mypackage
      ```

15. **Install Dependencies for a Package**
    ```
    dpkg --install --force-depends <package_file>.deb
    ```
    - **Description**: Installs a package even if it has unmet dependencies.
    - **Example**:
      ```
      dpkg --install --force-depends mypackage.deb
      ```

### Example Usage:

1. **Install a package:**
   ```
   dpkg -i package_name.deb
   ```

2. **Remove a package:**
   ```
   dpkg -r package_name
   ```

3. **Check installed packages:**
   ```
   dpkg -l
   ```

4. **Purge a package:**
   ```
   dpkg -P package_name
   ```

5. **Display information about a package:**
   ```
   dpkg -s package_name
   ```

---

These are the core options you’ll typically use with `dpkg`. For more options, you can always check the man page by running:

```
man dpkg
```
---   
by [Tanush Kushwah](https://www.linkedin.com/in/tanush-kushwah-b51a97319/?originalSubdomain=in)
