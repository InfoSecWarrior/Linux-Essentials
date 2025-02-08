# **Understanding `su` and `sg` Commands in Linux**  

## **1. `su` (Substitute User) Command**  

### **Purpose:**  
The `su` command allows you to switch to another user account in a Linux system. If no username is specified, it defaults to the root user. This is commonly used for administrative tasks or switching to users with specific privileges.  

### **Basic Syntax:**  
The basic syntax for using the `su` command is:

```bash
su [options] [username]

```
- If executed by a non-root user, `su` prompts for the target user's password before switching.
- If executed by root, `su` switches users without a password prompt.

### **Common Options:**

| **Option** | **Description** |
|------------|-----------------|
| `-` or `-l` or `--login` | Starts a full login shell, resetting the environment as if the user had logged in normally. |
| `-c [command]` | Executes a single command as the target user and then returns to the original shell. |
| `-s [shell]` | Specifies a shell to use when switching users. |
| `-m` or `-p` | Preserves the current environment variables when switching users. |

### **Examples of `su` Usage:**

1. **Switch to the root user with a login shell:**
   ```bash
   su -
   ```
   This prompts for the root password and starts a new shell with root’s environment settings. Equivalent to logging in as root directly.

2. **Switch to another user (e.g., `alex`) with a full login shell:**
   ```bash
   su - alex
   ```
   The `-` flag ensures that `alex`’s environment variables, shell, and profile settings are loaded.

3. **Execute a command as another user without switching permanently:**
   ```bash
   su -c 'whoami' admin
   ```
   Runs the `whoami` command as the `admin` user and then returns to the original shell.

4. **Run a command as a specific user with a different shell:**
   ```bash
   su -s /bin/zsh devuser
   ```
   Switches to `devuser` and starts a Zsh shell instead of the default shell.

5. **Preserve the current environment when switching users:**
   ```bash
   su -m alex
   ```
   Unlike `su - alex`, this keeps the current environment variables intact.

### **Security Considerations for `su`:**
- **Restricted Usage:** On some Linux distributions, direct root login via `su` may be disabled for security reasons (e.g., Ubuntu uses `sudo` instead).
- **Logging:** Switching users with `su` is logged in `/var/log/auth.log` or `/var/log/secure`.
- **Privilege Escalation Risks:** If compromised, an attacker could gain full access to another user’s account, making strict password policies essential.

---

## **2. `sg` (Switch Group) Command**  

### **Purpose:**  
The `sg` command allows a user to execute commands with the permissions of a specific group. This is useful when a user belongs to multiple groups and needs to run a command under a specific group identity.  

Unlike `su`, `sg` does not require a password. It assumes that the user is already a member of the specified group.  

### **Basic Syntax:**  
```bash
sg [group] -c "command"
```
- `[group]` specifies the target group.
- `-c "command"` runs a single command under the specified group.

### **Common Use Cases:**

| **Use Case** | **Example** |
|--------------|-------------|
| Run a command as a specific group | `sg developers -c 'id'` |
| List directory contents with a different group’s permissions | `sg staff -c 'ls /staff_data'` |
| Execute a script under a specific group | `sg security -c './audit.sh'` |
| Open a new shell as a specific group | `sg admins -` |

### **Examples of `sg` Usage:**

1. **Run a command under the `developers` group identity:**
   ```bash
   sg developers -c 'groups'
   ```
   Displays the groups associated with the current user while executing under the `developers` group identity.

2. **List files in `/staff_data` using `staff` group permissions:**
   ```bash
   sg staff -c 'ls /staff_data'
   ```
   Ensures the correct group permissions are used to access `/staff_data`.

3. **Execute a script under the `security` group:**
   ```bash
   sg security -c './audit.sh'
   ```
   Runs `audit.sh` with the security group’s permissions.

4. **Open a new shell as the `admins` group:**
   ```bash
   sg admins -
   ```
   Starts a new shell where commands execute under the `admins` group.

### **Security Considerations for `sg`:**
- **Group Membership Required:** The user must already be a member of the target group.
- **Less Risky than `su`:** Since `sg` does not switch users, it limits privilege escalation risks.
- **Use with `sudo` for Elevated Privileges:** If elevated privileges are needed, combining `sg` with `sudo` may be required.

---
