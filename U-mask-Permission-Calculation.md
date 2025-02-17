# U-Mask in Unix-like Operating Systems

**U-Mask** is a command used in Unix-like operating systems (such as Linux and macOS) to control the default permissions given to newly created files and directories. When a new file or directory is created, the system applies a default set of permissions. The `umask` determines how these default permissions should be modified.

---

## Default Permissions

By default, files and directories come with certain permissions when they are created. These default permissions are as follows:

1. **Default File Permissions:** `666` (rw-rw-rw-)
2. **Default Directory Permissions:** `777` (rwxrwxrwx)

Here’s a breakdown of what each permission represents:
- `r = read` – allows reading the contents of the file or directory.
- `w = write` – allows modifying the file or directory.
- `x = execute` – allows running the file (if it’s executable) or accessing the directory.

### Default Permissions Table:
| Permission | File (Default) | Directory (Default) |
|------------|----------------|---------------------|
| Owner      | rw-            | rwx                 |
| Group      | rw-            | rwx                 |
| Others     | rw-            | rwx                 |

---

## How Does Umask Work?

The `umask` works by subtracting certain permissions from the default permissions. It acts as a "mask" that removes specific permissions from the default set, resulting in more restrictive permissions.

### Process:
1. **Default permissions** are set for a file or directory:
   - Default file permission: `666` (rw-rw-rw-)
   - Default directory permission: `777` (rwxrwxrwx)
   
2. The `umask` value is applied by **subtracting it** from the default permissions to determine the final permission for the file or directory.

---

## Permission Calculation

### File Permission Calculation:

Let’s calculate the file permission with a **default file permission** of `666` (rw-rw-rw-) and a `umask` value of `022`.

Step-by-Step Calculation:

Default file permission: 666 (rw-rw-rw-)

Umask value: 022


The formula for permission calculation is:
```bash
Final Permission = Default Permission - Umask

### File Permission Calculation Example:

- **Default permissions for files**: `666` (`rw-rw-rw-`)
- **Umask**: `022`
  
#### Calculation:
- `666 - 022 = 644`

#### Resulting permissions:
- `rw-r--r--` (for files)


### Directory Permission Calculation Example:

- **Default permissions for directories**: `777` (`rwxrwxrwx`)
- **Umask**: `022`
  
#### Calculation:
- `777 - 022 = 755`

#### Resulting permissions:
- `rwxr-xr-x` (for directories)










