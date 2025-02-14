# Understanding Set GID (SGID) and Sticky Bit in Linux 

## Set GID (Set Group ID) Bit 

The Set GID (SGID) bit is a special permission in Linux that ensures files and directories inherit the group ownership of their parent directory rather than the user creating them.

### Behavior:

 1. On files : If a file has the SGID bit set, it will run with the group privileges of the file owner instead of the user executing it.

 2. On directories : Any new files or subdirectories created inside an SGID-enabled directory will inherit the group's ownership from the parent directory, not the user's primary group.

### Usage:

 1. Set SGID on a directory:

        chmod g+s directory_name

 2. Set SGID on a file:

        chmod 2755 script.sh
   

 3. Check if SGID is set:
   
        ls -lh directory_name

  * Example output:

         drwxr-sr-x  2 user group 4096 Feb 12 12:34 directory_name

    The s in drwxr-sr-x indicates that the SGID bit is set.

##  Sticky Bit 

The Sticky Bit is a permission typically set on directories to restrict file deletion. Only the file owner (or root) can delete their own files inside a sticky-bit-enabled directory.

### Usage:

1. Set Sticky Bit on a directory:

        chmod +t /tmp
    

2. Check if the Sticky Bit is set:

        ls -lh /tmp

 * Example output:

         drwxrwxrwt  2 root root 4096 Feb 12 12:34 /tmp

   The t in drwxrwxrwt indicates that the Sticky Bit is set.

### Summary Table


| Feature      | SGID (Set Group ID) | Sticky Bit |
|-------------|---------------------|------------|
| **Usage On** | Files & Directories | Directories Only |
| **Effect on Files** | Runs with group’s permissions | No effect |
| **Effect on Directories** | New files inherit the group of the directory | Only the owner (or root) can delete files inside the directory |
| **Command to Set** | `chmod g+s filename/directory` | `chmod +t directory_name` |
| **Command to Check** | `ls -lh` (shows `rws` in group section) | `ls -lh` (shows `t` at the end) |
| **Example Usage** | Shared project directories | `/tmp` folder in Linux |

### Real-World Use Cases

   *  SGID on Directories: Useful for shared project folders where all users should inherit the same group (e.g., /var/www/html for web development).

   *  Sticky Bit on /tmp: Ensures multiple users can store temporary files but cannot delete others' files.


