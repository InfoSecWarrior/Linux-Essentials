# **Quota Management in Linux**

Quota management in Linux is used to restrict and monitor disk space and inode usage by users and groups on a filesystem. It helps prevent a single user or process from consuming excessive resources.

## **Enabling Disk Quotas**

### **Install Quota Package**

- **Debian-based systems:**
    
    ```bash
    bash
    CopyEdit
    sudo apt install quota -y
    
    ```
    
- **RHEL/CentOS:**
    
    ```bash
    bash
    CopyEdit
    sudo yum install quota -y
    
    ```
    
- **Fedora:**
    
    ```bash
    bash
    CopyEdit
    sudo dnf install quota -y
    
    ```
    

---

## **Enable Quotas on a Filesystem**

### **Modify `/etc/fstab` File**

Add quota options for the desired partition:

```bash
bash
CopyEdit
/dev/sdb1 /d1 ext4 defaults,usrquota,grpquota 0 0

```

### **Remount the Filesystem**

```bash
bash
CopyEdit
sudo mount -o remount /d1

```

---

## **Create Quota Database**

Run the following command to check and create the quota database:

```bash
bash
CopyEdit
sudo quotacheck -cum /home

```

### **Command Breakdown:**

- `c`: Create quota files
- `u`: Check user quotas
- `m`: Do not remount the filesystem as read-only

---

## **Enable Quota**

1. Initialize quotas on the filesystem:
    
    ```bash
    bash
    CopyEdit
    sudo quotaon /d1
    
    ```
    
2. Verify quota status:
    
    ```bash
    bash
    CopyEdit
    sudo quota -ap
    
    ```
    

---

### **Additional Commands and Tools**

1. **Check Block Device Information:**
    
    ```bash
    bash
    CopyEdit
    lsblk
    blkid
    df -h
    
    ```
    
2. **Format Filesystem:**
    
    ```bash
    bash
    CopyEdit
    sudo mkfs.ext4 /dev/sdb1
    sudo mkfs.xfs /dev/sdb1
    
    ```
    
3. **Quota Management Commands:**
    - `quotacheck -cum /d1`: Check and create quota files
    - `quotacheck -cugv /d2`: Check quotas for users and groups
    - `quota -ap`: Display all quotas
    - `edquota username`: Edit user quotas
    - `touch /d1/aquota.user /d1/aquota.group`: Create required quota files
    - `tune2fs -O quota /dev/sdb1`: Enable quota feature on ext4 filesystem

# **Logical Volume Manager (LVM)  and RAID Setup and Management 

Logical Volume Manager (LVM) is a storage management solution in Linux that provides flexibility and advanced features for managing disk space. It allows dynamic resizing of partitions,
LVM (Logical Volume Manager) Setup and Management Guide

Key Components of LVM

Physical Volume (PV): The actual storage device (e.g., /dev/sdb, /dev/sdc).

Volume Group (VG): A pool of storage created from one or more PVs.

Logical Volume (LV): A partition-like structure inside a VG, where file systems are created.

Setting Up LVM

Step 1: Install LVM (If Not Installed)

Debian/Ubuntu:

apt install lvm2 -y

RHEL/CentOS:

yum install lvm2 -y

Verify Installation:

Check installed packages:

rpm -qa | grep lvm2

List package files:

rpm -ql | grep lvm2

Display package information:

rpm -qi lvm2

Disk Preparation

Free the disk:

fdisk /dev/sdb

Create a single partition:

fdisk /dev/sdb

Check system block devices:

lsblk

View mounted filesystems:

df -h

Edit fstab (remove any unwanted entries):

vim /etc/fstab

Step 2: Create Physical Volume

Identify available disks:

lsblk

Initialize the disk as an LVM physical volume:

pvcreate /dev/sdb /dev/sdc

Display physical volume details:

pvdisplay

Verify physical volumes:

pvs

Step 3: Create a Volume Group

Create a volume group named vg_data:

vgcreate vg_data /dev/sdb /dev/sdc

Display volume group details:

vgdisplay

Step 4: Create a Logical Volume

Create a 60 GB logical volume named lv_storage:

lvcreate -L 60G -n lv_storage vg_data

Check the logical volume content:

lvs

Step 5: Formatting and Mounting the LVM Partition

Format the logical volume:

mkfs.ext4 /dev/vg_data/lv_storage

Create a mount point:

mkdir /mnt/storage

Mount the logical volume:

mount /dev/vg_data/lv_storage /mnt/storage

Verify the block devices:

lsblk

Check filesystem UUID:

blkid

Verify the mount:

df -h

Copy logs as a test:

cp -vr /var/log/* /mnt/storage

List contents:

ls -lh /mnt/storage

Resizing Logical Volumes

Extend an LV (Increase Size)

Extend the logical volume by 10 GB:

lvextend -L +10G /dev/vg_data/lv_storage

Resize the filesystem:

resize2fs /dev/vg_data/lv_storage

Verify the change:

df -h /mnt/storage

Shrink an LV (Reduce Size)

Unmount the volume:

umount /mnt/storage

Check and reduce the filesystem:

e2fsck -f /dev/vg_data/lv_storage
resize2fs /dev/vg_data/lv_storage 15G

Reduce the logical volume size:

lvreduce -L 15G /dev/vg_data/lv_storage

Remount the volume:

mount /dev/vg_data/lv_storage /mnt/storage

Mounting Snapshots

Mount the snapshot:

mount /dev/vg_data/lv_snapshot /mnt/snapshot

Remove the snapshot after use:

umount /dev/vg_data/lv_snapshot
lvremove /dev/vg_data/lv_snapshot

Removing LVM Components

Remove a Logical Volume

Unmount the logical volume:

umount /mnt/storage

Remove the logical volume:

lvremove /dev/vg_data/lv_storage

Verify removal:
lvdisplay



