# 🖥 **Linux Disk Partitioning & Management – Complete Guide**  

Linux में **Disk Partitioning** सिस्टम के Storage को Manage करने के लिए आवश्यक प्रक्रिया है।  

✅ **Covers:**  
- **Check Disks & Partitions**  
- **Create, Format, & Mount Partitions**  
- **Modify `/etc/fstab` for Auto-Mount**  
- **Unmount & Remove Partitions**  

📌 **Works for:** Ubuntu, Debian, CentOS, RHEL, Fedora, Rocky Linux, AlmaLinux  

---

# 📌 **1. Check Available Disks & Partitions**  

### 🔹 **1.1 List All Disks and Partitions (`lsblk`)**  
```bash
lsblk
```
📌 **Output Example:**
```
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0   500G  0 disk 
├─sda1   8:1    0   100G  0 part /
└─sda2   8:2    0   400G  0 part /data
sdb      8:16   1   8G    0 disk 
```
✅ **Shows all block devices and their partitions.**  

---

### 🔹 **1.2 Check Disk Details (`fdisk -l`)**  
```bash
sudo fdisk -l
```
📌 **Output Example:**
```
Disk /dev/sda: 500 GiB, 500107862016 bytes, 976773168 sectors
Disk /dev/sdb: 8 GiB, 8589934592 bytes, 16777216 sectors
```
✅ **Lists disk size, sector info, and partitions.**  

---

# 📌 **2. Create a New Partition Using `fdisk`**  

### 🔹 **2.1 Start `fdisk` for the Target Disk (`/dev/sdb`)**  
```bash
sudo fdisk /dev/sdb
```
📌 **Output:**
```
Command (m for help):
```

### 🔹 **2.2 Create a New Partition (`n`)**
```bash
n
```
📌 **Output:**
```
Partition type:
   p   primary (0 primary, 0 extended, 4 free)
   e   extended
Select (default p): 
```
🔹 **Press `ENTER` to select `Primary` partition.**  

---

### 🔹 **2.3 Choose Partition Number & Size**
🔹 Select **Partition Number** (`1`, `2`, etc.) → **Press `ENTER`**  
🔹 Select **First Sector** → **Press `ENTER`**  
🔹 Select **Partition Size (e.g., 4GB)**  
```bash
+4G
```
📌 **Output:**
```
Partition size set to 4 GiB
```
✅ **Creates a 4GB partition.**  

---

### 🔹 **2.4 Save & Exit `fdisk` (`w`)**
```bash
w
```
✅ **Writes changes to disk and exits.**  

---

# 📌 **3. Format the New Partition**  

### 🔹 **3.1 Format as `ext4` Filesystem**  
```bash
sudo mkfs.ext4 /dev/sdb1
```
📌 **Output:**
```
Creating filesystem with 1048576 4k blocks and 262144 inodes
```
✅ **Formats `/dev/sdb1` as `ext4`.**  

---

### 🔹 **3.2 Format as `FAT32` (Optional)**
```bash
sudo mkfs.fat /dev/sdb2
```
📌 **Output:**
```
mkfs.fat 4.1 (2017-01-24)
```
✅ **Formats `/dev/sdb2` as `FAT32`.**  

---

# 📌 **4. Mount the Partition**  

### 🔹 **4.1 Create a Mount Point**
```bash
sudo mkdir /mnt/data1
```
✅ **Creates `/mnt/data1` for mounting the partition.**  

---

### 🔹 **4.2 Mount the Partition**
```bash
sudo mount /dev/sdb1 /mnt/data1
```
✅ **Mounts `/dev/sdb1` to `/mnt/data1`.**  

---

### 🔹 **4.3 Verify Mounted Partitions (`df -h`)**
```bash
df -h
```
📌 **Output Example:**
```
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       100G   20G   80G  20% /
/dev/sdb1       4.0G  1.0G  3.0G  25% /mnt/data1
```
✅ **Shows `/dev/sdb1` is successfully mounted.**  

---

# 📌 **5. Automount Partition on Boot (`/etc/fstab`)**  

### 🔹 **5.1 Find Partition UUID**
```bash
sudo blkid
```
📌 **Output Example:**
```
/dev/sdb1: UUID="e99b27a0-9b32-4f89-91f3-1f6e3c7884b4" TYPE="ext4"
```
✅ **Copy the UUID of `/dev/sdb1`.**  

---

### 🔹 **5.2 Edit `/etc/fstab` to Add Auto-Mount Entry**
```bash
sudo nano /etc/fstab
```
🔹 **Add this line (replace UUID with actual one):**
```
UUID=e99b27a0-9b32-4f89-91f3-1f6e3c7884b4  /mnt/data1  ext4  defaults  0  2
```
✅ **Ensures partition auto-mounts at boot.**  

---

### 🔹 **5.3 Apply Changes**
```bash
sudo mount -a
```
✅ **Mounts all partitions defined in `/etc/fstab`.**  

---

# 📌 **6. Unmount & Remove Partitions**  

### 🔹 **6.1 Unmount a Partition**
```bash
sudo umount /mnt/data1
```
✅ **Unmounts the partition.**  

---

### 🔹 **6.2 Remove Partition (`fdisk`)**
```bash
sudo fdisk /dev/sdb
```
📌 **Inside `fdisk`:**
```bash
d  # Delete a partition
w  # Write changes and exit
```
✅ **Deletes the partition.**  

---

# 📊 **Summary of Linux Disk Partitioning Commands**  
| **Command** | **Purpose** |
|------------|------------|
| `lsblk` | Show all disks and partitions |
| `fdisk -l` | List disk details |
| `fdisk /dev/sdb` | Start partitioning tool |
| `n` | Create a new partition |
| `w` | Save changes & exit `fdisk` |
| `mkfs.ext4 /dev/sdb1` | Format partition as `ext4` |
| `mount /dev/sdb1 /mnt/data1` | Mount partition |
| `df -h` | Check mounted partitions |
| `blkid` | Find partition UUID |
| `nano /etc/fstab` | Edit fstab for auto-mount |
| `mount -a` | Apply fstab changes |
| `umount /mnt/data1` | Unmount partition |
| `fdisk /dev/sdb → d` | Delete partition |

---
