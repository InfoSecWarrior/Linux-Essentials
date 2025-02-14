# Switching Users and Groups in Linux

## 1. `su` Command (Switch User)

The `su` (substitute user) command allows a user to **switch to another user account** or execute commands as another user, commonly `root`.

### **Key Features**:

- Requires authentication using the **password of the target user**.
- Enables complete user switching or the execution of commands under a different user.
- `su` : Switches user without changing the environment variables.
- `su -` : Starts a new shell session with the full login environment of the target user.

### **Syntax**:

```bash
su [OPTIONS] [USERNAME]
```

### **Commonly Used Options**:

- `-` : Loads the target user’s environment variables.
- `-c "command"` : Executes a single command as the target user.
- `-s /bin/bash` : Changes the shell when switching users.

### **Examples**:

1. **Switch to the ****`root`**** user:**

   ```bash
   su
   ```

   This prompts for the `root` user password.

2. **Switch to a specific user (e.g., ****`john`****):**

   ```bash
   su john
   ```

   This switches to `john`’s account and requires authentication.

3. **Run a command as another user:**

   ```bash
   su -c "whoami" username
   ```

   Example:

   ```bash
   su -c "ls /root" root
   ```

   Runs `ls /root` as `root` while staying in the current shell.

4. **Start a full login session for a user:**

   ```bash
   su - username
   ```

   This loads the user’s full environment as if they had logged in directly.

---

## 2. `sg` Command (Switch Group)

The `sg` (substitute group) command allows users to **execute commands as a member of a specified group**. This is useful when working with group-based permissions without changing user ownership.

### **Key Features**:

- Runs commands under a **specific group context**.
- Does not require password authentication.
- The user must already be a member of the target group.
- Limited to command execution and does not open a full session.

### **Syntax**:

```bash
sg groupname -c "command"
```

### **Examples**:

1. **Run a command as a member of a group:**

   ```bash
   sg developers -c "touch file.txt"
   ```

   This creates a file under the `developers` group context.

2. **Start a new shell as a member of a group:**

   ```bash
   sg groupname
   ```

   This opens a shell where commands execute under the specified group.

3. **Check your current group membership:**

   ```bash
   groups
   ```

   This displays all groups you belong to.

---

## 4. Comparison: `su` vs. `sg`

| Feature            | `su` (Switch User)                            | `sg` (Switch Group)                                           |
| ------------------ | --------------------------------------------- | ------------------------------------------------------------- |
| **Purpose**        | Switch to another **user account**.           | Temporarily switch to another **group**.                      |
| **Authentication** | Requires the **target user’s password**.      | Requires membership in the target group (no password needed). |
| **Scope**          | Switch user entirely or run commands as them. | Execute commands as a specific group member.                  |
| **Use Case**       | For administrative tasks or user switching.   | For group-based permissions and tasks.                        |

---

## 5. When to Use `sg`

- When you need to work on files or execute commands with **specific group-based permissions**.
- **Example Scenario:**
  - You are part of the `developers` and `admins` groups.
  - A file is owned by the `admins` group.
  - Instead of switching users, you can use `sg admins` to work on the file **without changing ownership**.


