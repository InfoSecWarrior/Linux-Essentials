
# 🐧 **Linux `usermod` Command – Modify User Accounts** 🔧  

The `usermod` command in Linux is used to modify existing user accounts. Below is a detailed overview of its options, examples, and expected outputs.  

## 📌 **Basic Syntax**  
```bash
usermod [options] username
```

## ⚙️ **Common Options and Examples**  

### 1️⃣ **Add Comment 📝**  
```bash
usermod -c "Test User" ul
```
- **📌 Output:** No output if successful. ✅  
- **🔍 Verify:** Check the `/etc/passwd` entry for `ul`.  

---

### 2️⃣ **Change User Shell 🐚**  
```bash
usermod -s /usr/bin/zsh ul
```
- **📌 Output:** No output if successful. ✅  
- **🔍 Verify:** Log in as `ul` and run `echo $SHELL`.  

---

### 3️⃣ **Change User ID (UID) 🆔**  
```bash
usermod -u 1100 ul
```
- **📌 Output:** No output if successful. ✅  
- **🔍 Verify:** Use `id ul` to check the UID.  

---

### 4️⃣ **Change Home Directory 🏠**  
```bash
usermod -d /data/ul ul
```
- **📌 Output:** No output if successful. ✅  
- **🔍 Verify:** Check `/etc/passwd` for the home directory entry.  

---

### 5️⃣ **Check User Status 🔎**  
```bash
grep u1 /etc/shadow
```
- **📌 Output:** Displays the shadow entry for user `u1`, showing password and expiration details.  

---

### 6️⃣ **Generate a Password 🔑**  
```bash
openssl passwd 123
```
- **📌 Output:** Returns a hashed password string. 🔢  
- **🔍 Use:** This can be used to set a password for a user.  

---

### 7️⃣ **Check User Groups 👥**  
```bash
groups ul
```
- **📌 Output:** Lists all groups that user `ul` belongs to.  

---

### 8️⃣ **Check Password Status (Shadow File) 🔍**  
```bash
grep u2 /etc/shadow
```
- **📌 Output:** Displays the shadow entry for user `u2`, indicating password status.  

---

### 9️⃣ **Lock a User Account 🔒**  
```bash
usermod -L u2
```
- **📌 Output:** No output if successful. ✅  
- **🔍 Effect:** Prevents `u2` from logging in.  

---

### 🔟 **Unlock a User Account 🔓**  
```bash
usermod -U u2
```
- **📌 Output:** No output if successful. ✅  
- **🔍 Effect:** Allows `u2` to log in again.  

---

### 1️⃣1️⃣ **Delete a User ❌**  
```bash
userdel u2
```
- **📌 Output:** No output if successful. ✅  
- **🔍 Effect:** Removes user `u2` from the system.  

---

### 1️⃣2️⃣ **Delete User & Home Directory 🏠🗑️**  
```bash
userdel -r u2
```
- **📌 Output:** No output if successful. ✅  
- **🔍 Effect:** Removes `u2` and their home directory.  

---

### 1️⃣3️⃣ **Forcefully Delete User ⚠️❌**  
```bash
userdel -f -r u2
```
- **📌 Output:** No output if successful. ✅  
- **🔍 Effect:** Forcefully removes user `u2` and their home directory without confirmation.  

---

## 📊 **Command Summary Table**  

| 📌 **Command** | 📝 **Description** |
|------------------|----------------------------------|
| `usermod -c "Test User" ul` | 🏷️ Add comment to a user |
| `usermod -s /usr/bin/zsh ul` | 🐚 Change user's shell |
| `usermod -u 1100 ul` | 🆔 Change user's UID |
| `usermod -d /data/ul ul` | 🏠 Change user's home directory |
| `grep u1 /etc/shadow` | 🔍 Check password status of `u1` |
| `openssl passwd 123` | 🔑 Generate a hashed password |
| `groups ul` | 👥 List groups for user `ul` |
| `grep u2 /etc/shadow` | 🔍 Check password status of `u2` |
| `usermod -L u2` | 🔒 Lock user account |
| `usermod -U u2` | 🔓 Unlock user account |
| `userdel u2` | ❌ Delete user `u2` |
| `userdel -r u2` | 🏠🗑️ Delete user & home directory |
| `userdel -f -r u2` | ⚠️❌ Forcefully delete user |

This guide provides **system administrators** with powerful tools to efficiently **manage user accounts** in **Linux environments**. 🚀💻  

---
