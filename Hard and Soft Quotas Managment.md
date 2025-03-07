# 🔥 **How to Set Up Disk Quotas in Linux** 🔥  

Disk quotas **limit** how much disk space a user or group can use. Here’s a step-by-step guide to **configure disk quotas with both hard and soft limits** in Linux.  

✅ **Works on:** RHEL, CentOS, Ubuntu, Debian, Fedora  
✅ **Applies to:** Users and Groups  

---

## **📌 Step 1: Enable Quotas on a File System**  

Before applying quotas, you need to enable them on your file system.  

### 🔹 **Modify `/etc/fstab`**
Edit the `/etc/fstab` file to enable **user (`usrquota`)** and **group (`grpquota`)** quotas.

```bash
sudo nano /etc/fstab
```

🔹 **Modify the line for `/home`** (or the partition where quotas will be applied):

```plaintext
/dev/sdb1   /home   ext4   defaults,usrquota,grpquota   0 2
```

✅ **This enables user and group quotas on `/home`.**  

---

## **📌 Step 2: Remount the File System**  

For the changes to take effect, remount the partition.  

```bash
sudo mount -o remount /home
```

Alternatively, **reboot the system**:

```bash
sudo reboot
```

✅ **Now, the file system is ready for quotas.**  

---

## **📌 Step 3: Create Quota Database Files**  

Create the necessary **quota files** on the `/home` partition.

```bash
sudo quotacheck -cug /home
```

📌 **Explanation:**
- `-c` → Create new quota files  
- `-u` → Enable **user** quotas  
- `-g` → Enable **group** quotas  

✅ **Generates `aquota.user` and `aquota.group` files in `/home`.**  

---

## **📌 Step 4: Assign Quotas to a User**  

Let’s set up a **quota** for a user named `testuser`.  

```bash
sudo edquota testuser
```

🔹 **This opens a quota editor:**  
```plaintext
Disk quotas for user testuser (uid 1001):
Filesystem         blocks    soft    hard  inodes  soft  hard
/dev/sdb1         1000000  5000000  5500000  1000  5000  5500
```

📌 **Set soft and hard limits:**
- **Soft limit:** The user gets a warning when exceeding this.  
- **Hard limit:** The user **cannot** exceed this limit.  

✅ **Example:**
- **Soft limit:** `5,000,000` blocks  
- **Hard limit:** `5,500,000` blocks  
- **Soft inodes:** `5,000`  
- **Hard inodes:** `5,500`  

Save and exit (`Ctrl + X`, then `Y`, then `Enter`).  

---

## **📌 Step 5: Assign Quotas to a Group**  

To assign quotas to a group **(e.g., `developers`)**:  

```bash
sudo edquota -g developers
```

🔹 **Modify limits like this:**
```plaintext
Disk quotas for group developers (gid 1010):
Filesystem         blocks    soft    hard  inodes  soft  hard
/dev/sdb1         2000000 10000000 11000000  2000 10000 11000
```

✅ **This applies quotas to all users in the `developers` group.**  

---

## **📌 Step 6: Set Grace Period for Soft Limits**  

You can **give users extra time** before enforcing the soft limit.  

```bash
sudo edquota -t
```

🔹 **Modify the grace period like this:**
```plaintext
Grace period before enforcing soft limits:
Filesystem     Block grace period    Inode grace period
/dev/sdb1     7days                 5days
```

✅ **Users have 7 days to reduce their disk usage before enforcement.**  

---

## **📌 Step 7: Turn on Quotas**  

To activate quotas:  

```bash
sudo quotaon -v /home
```

📌 **Output Example:**  
```
/dev/sdb1 [SUCCESS]: user and group quotas turned on
```

✅ **Quotas are now enforced!**  

---

## **📌 Step 8: Verify Quotas**  

To **check** the quota usage of `testuser`:  

```bash
sudo quota testuser
```

📌 **Example Output:**  
```plaintext
Disk quotas for user testuser (uid 1001):
Filesystem   blocks   quota   limit   grace   files   quota   limit   grace
/dev/sdb1   4000000 5000000 5500000       -      800   5000   5500      -
```

✅ **User is using `4,000,000` blocks out of `5,000,000` (soft limit).**  

---

## **📌 Step 9: Check All Users & Groups**  

🔹 **Check all user quotas:**  
```bash
sudo repquota -a
```

🔹 **Check a group quota:**  
```bash
sudo quota -g developers
```

---

## **📌 Step 10: Disable Quotas (if needed)**  

To temporarily **turn off quotas**:  
```bash
sudo quotaoff -v /home
```

📌 **Output Example:**  
```
/dev/sdb1 [SUCCESS]: user and group quotas turned off
```

✅ **This disables quotas on `/home`.**  

---

# **📊 Summary of Disk Quota Commands**  

| Command | Description |
|---------|-------------|
| `nano /etc/fstab` | Enable `usrquota,grpquota` in `/home` |
| `mount -o remount /home` | Apply `/etc/fstab` changes |
| `quotacheck -cug /home` | Create quota database files |
| `quotaon -v /home` | Enable disk quotas |
| `quotaoff -v /home` | Disable disk quotas |
| `edquota testuser` | Set quotas for a user |
| `edquota -g developers` | Set quotas for a group |
| `edquota -t` | Set grace periods |
| `quota testuser` | Check quota for a user |
| `quota -g developers` | Check quota for a group |
| `repquota -a` | Show all quota usage |

---
