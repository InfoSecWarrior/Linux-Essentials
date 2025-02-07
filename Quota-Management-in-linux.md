
# Quota Management in Linux

Quota management in Linux is used to restrict and monitor disk space and inode usage by users and groups on a filesystem. It helps prevent a single user or process from consuming excessive resources.

## Enabling Disk Quotas

### Install Quota Package

- **Debian-based systems:**
  ```bash
  apt install quota -y
  ```

- **RHEL/CentOS:**
  ```bash
  yum install quota -y
  ```

- **Fedora:**
  ```bash
  dnf install quota -y
  ```

## Enable Quotas on a Filesystem

### Modify `/etc/fstab` File
Add quota options for the desired partition:
```bash
/dev/sdb1 /d1 ext4 defaults,usrquota,grpquota 0 0
```

### Remount the Filesystem
```bash
mount -o remount /d1
```

## Create Quota Database
Run the following command to check and create the quota database:
```bash
quotacheck -cum /home
```

### Command Breakdown:
- `c`: Create quota files
- `u`: Check user quotas
- `m`: Do not remount the filesystem as read-only

## Enable Quota
1. Initialize quotas on the filesystem:
    ```bash
    quotaon /d1
    ```
2. Verify quota status:
    ```bash
    quota -ap
    ```

## Additional Commands and Tools

1. **Check Block Device Information:**
    ```bash
    lsblk
    blkid
    df -h
    ```

2. **Format Filesystem:**
    ```bash
    mkfs.ext4 /dev/sdb1
    mkfs.xfs /dev/sdb1
    ```

3. **Quota Management Commands:**
    - `quotacheck -cum /d1`: Check and create quota files
    - `quotacheck -cugv /d2`: Check quotas for users and groups
    - `quota -ap`: Display all quotas
    - `edquota username`: Edit user quotas
    - `touch /d1/aquota.user /d1/aquota.group`: Create required quota files
    - `tune2fs -O quota /dev/sdb1`: Enable quota feature on ext4 filesystem

  ```
