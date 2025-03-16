# MOUNT COMMANDS

The `mount` command is used to attach filesystems to a specified directory in the Linux filesystem hierarchy. Below is a concise guide to using the `mount` command for various tasks.

---

## Basic Syntax

```
mount [options] <device> <mount_point>
```
- **device**: The device or partition to be mounted (e.g., `/dev/sda1`).
- **mount_point**: The directory where the filesystem will be attached (e.g., `/mnt/data`).

---

## Common Mounting Commands

- **Mount a Filesystem:**
  ```
  mount /dev/sdXn /mnt/data
  ```

- **Mount with a Specific Filesystem Type:**
  ```
  mount -t ext4 /dev/sdXn /mnt/data
  ```

- **Mount with Read-Only Option:**
  ```
  mount -o ro /dev/sdXn /mnt/data
  ```

- **Mount with Specific Options:**
  ```
  mount -o defaults,noatime /dev/sdXn /mnt/data
  ```

- **Bind Mount (Mount a Directory to Another Location):**
  ```
  mount --bind /source/directory /target/directory
  ```

- **Remount a Filesystem with Different Options:**
  ```
  mount -o remount,rw /dev/sdXn /mnt/data
  ```

- **Mount an ISO File:**
  ```
  mount -o loop /path/to/file.iso /mnt
  ```

- **Mount an NFS (Network File System) Share:**
  ```
  mount -t nfs server:/path/to/share /mnt
  ```

- **Mount with Verbose Output:**
  ```
  mount -v /dev/sda1 /mnt
  ```

---

## Viewing Mounted Filesystems

- **List All Mounted Filesystems:**
  ```
  mount
  ```

- **List Mounted Filesystems (Alternative):**
  ```
  findmnt
  ```

- **View Filesystem Disk Space Usage:**
  ```
  df -h
  ```

- **List Block Devices:**
  ```
  lsblk
  ```

---

## Unmounting Filesystems

- **Unmount a Filesystem:**
  ```
  umount /mnt/data
  ```

- **Unmount Using Device Name:**
  ```
  umount /dev/sdXn
  ```

- **Lazy Unmount (Detach Even if Busy):**
  ```
  umount -l /mnt
  ```

- **Forced Unmount:**
  ```
  umount -f /mnt
  ```

---

## Managing Mounted Filesystems

- **Mount All Filesystems from /etc/fstab:**
  ```
  mount -a
  ```

- **Find Processes Using a Mount Point:**
  ```
  lsof +D /mnt
  ```

- **Kill Processes Blocking Unmounting:**
  ```
  fuser -vm /mnt
  ```
  ```
  kill -9 <PID>
  ```

---

## Persistent Mounts

To make mounts persistent across reboots, add entries to the `/etc/fstab` file.

*Example `/etc/fstab` entry:*
```
/dev/sdXn  /mnt/data  ext4  defaults  0  2
```

