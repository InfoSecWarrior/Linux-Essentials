
## 🛠️ **1. Display Help for `useradd` Command**
### 📌 **Command:**
```bash
useradd -h
```
### 📌 **Example Output:**
```bash
Usage: useradd [options] LOGIN
Options:
  -b, --base-dir BASE_DIR       🏠 Set base home directory
  -c, --comment COMMENT         📝 Add user comment
  -d, --home-dir HOME_DIR       📂 Specify home directory path
  -e, --expiredate EXPIRE_DATE  ⏳ Set account expiration date
  -g, --gid GROUP               👥 Set primary group ID
  -G, --groups GROUPS           🔄 Add secondary groups
  -m, --create-home             🏡 Create a home directory
  -M, --no-create-home          🚫 Do not create a home directory
  -s, --shell SHELL             🖥️ Set login shell
  -u, --uid UID                 🔢 Set user ID
  -p, --password PASSWORD       🔑 Set an encrypted password
  -r, --system                  ⚙️ Create a system user
```
✅ **This helps understand all `useradd` options.**

---

## 🏠 **2. Create a New User with Home Directory**
### 📌 **Command:**
```bash
useradd -m -d /home/john john
```
✅ **Creates user `john` with a home directory `/home/john`.**

### 📌 **Verify:**
```bash
tail -n 1 /etc/passwd
```
#### **Expected Output:**
```bash
john:x:1001:1001::/home/john:/bin/bash
```

---

## 🔑 **3. Set Password for a User**
### 📌 **Command:**
```bash
passwd john
```
✅ **Sets a password for user `john`.**

### 📌 **For an Encrypted Password:**
```bash
useradd -p $(openssl passwd -1 "MySecurePassword") user1
```
✅ **Uses `openssl` to set an encrypted password.**

---

## 🎯 **4. Create a User with a Specific UID**
### 📌 **Command:**
```bash
useradd -u 1050 user2
```
✅ **Creates `user2` with UID `1050`.**

### 📌 **Verify:**
```bash
id user2
```
#### **Expected Output:**
```bash
uid=1050(user2) gid=1050(user2) groups=1050(user2)
```

---

## 👥 **5. Assign a User to a Specific Group**
### 📌 **Command:**
```bash
useradd -g developers user3
```
✅ **Creates `user3` and assigns it to the `developers` group.**

### 📌 **Check Group:**
```bash
id user3
```

---

## 🔄 **6. Add a User to Multiple Groups**
### 📌 **Command:**
```bash
useradd -G sudo,developers user4
```
✅ **Adds `user4` to `sudo` and `developers` groups.**

### 📌 **Verify:**
```bash
groups user4
```
#### **Expected Output:**
```bash
user4 : user4 sudo developers
```

---

## ⏳ **7. Set Account Expiration Date**
### 📌 **Command:**
```bash
useradd -e 2025-12-31 user5
```
✅ **User `user5` will expire on `31 Dec 2025`.**

### 📌 **Verify:**
```bash
chage -l user5
```
#### **Expected Output:**
```bash
Account expires: Dec 31, 2025
```

---

## 🚫 **8. Create a User Without a Home Directory**
### 📌 **Command:**
```bash
useradd --no-create-home user6
```
✅ **Creates `user6` without a home directory.**

### 📌 **Verify:**
```bash
ls -ld /home/user6
```
#### **Expected Output:** (No directory found)
```bash
ls: cannot access '/home/user6': No such file or directory
```

---

## 🖥️ **9. Set Default Shell for a User**
### 📌 **Command:**
```bash
useradd -s /bin/zsh user7
```
✅ **Sets `/bin/zsh` as the default shell for `user7`.**

### 📌 **Verify:**
```bash
cat /etc/passwd | grep user7
```
#### **Expected Output:**
```bash
user7:x:1007:1007::/home/user7:/bin/zsh
```

---

## ⚙️ **10. Create a System User**
### 📌 **Command:**
```bash
useradd -r systemuser
```
✅ **Creates a system user `systemuser`.**

### 📌 **Verify:**
```bash
id systemuser
```
#### **Expected Output:**
```bash
uid=497(systemuser) gid=497(systemuser) groups=497(systemuser)
```

---

## 🏷️ **11. Create a User with Custom Comments**
### 📌 **Command:**
```bash
useradd -c "Project Manager" user8
```
✅ **Adds `Project Manager` as a comment for `user8`.**

### 📌 **Verify:**
```bash
cat /etc/passwd | grep user8
```
#### **Expected Output:**
```bash
user8:x:1008:1008:Project Manager:/home/user8:/bin/bash
```

---

## 🏁 **12. Delete a User**
### 📌 **Command:**
```bash
userdel user9
```
✅ **Deletes `user9` but keeps their home directory.**

### 📌 **Delete User and Home Directory**
```bash
userdel -r user10
```
✅ **Deletes `user10` and removes `/home/user10`.**

---

# 🔥 **Summary Table**
| 🎯 **Command** | 📌 **Description** |
|---------------|----------------|
| `useradd -m john` | Creates a user `john` with a home directory |
| `passwd john` | Sets a password for `john` |
| `useradd -u 1050 user2` | Creates `user2` with UID `1050` |
| `useradd -g developers user3` | Assigns `user3` to `developers` group |
| `useradd -G sudo,developers user4` | Adds `user4` to multiple groups |
| `useradd -e 2025-12-31 user5` | Sets an expiration date for `user5` |
| `useradd --no-create-home user6` | Creates `user6` without a home directory |
| `useradd -s /bin/zsh user7` | Sets `/bin/zsh` as the shell for `user7` |
| `useradd -r systemuser` | Creates a system user |
| `useradd -c "Project Manager" user8` | Adds a comment for `user8` |
| `userdel user9` | Deletes `user9` but keeps home directory |
| `userdel -r user10` | Deletes `user10` and removes home directory |

---

