# `Sudo`

## What is Sudo?
- `sudo` (Super User DO) allows a permitted user to run commands as a superuser (root) or another user.
- Unlike `su`, which switches users, `sudo` runs commands with elevated privileges without changing users.

---

## Installing and Checking `Sudo`

### Check if `sudo` is installed

```sh
rpm -qa | grep sudo  
```

### Install `sudo` (if not installed)
```sh
yum install sudo  
```

### List installed files
```sh
rpm -ql sudo  
```

### View `sudo` configuration files
```sh
rpm -qc sudo  
```

### View `sudo` documentation
```sh
rpm -qd sudo  
```

---

## Sudo Configuration File
- The main configuration file is: `/etc/sudoers`
- Always edit using: `visudo`

---

## Managing Sudo Permissions

### View sudoers file without comments
```sh
grep -v "^#" /etc/sudoers | sed '/^$/d'
```

- **Default sudo rule:**
  ```sh
  root ALL=(ALL) ALL
  ```
- **Format for adding users:**
  ```sh
  USERNAME HOSTNAME=(USER:GROUP) COMMANDS
  ```
  - `USERNAME` → User receiving sudo privileges
  - `HOSTNAME` → System where the user can execute commands
  - `GROUP` → The group under which the user can run commands
  - `COMMANDS` → Specific commands allowed

### Example Entries in `/etc/sudoers`

#### Give full sudo access to 'neha'
```sh
neha ALL=(ALL) ALL  
```

---

## Checking Sudo Permissions
```sh
sudo -l   # Check sudo access  
sudo id   # Show user ID with sudo  
sudo -u neha id   # Run command as another user  
sudo -u neha -g IT id   # Run command as a specific user and group  
```

---

## Granting Sudo Access to a User

### Open the sudoers file
```sh
visudo
```
### Add the following line
neha ALL=(ALL) ALL
```
Now, `neha` can use sudo:
```sh
sudo -l
sudo id
```

---

## Using the Wheel Group
- The `wheel` group is predefined in sudoers.
- Any member of this group can run all commands as any user.

### Adding a User to the Wheel Group

#### Add user to wheel group
```sh
gpasswd -a neha wheel  
```
#### Verify group membership
```sh
cat /etc/group | grep wheel  
```

After adding `neha` to the `wheel` group:
```sh
sudo -l  

# Output: User neha may run the following commands on localhost: (ALL) ALL  
```
```sh
sudo id 

# Output: uid=0(root) gid=0(root) groups=0(root)  
