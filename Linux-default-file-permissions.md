In Linux, the **default permissions** assigned to newly created files and directories are as follows:

### Default Permissions for Files:

- **`666` (rw-rw-rw-)**
This means:

However, files typically **do not** have execute permissions by default. The absence of the execute permission prevents files from being run as executables by default.
- The **owner** has **read** and **write** permissions (`rw-`).
- The **group** has **read** and **write** permissions (`rw-`).
- **Others** have **read** and **write** permissions (`rw-`).

### Default Permissions for Directories:

- **`777` (rwxrwxrwx)**
This means:

The execute permission (`x`) for directories is necessary for users to access and list files within them.
- The **owner** has **read**, **write**, and **execute** permissions (`rwx`).
- The **group** has **read**, **write**, and **execute** permissions (`rwx`).
- **Others** have **read**, **write**, and **execute** permissions (`rwx`).

# Each character in these parts can be one of:

- **`r`** (read) – Allows reading the contents of the file or listing the contents of the directory.

- **`w`** (write) – Allows modifying the file or adding/removing files in the directory.
- **`x`** (execute) – Allows executing the file (if it’s a program or script) or entering the directory.

If a permission is **not granted**, it is represented by a **dash (`-`)** instead of the corresponding letter.

### Example:

```
-rwxrwxrwx

```

- The first **``** indicates it's a regular **file**. (If it were a **directory**, this would be a `d`.)
- **`rwx`** (for the owner): The owner has **read**, **write**, and **execute** permissions.
- **`rwx`** (for the group): The group has **read**, **write**, and **execute** permissions.
- **`rwx`** (for others): Everyone else has **read**, **write**, and **execute** permissions.

### Permission Breakdown:

### Owner (`rwx`):

- **`r` (read)**: The owner can view the file's contents (for files) or list the contents of the directory (for directories).
- **`w` (write)**: The owner can modify the file's contents (for files) or add/remove files in the directory (for directories).
- **`x` (execute)**: The owner can run the file as a program or script (for files) or change into the directory (for directories).

### Group (`rwx`):

- **`r` (read)**: The group members can view the file's contents (for files) or list the contents of the directory (for directories).
- **`w` (write)**: The group members can modify the file (for files) or add/remove files in the directory (for directories).
- **`x` (execute)**: The group members can run the file (for files) or access the directory (for directories).

### Others (`rwx`):

- **`r` (read)**: Others can view the file's contents (for files) or list the contents of the directory (for directories).
- **`w` (write)**: Others can modify the file (for files) or add/remove files in the directory (for directories).
- **`x` (execute)**: Others can run the file (for files) or enter the directory (for directories).

### Example with dashes:

```
rw-r--r--

```

- The **owner** has **read** and **write** permissions (`rw-`), but not execute permission.
- The **group** has **read** permission (`r--`), but not write or execute.
- **Others** have **read** permission (`r--`), but not write or execute.

### Numeric Representation:

Each permission can also be represented by a number. Here's how it works:

- **`r` = 4**
- **`w` = 2**
- **`x` = 1**
- **`` (no permission) = 0**

These numbers are summed up for each section (owner, group, and others), and the result gives a **numeric permission value**.

For example:

- **`rwx`** (read, write, execute) = 4 + 2 + 1 = **7**
- **`rw-`** (read, write) = 4 + 2 + 0 = **6**
- **`r--`** (read only) = 4 + 0 + 0 = **4**

So, for the permissions `rwxr-xr--`, the numeric representation would be:

- Owner: `rwx` → 7
- Group: `r-x` → 5
- Others: `r--` → 4

Thus, the numeric permission value is **`754`**.

### Common Permissions Examples:

- **`rwxr-xr-x` (755)**: Full permissions for the owner, and read/execute permissions for group and others. Common for executable files and directories.
- **`rw-r--r--` (644)**: The owner can read and write the file, while the group and others can only read. Common for regular files.
- **`rwxrwxrwx` (777)**: Full permissions for everyone. This is **not recommended** for most files because it allows anyone to read, write, and execute the file or directory, which can pose a security risk.

### Summary of the Permissions:

- **r (read)**: Grants the ability to view the contents.
- **w (write)**: Grants the ability to modify the contents.
- **x (execute)**: Grants the ability to execute the file or access the directory.

This system of file permissions allows you to manage who can interact with your files and directories and in what way.
