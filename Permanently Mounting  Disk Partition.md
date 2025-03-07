# 📌 **How to Permanently Mount a Disk Partition in Linux**  

When you add a new disk partition, **you must configure it to mount automatically on boot**. Here’s a complete step-by-step guide to permanently mounting a partition in Linux.

✅ **Works for:** Ubuntu, Debian, CentOS, RHEL, Fedora, Rocky Linux, AlmaLinux  
✅ **Covers:** Disk identification, partitioning, formatting, mounting, and configuring `/etc/fstab` for auto-mount  

---

# 📌 **1. Identify Available Disks & Partitions**  

### 🔹 **Step 1: Check Existing Partitions (`lsblk`)**
```bash
lsblk
```
📌 **Output Example:**
```
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0   500G  0 disk 
├─sda1   8:1    0   100G  0 part /
└─sda2   8:2    0   400G  0 part /data
sdb      8:16   1   100G  0 disk 
```
✅ **Disk `/dev/sdb` is unmounted and ready to be configured.**  

---

# 📌 **2. Create a Partition (if needed)**  

### 🔹 **Step 1: Open `fdisk` for the Target Disk**  
```bash
sudo fdisk /dev/sdb
```
📌 **Inside `fdisk`:**
```bash
n   # Create new partition
p   # Primary partition
1   # Partition number (1)
ENTER  # Default first sector
ENTER  # Default last sector (uses full disk)
w   # Write changes & exit
```
✅ **Creates `/dev/sdb1` partition.**  

---

# 📌 **3. Format the Partition**  

### 🔹 **Step 1: Format as `ext4` Filesystem**
```bash
sudo mkfs.ext4 /dev/sdb1
```
📌 **Output Example:**
```
Creating filesystem with 5242880 4k blocks and 1310720 inodes
```
✅ **Formats `/dev/sdb1` as `ext4`.**  

---

# 📌 **4. Create a Mount Point & Temporarily Mount the Partition**  

### 🔹 **Step 1: Create a Mount Directory**
```bash
sudo mkdir /mnt/data
```
✅ **Creates `/mnt/data` to mount the new partition.**  

---

### 🔹 **Step 2: Mount the Partition**
```bash
sudo mount /dev/sdb1 /mnt/data
```
✅ **Mounts `/dev/sdb1` to `/mnt/data`.**  

---

### 🔹 **Step 3: Verify Mount (`df -h`)**
```bash
df -h
```
📌 **Output Example:**
```
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdb1       100G  1.0G  99G   5% /mnt/data
```
✅ **New disk is successfully mounted!** 🎉  

---

# 📌 **5. Auto-Mount the Partition at Boot (`/etc/fstab`)**  

### 🔹 **Step 1: Get the Partition UUID**
```bash
sudo blkid
```
📌 **Example Output:**
```
/dev/sdb1: UUID="abcd-1234-efgh-5678" TYPE="ext4"
```
✅ **Copy the UUID of `/dev/sdb1`.**  

---

### 🔹 **Step 2: Edit `/etc/fstab` to Auto-Mount**  
```bash
sudo nano /etc/fstab
```
🔹 **Add this line at the end:**
```
UUID=abcd-1234-efgh-5678  /mnt/data  ext4  defaults  0  2
```
✅ **Ensures the disk mounts automatically on boot.**  

---

### 🔹 **Step 3: Apply Changes & Test**
```bash
sudo mount -a
```
✅ **Confirms `fstab` changes.**  

---

# 📌 **6. Verify Everything After Reboot**  

### 🔹 **Step 1: Reboot the System**
```bash
sudo reboot
```
✅ **Reboots the system to check if the partition auto-mounts.**  

---

### 🔹 **Step 2: Check Mounted Partitions**
```bash
df -h
```
📌 **Output Example:**
```
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdb1       100G  1.0G  99G   5% /mnt/data
```
✅ **Partition `/dev/sdb1` is automatically mounted at `/mnt/data`.** 🎉  

---

# 📊 **Summary Table of Linux Disk Mounting Commands**  
| **Step** | **Command** | **Purpose** |
|---------|------------|------------|
| **1. Check Disks** | `lsblk` | List all disks & partitions |
| **2. Create Partition** | `fdisk /dev/sdb` → `n` → `w` | Create new partition |
| **3. Format Partition** | `mkfs.ext4 /dev/sdb1` | Format as `ext4` |
| **4. Mount Temporarily** | `mount /dev/sdb1 /mnt/data` | Temporary mount |
| **5. Get UUID** | `blkid` | Get partition UUID |
| **6. Auto-Mount at Boot** | Edit `/etc/fstab` | Make permanent mount |
| **7. Apply Changes** | `mount -a` | Verify `/etc/fstab` changes |
| **8. Verify & Reboot** | `df -h`, `reboot` | Check & confirm |

---
