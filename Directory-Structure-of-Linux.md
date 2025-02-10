# Linux Directory Structure 

The Linux directory structure is organized hierarchically and adheres to the **Filesystem Hierarchy Standard (FHS)**, ensuring a consistent way of locating files and directories across Linux distributions. Below is an overview table of each major directory, its purpose, and examples of its usage.

## Overview Table

| Directory | Purpose |
| --- | --- |
| `/` | Root directory, the top-most level of the file system. Contains all other directories. |
| `/bin` | Essential system binaries for basic commands (e.g., `ls`, `cp`, `mv`). |
| `/sbin` | System binaries for administrative tasks, usually executed by the root user (e.g., `fsck`, `reboot`). |
| `/etc` | Configuration files for the system and applications (e.g., network, user settings). |
| `/dev` | Device files representing hardware devices (e.g., `tty`, `sda`, `null`). |
| `/proc` | Virtual files providing process and kernel information, such as `/proc/cpuinfo` and `/proc/meminfo`. |
| `/home` | Home directories for regular users where personal files and configurations are stored. |
| `/root` | Home directory for the root user (administrator). |
| `/lib` | Shared libraries required by system binaries and programs to run. |
| `/lib64` | 64-bit shared libraries for modern systems, similar to `/lib` but for 64-bit architecture. |
| `/media` | Mount points for removable media (e.g., CD/DVD drives, USB drives). |
| `/mnt` | Temporary mount points for manually mounted devices (e.g., mounting a network share). |
| `/opt` | Optional application software and packages not part of the core system. |
| `/srv` | Service data provided by the system, such as web server data or FTP server data. |
| `/tmp` | Temporary files used by applications. Cleared on reboot. |
| `/usr` | User programs, data, and shared files. This directory contains most user utilities and applications. |
| `/var` | Variable data files that change during system operation (e.g., logs in `/var/log`, spools, cache). |
| `/run` | Runtime data for processes since the last boot. Replaces `/var/run` and is available early during boot. |
| `/pwd`  | Display the full path of the current directory |

---

Below is a detailed explanation of each directory.

## 1. `/` (Root Directory)

- **What It Is**: The root directory is the starting point of the Linux filesystem hierarchy. It is represented by a single forward slash (`/`). All other files and directories are contained within this directory.

- **Purpose**: Serves as the top-level directory from which all other directories branch out.

- **Key Note**: Only the root user (administrator) has full access to this directory.

## 2. `/bin` (User Binaries)

- **What It Is**: The `/bin` directory contains essential user command binaries (executables) needed for system booting, repairing, maintenance, and basic operations.

- **Purpose**: Stores basic commands and utilities that are used by all users on the system.

- **Examples**: `ls` (list directory contents), `cat` (concatenate files), `cp` (copy files), `mv` (move/rename files), `mkdir` (create directories).

- **Relevance for Pentesters**: Contains shells like `sh` and `bash`, which can be used for scripting and command execution.

## 3. `/sbin` (System Binaries)

- **What It Is**: The `/sbin` directory holds binary executables used for system administration tasks. These commands are typically used by the root user for system maintenance.

- **Purpose**: Stores essential system binaries required for booting and system recovery.

- **Examples**: `fsck` (filesystem check), `reboot` (restart the system), `ifconfig` (network interface configuration).

- **Relevance for Pentesters**: Includes tools like `iptables`, which can be inspected for firewall configurations and potential exploitation.

## 4. `/etc` (Configuration Files)

- **What It Is**: The `/etc` directory contains system-wide configuration files and directories. It holds settings and configurations for the operating system and installed applications.

- **Purpose**: Stores all the administrative, configuration, and other system-related files.

- **Examples**:
  - `/etc/passwd`: Contains user account information.
  - `/etc/shadow`: Stores hashed user passwords (accessible only by root).
  - `/etc/ssh/sshd_config`: Configuration file for the SSH server.

- **Relevance for Pentesters**: Critical for analyzing system configurations, potential misconfigurations, and retrieving sensitive information like user credentials.

## 5. `/dev` (Device Files)

- **What It Is**: The `/dev` directory is a special location that contains device files representing hardware components and peripherals. These are special files that act as interfaces to the hardware devices.

- **Purpose**: Provides a unified way to access hardware devices, treating them as files.

- **Examples**:
  - `/dev/null`: Discards all data written to it; acts as a black hole.
  - `/dev/sda`: Represents the first hard disk drive.
  - `/dev/tty`: Represents terminal devices.

- **Relevance for Pentesters**: Access to device files like `/dev/mem` or `/dev/kmem` can lead to sensitive information disclosure or privilege escalation.

## 6. `/proc` (Process Information)

- **What It Is**: The `/proc` directory is a virtual filesystem that provides a hierarchical view of the processes and kernel parameters. It contains files that represent system and process information.

- **Purpose**: Allows the system and users to access process and system information dynamically.

- **Examples**:
  - `/proc/cpuinfo`: Displays information about the CPU.
  - `/proc/meminfo`: Provides memory usage information.
  - `/proc/[PID]/`: Contains information about a specific process with the given PID (Process ID).

- **Relevance for Pentesters**: Useful for monitoring running processes, extracting command-line arguments, and identifying potential targets.

## 7. `/home` (User Home Directories)

- **What It Is**: The `/home` directory contains the personal directories of all regular (non-root) users on the system. Each user has a subdirectory within `/home` to store personal files and configurations.

- **Purpose**: Provides a personal workspace for users to store their documents, media, and configuration files.

- **Examples**:
  - `/home/alice`: Home directory for the user `alice`.
  - `/home/bob`: Home directory for the user `bob`.

- **Relevance for Pentesters**:
  - Accessing user files may reveal sensitive information.
  - SSH keys and configuration files in `/home/user/.ssh/` can be used for privilege escalation or lateral movement.

## 8. `/root` (Root User Home Directory)

- **What It Is**: The `/root` directory is the home directory for the root user, the superuser or administrator of the system.

- **Purpose**: Stores personal files and settings for the root user, separate from other users' data.

- **Relevance for Pentesters**: Gaining access to `/root` can provide complete control over the system and access to all sensitive data.

## 9. `/lib` and `/lib64` (Libraries)

- **What It Is**: The `/lib` and `/lib64` directories contain shared libraries needed by the binaries in `/bin` and `/sbin`. These libraries are similar to DLL files in Windows.

- **Purpose**: Provides essential shared libraries required by system programs to function properly.

- **Examples**:
  - `/lib/libc.so.6`: The GNU C Library.
  - `/lib64/`: Contains 64-bit libraries on systems that support both 32-bit and 64-bit applications.

- **Relevance for Pentesters**: Outdated or vulnerable libraries can be exploited to execute arbitrary code or escalate privileges.

## 10. `/media` and `/mnt` (Mount Points)

- **What It Is**:
  - `/media`: Default mount point for removable media devices automatically mounted by the system, such as CDs, DVDs, and USB drives.
  - `/mnt`: A directory where system administrators can mount temporary file systems manually.

- **Purpose**: Provides standard locations for mounting external storage devices, making them accessible to the system.

- **Relevance for Pentesters**: External media can be used to introduce malicious software or extract data from the system.

## 11. `/opt` (Optional Software)

- **What It Is**: The `/opt` directory is used for installing additional or optional software packages that are not part of the default installation.

- **Purpose**: Stores third-party applications, typically in self-contained directories.

- **Examples**:
  - `/opt/google/chrome`: Installation directory for Google Chrome.
  - `/opt/myapp`: Custom application installed by the user.

- **Relevance for Pentesters**: Software here may not be managed by the system's package manager and could contain vulnerabilities due to outdated versions.

## 12. `/srv` (Service Data)

- **What It Is**: The `/srv` directory holds data for services provided by the system, such as web servers, FTP servers, and repositories.

- **Purpose**: Stores site-specific data served by the system.

- **Examples**:
  - `/srv/www`: Data for a web server.
  - `/srv/ftp`: Files for an FTP server.

- **Relevance for Pentesters**: Contains service data that might reveal information about services running on the system and potential misconfigurations.

## 13. `/tmp` (Temporary Files)

- **What It Is**: The `/tmp` directory is a world-writable space used for storing temporary files created by applications and the system.

- **Purpose**: Allows programs to store transient data that doesn't need to persist across reboots.

- **Relevance for Pentesters**:
  - Can be used to upload and execute malicious scripts.
  - World-writable permissions may be exploited if proper security measures aren't in place.

## 14. `/usr` (User System Resources)

- **What It Is**: The `/usr` directory (Unix System Resources) contains user programs, libraries, documentation, and other shared resources.

- **Purpose**: Stores applications and files that are not essential for booting or repairing the system but are used during normal operations.

- **Subdirectories**:
  - `/usr/bin`: General user command binaries (e.g., `gcc`, `python`).
  - `/usr/sbin`: Non-essential system administration binaries.
  - `/usr/local`: Locally installed software and custom applications.
  - `/usr/share`: Shared resources like documentation and icons.

- **Relevance for Pentesters**: Misconfigured or vulnerable applications installed here can be targeted for exploitation.

## 15. `/var` (Variable Data)

- **What It Is**: The `/var` directory contains variable files that are expected to grow over time, such as logs, mail spools, and caches.

- **Purpose**: Stores data that changes frequently during system operation.

- **Examples**:
  - `/var/log`: System and application log files (e.g., `auth.log`, `syslog`).
  - `/var/www`: Default web server document root.
  - `/var/mail`: Incoming email storage.

- **Relevance for Pentesters**:
  - Logs can reveal information about system activity and potential vulnerabilities.
  - Access to web server files can lead to web application attacks.

## 16. `/run` (Runtime Variable Data)

- **What It Is**: The `/run` directory is a temporary filesystem that stores runtime data for processes since the last boot. It replaces older directories like `/var/run`.

- **Purpose**: Holds transient files like process IDs (PIDs), sockets, and other system information needed during operation.

- **Examples**:
  - `/run/nginx.pid`: Stores the process ID of the Nginx service.
  - `/run/systemd/journal/socket`: Socket file for systemd journaling.

- **Relevance for Pentesters**:
  - May contain sensitive information in temporary files.
  - Misconfigured permissions could allow unauthorized access to system processes.

Certainly! Here's an explanation of the `pwd` command in a similar format:

---

## 17. `pwd` (Print Working Directory)

- **What It Is**: The `pwd` command is used to display the full path of the current directory you're in within the filesystem. It stands for "Print Working Directory."

- **Purpose**: Helps users identify their current location in the filesystem, especially when navigating through different directories in the terminal.

- **How It Works**: When you run `pwd`, it outputs the absolute path of the directory you're currently working in, starting from the root directory `/`.

- **Examples**:
  - After running `pwd` in the `/home/user/Documents` directory, you might see:
    ```
    /home/user/Documents
    ```
  - Running `pwd` in `/etc/nginx` might return:
    ```
    /etc/nginx
    ```

- **Relevance for Users**:
  - Helps you understand where you are in the file system and aids navigation.
  - Useful when performing tasks like finding or creating files in the current directory.
  - Can assist in scripting by providing the current directory's full path.


---
