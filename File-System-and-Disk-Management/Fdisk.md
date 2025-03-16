# FDISK COMMANDS

Fdisk is a Linux command-line tool for managing disk partitions, supporting both MBR and GPT partition schemes. It enables users to create, delete, modify, and view partitions interactively.

---

## Basic Syntax

```
fdisk [options] <device>
```
- `<device>`: Specifies the disk device (e.g., `/dev/sda`, `/dev/nvme0n1`).

---

## Basic Concepts

- **Disk:**  
  A storage device like `/dev/sda`, `/dev/sdb`, etc.

- **Partition:**  
  A subdivision of a disk. It can contain a filesystem or swap space. For example, `/dev/sdb1` is the first partition on disk `/dev/sdb`.

---

## Partition Types Supported

- **MBR (DOS partition table):**  
  Default for older systems and disks ≤ 2TB.
  
- **GPT (GUID Partition Table):**  
  Required for UEFI boot and disks > 2TB.
  
- **Sun Partition Table:**  
  Used in legacy Sun systems.
  
- **SGI (IRIX) Partition Table:**  
  Used in SGI IRIX systems (rare).

---

## List All Available Storage Devices and Partitions

- **List in a tree structure:**
```
lsblk
```

*Example Output:*
```
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0   500G  0 disk
├─sdb1   8:1    0   100G  0 part /
├─sdb2   8:2    0    50G  0 part /home
├─sdb3   8:3    0   350G  0 part /data
```

- **View Detailed Information:**
```
fdisk -l
```

*Example Output:*
```
Disk /dev/sda: 500 GiB, 536870912000 bytes, 1048576000 sectors
Device     Boot Start       End   Sectors  Size Id Type
/dev/sdb1  *     2048   2099199   2097152  100M 83 Linux
/dev/sdb2       2099200  4196351   2097152  100M 82 Linux swap
/dev/sdb3       4196352 1048575999 1044389648 500G 83 Linux
```

---

## Opening a Specific Disk in Fdisk

*Caution: Choose the correct disk (e.g., `/dev/sdX`) to avoid data loss.*

```
fdisk /dev/sdX
```

This command opens the disk in interactive mode.

---

## Interactive Mode Commands

- **Display Help Menu:**
```
m
```

- **Initialize Disk with GPT Partition Table:**
```
g
```

- **Initialize Disk with MBR (DOS) Partition Scheme:**
```
o
```

- **Print the Current Partition Table:**
```
p
```

*Example Output:*
```
Device     Boot    Start      End  Sectors Size Id Type
/dev/sdd1           2048 10487807 10485760   5G 83 Linux
/dev/sdd2       10487808 20973567 10485760   5G 83 Linux
/dev/sdd3       20973568 41943039 20969472  10G 83 Linux
```

- **Create a New Partition:**
```
n
```

  *Interactive Steps:*  
  1. **Choose Partition Type (MBR only):**  
     - For Primary partition:  
       ```
       p
       ```
     - For Extended partition:  
       ```
       e
       ```
     - For Logical partition (only if an extended partition exists):  
       ```
       l
       ```

  2. **Choose Partition Number:**  
     - **MBR:** 1–4  
     - **GPT:** 1 to 128 (or higher, depending on disk size)

  3. **Select Starting Sector:**  
     When prompted, press Enter to accept the default.
     *Example prompt:*  
     ```
     First sector (2048-41943039, default 2048):
     ```

  4. **Select Partition Size:**  
     Specify size with suffixes K, M, G, T, or P.
     - For 10 KB:  
       ```
       +10K
       ```
     - For 10 MB:  
       ```
       +10M
       ```
     - For 10 GB:  
       ```
       +10G
       ```
     - For 10 TB:  
       ```
       +10T
       ```
     - For 10 PB:  
       ```
       +10P
       ```
     When prompted for the last sector, press Enter or specify size accordingly.

- **Toggle Bootable Flag:**  
  Toggles the bootable flag on a partition.
  ```
  a
  ```

- **Change Partition Type:**
```
t
```

  *After invoking, follow these steps:*
  1. **Select the Partition Number.**
  2. **Enter the New Partition Type Code.**

  **MBR Partition Type Codes:**

  | Partition Type     | Code |
  |--------------------|------|
  | Linux              | 83   |
  | Swap               | 82   |
  | Extended           | 05   |
  | UEFI               | EF   |
  | RAID               | FD   |
  | LVM                | 8E   |
  | Linux extended     | 85   |

  **GPT Partition Type Codes:**

  | Partition Type     | Code |
  |--------------------|------|
  | Linux              | 20   |
  | Swap               | 19   |
  | Home               | 28   |
  | UEFI               | 1    |
  | RAID               | 29   |
  | LVM                | 30   |

- **Delete a Partition:**  
  Erases all data in the partition.
  ```
  d
  ```

- **Display Detailed Partition Information:**  
  Shows detailed info about a selected partition.
  ```
  i
  ```

*Example Output:*
```
Selected partition 1
         Device: /dev/sdb1
          Start: 2048
            End: 2099199
        Sectors: 2097152
      Cylinders: 131
           Size: 1G
             Id: 83
           Type: Linux
    Start-C/H/S: 0/32/33
      End-C/H/S: 130/170/40
```

- **Write Changes to Disk:**  
  Saves the current partition table changes.
  ```
  w
  ```

- **Exit Without Saving:**  
  Exits fdisk without writing any changes to disk.
  ```
  q
  ```

- **List Free Unpartitioned Space:**  
  Displays unpartitioned (free) space on the disk.
  ```
  F
  ```

*Example Output:*
```
Unpartitioned space /dev/sdb: 0 B, 0 bytes, 0 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
```

- **Verify Partition Table Consistency:**  
  Checks the partition table for errors.
  ```
  v
  ```

*Example Output:*
```
No errors detected.
```

- **Dump Partition Layout to an sfdisk Script File:**  
  Outputs the partition table layout in sfdisk script format.
  ```
  O
  ```

- **Load Disk Layout from an sfdisk Script File:**  
  Loads a previously dumped partition layout.
  ```
  I
  ```

- **Change Display Units:**  
  Changes the display units (sectors, bytes, cylinders).
  ```
  u
  ```

- **Enter Expert Mode:**  
  Enters expert mode for advanced disk modifications.
  ```
  x
  ```

# GDISK COMMANDS

Gdisk is used for managing GPT (GUID Partition Table) disks. Use gdisk when dealing with modern systems that use UEFI or when working with disks larger than 2TB. In contrast, use fdisk for older systems with MBR partition schemes. Use fdisk for managing MBR disks (older systems, BIOS) and gdisk for GPT disks (modern UEFI systems, disks >2TB). The commands below provide a concise reference to view, create, delete, and modify GPT partitions using gdisk. Use these commands carefully to manage your disk partitions effectively.

---

## Basic Syntax

```
gdisk [options] <device>
```
- **<device>**: Disk device (e.g., `/dev/sda`, `/dev/nvme0n1`).

---

## Key Commands

- **List Partition Table:**  
  ```
  gdisk -l /dev/sda
  ```  
  Displays detailed partition information for the specified disk.

- **Open Disk in Interactive Mode:**  
  ```
  gdisk /dev/sda
  ```  
  Opens the disk for partition management (choose the correct disk!).

- **Display Help:**  
  In interactive mode, type:
  ```
  ?
  ```

- **Print Partition Table:**  
  Inside interactive mode, type:
  ```
  p
  ```

- **Create New Partition:**  
  In interactive mode, type:
  ```
  n
  ```  
  Follow prompts to specify partition number (GPT: 1–128), starting sector (default accepted by pressing Enter), and size (e.g., `+10G`).

- **Delete a Partition:**  
  In interactive mode, type:
  ```
  d
  ```  
  Then enter the partition number to delete.

- **Change Partition Type:**  
  In interactive mode, type:
  ```
  t
  ```  
  Then choose the partition number and enter the new type code. Use `l` (lowercase L) to list valid type codes.

- **Display Detailed Partition Info:**  
  In interactive mode, type:
  ```
  i
  ```

- **Verify Partition Table:**  
  In interactive mode, type:
  ```
  v
  ```

- **Write Changes to Disk:**  
  To commit changes, type:
  ```
  w
  ```

- **Quit Without Saving:**  
  To exit without saving changes, type:
  ```
  q
  ```
