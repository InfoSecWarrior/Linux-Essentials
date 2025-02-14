## User Modify (`usermod`)
The `usermod` command in Linux is used to modify existing user accounts. It allows system administrators to change user attributes such as username, home directory, groups, shell, and more.

---

## Basic Syntax

sudo usermod [options] username

- Requires `sudo` or root privileges.
- Replace `[options]` with the appropriate flags to modify user attributes.

---

## Useful `usermod` Switches

### 1. Change Username (`-l`)
**What it does**: Renames an existing user account.  
**Syntax**:  
```bash
usermod -l new_username old_username

**Example**:  
```bash
usermod -l user1_new user1_old
```

- Changes the username from `user1_old` to `user1_new`.

---

### 2. Change Home Directory (`-d`)
**What it does**: Changes the user's home directory.  
**Syntax**:  
```bash
usermod -d /new/home/dir -m username
```
**Example**:  
```bash
usermod -d /home/user1_new -m user1
```
- `-d`: Specifies the new home directory.
- `-m`: Moves the contents of the old home directory to the new one.

---

### 3. Change User's Shell (`-s`)
**What it does**: Changes the user's login shell.  
**Syntax**:  
```bash
usermod -s /path/to/shell username
```
**Example**:  
```bash
usermod -s /usr/bin/zsh user1
```
- Sets the user's login shell to `/usr/bin/zsh`.

---

### 4. Add User to Supplementary Groups (`-aG`)
**What it does**: Adds the user to additional groups without removing existing group memberships.  
**Syntax**:  
```bash
usermod -aG group1,group2 username
```
**Example**:  
```bash
usermod -aG sudo,developers user1
```
- `-a`: Append to existing groups (prevents overwriting).
- `-G`: Specifies the groups to add the user to.

---

### 5. Lock/Unlock User Account (`-L`, `-U`)
**What it does**: Locks or unlocks a user account.  
**Syntax**:  
- **Lock**:  
  ```bash
  usermod -L username
  ```
- **Unlock**:  
  ```bash
  usermod -U username
  ```

---

### 6. Change User ID (`-u`)
**What it does**: Changes the user's UID (User ID).  
**Syntax**:  
```bash
usermod -u new_uid username
```
**Example**:  
```bash
usermod -u 1100 user1
```
- Updates the user's UID to `1100`.

---

### 7. Change Group ID (`-g`)
**What it does**: Changes the user's primary group.  
**Syntax**:  
```bash
usermod -g new_gid username
```
**Example**:  
```bash
usermod -g 1050 user1
```
- Updates the user's primary group to `1050`.

---

### 8. Set Account Expiry Date (`-e`)
**What it does**: Sets an expiry date for the user account.  
**Syntax**:  
```bash
usermod -e YYYY-MM-DD username
```
**Example**:  
```bash
usermod -e 2025-12-31 user1
```
- The account will expire on December 31, 2025.

---

### 9. Change User's Full Name (`-c`)
**What it does**: Updates the user's comment field (often used for the full name).  
**Syntax**:  
```bash
usermod -c "Full Name" username
```
**Example**:  
```bash
usermod -c "John Doe" user1
```
- Updates the user's comment field to "John Doe".

---

### 10. Move User's Home Directory (`-m`)
**What it does**: Moves the contents of the user's home directory to a new location.  
**Syntax**:  
```bash
usermod -d /new/home/dir -m username
```
**Example**:  
```bash
usermod -d /home/user1_new -m user1
```
- Moves the contents of `/home/user1` to `/home/user1_new`.

---

### 11. Force Password Change (`-f`)
**What it does**: Sets the number of days after which the password must be changed.  
**Syntax**:  
```bash
usermod -f days username
```
**Example**:  
```bash
usermod -f 8 user1
```
- The user must change their password after 8 days.

---

### 12. Allow Non-Unique UID (`-o`)
**What it does**: Allows duplicate UIDs (not recommended for security reasons).  
**Syntax**:  
```bash
usermod -o -u 0 username
```
**Example**:  
```bash
usermod -o -u 0 user1
```
- Sets the UID to `0` (root), even if another user has the same UID.

---

### 13. Set Encrypted Password (`-p`)
**What it does**: Sets an encrypted password for the user.  
**Syntax**:  
```bash
usermod -p 'encrypted_password' username
```
**Example**:  

**Generate Encrypted Password** :
```bash
openssl passwd 123
$1$dr5MGUev$uZ8QHz4ilePmWugMkj7yA.
```

**Sets the encrypted password** :
```bash

usermod -p '$1$dr5MGUev$uZ8QHz4ilePmWugMkj7yA.' user1
```


---

## User Deletion (`userdel`)
The `userdel` command in Linux is used to **delete user accounts** from the system. It removes the user's entry from the `/etc/passwd`, `/etc/shadow`, and `/etc/group` files, effectively removing the user from the system.

**Syntax**:  
```bash
userdel [options] username
```
**Examples**:  
- Delete a user:  
  ```bash
  userdel user1
  ```
- Delete a user and their home directory:  
  ```bash
  userdel -r user1
  ```
- Forcefully delete a user and their home directory:  
  ```bash
  userdel -f -r user1
  ```

---

## Password Management (`passwd`)
The `passwd` command in Linux is used to **manage user passwords**. It allows users to change their own passwords and enables administrators to manage passwords for other users. The command also provides options to lock, unlock, and check the status of passwords.

**Syntax**:  
```bash
passwd [options] username
```
**Examples**:  
- Change a user's password:  
  ```bash
  passwd user1
  ```
- Delete a user's password:  
  ```bash
  passwd -d user1
  ```
- Lock a user's password:  
  ```bash
  passwd -l user1
  ```
- Unlock a user's password:  
  ```bash
  passwd -u user1
  ```
- Check password status:  
  ```bash
  passwd -S user1
  ```
- Forces `user1` to change their password on their next login.:  
  ```bash
  passwd -e user1
  ```
- Forces `user1` to change their password on their next login.:  
  ```bash
  passwd -e user1
  ```

---

## Summary Table
| Command          | Description                              | Example                                  |
|------------------|------------------------------------------|------------------------------------------|
| `usermod -l`     | Change username                          | `usermod -l user1_new user1_old`         |
| `usermod -d`     | Change home directory                    | `usermod -d /home/user1_new -m user1`    |
| `usermod -s`     | Change login shell                       | `usermod -s /usr/bin/zsh user1`          |
| `usermod -aG`    | Add user to groups                       | `usermod -aG sudo,dev user1`             |
| `usermod -L/U`   | Lock/unlock account                      | `usermod -L user1`                       |
| `usermod -u`     | Change UID                               | `usermod -u 1100 user1`                  |
| `usermod -g`     | Change primary GID                       | `usermod -g 1050 user1`                  |
| `usermod -e`     | Set account expiry date                  | `usermod -e 2025-12-31 user1`            |
| `usermod -c`     | Update comment (e.g., full name)         | `usermod -c "John Doe" user1`            |
| `usermod -m`     | Move home directory contents             | `usermod -d /home/user1_new -m user1`    |
| `usermod -f`     | Force password change                    | `usermod -f 8 user1`                     |
| `usermod -o`     | Allow non-unique UID                     | `usermod -o -u 0 user1`                  |
| `usermod -p`     | Set encrypted password                   | `usermod -p $(openssl passwd -1 '123')`  |
| `userdel`        | Delete user                              | `userdel -r user1`                       |
| `passwd`         | Manage passwords                         | `passwd -S user1`                        |

