# Sudo Aliases & Configuration

## 1. Creating Sudo Access for a User
To allow a user to run all sudo commands:

```sh
user1 localhost=(ALL) ALL
```

Edit using:

```sh
# visudo 
# EDITOR=vim visudo
```

If there's an error while editing, press 'e' to fix it.

---

## 2. Hostname Aliases
To define multiple hosts under an alias:

```sh
Host_Alias IT_HOSTS = localhost, ns2, webserver
```

Grant sudo access:

```sh
neha IT_HOSTS = (ALL) ALL
```

Check assigned sudo privileges:

```sh
sudo -l
```

---

## 3. Username Aliases
To group multiple users under an alias:

```sh
User_Alias IT_USERS = it1, it2, it3
IT_USERS ALL = (ALL) ALL
```

Check users:

```sh
# cat /etc/passwd | grep it
```


```
```
### Restricting sudo to specific users

```sh
User_Alias IT_USERS = it1, it2, it3
IT_USERS ALL = (neha, it1) ALL
```

- `it1` can use sudo: ✅
- `neha` is not defined in alias: ❌
- Check sudo access:

```sh
[it1@localhost ~]$ sudo -l
[neha@localhost ~]$ sudo -l   # Will show an error
```

### Giving sudo with specific group permissions

```sh
User_Alias IT_USERS = it1, it2, it3
IT_USERS ALL = ("it1" : "IT") ALL
```

Check access for `it2`:

```sh
[it2@localhost ~]$ sudo -l
```

Run sudo as a user with a group:

```sh
[it2@localhost ~]$ sudo -u it1 -g IT id
```

---

## 4. Command Aliases

### To allow a group of commands in sudo:

```sh
Cmnd_Alias NEHA_CMD = /usr/sbin/fdisk, /usr/bin/yum, /usr/sbin/useradd
Cmnd_Alias MAVKAR_CMD = /usr/bin/id, /usr/bin/whoami, /usr/bin/mkdir
Cmnd_Alias IT_CMD = /usr/sbin/ifconfig, /usr/bin/ping, /usr/sbin/ip, /usr/bin/rpm
```

### Assigning commands to users:

```sh
User_Alias IT_USERS = it1, it2, it3
User_Alias HR_USERS = hr1, hr2, hr3

neha ALL = (ALL) /usr/bin/id
IT_USERS ALL = (root, neha, "hr1" : "HR") SOFTWARE, NEHA_CMD, MAVKAR_CMD
HR_USERS ALL = (root, neha, "it1" : "IT") SOFTWARE, IT_CMD
```

---

## 5. NOPASSWD Configuration
Allow sudo without a password for some commands:

```sh
IT_USERS ALL = (root) NOPASSWD: SOFTWARE
HR_USERS ALL = (ALL) NOPASSWD: SOFTWARE, NEHA_CMD PASSWD: IT_CMD
```

### Example:

```sh
[it1@localhost ~]$ sudo yum repolist
[it1@localhost ~]$ sudo cat /etc/passwd  # Requires password
```

If a command is not in the `NOPASSWD` list, the user will need to enter a password.

---

## Summary
- **Host_Alias**: Groups multiple hosts.
- **User_Alias**: Groups multiple users.
- **Cmnd_Alias**: Groups multiple commands.
- **NOPASSWD**: Allows some commands without a password.
