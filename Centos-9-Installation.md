## CentOS 9 Installation (GUI)
[Download CentOS 9 Stream ISO](https://mirror.stream.centos.org/9-stream/BaseOS/x86_64/iso/CentOS-Stream-9-20250210.0-x86_64-dvd1.iso)

### VirtualBox Setup

1. Open VirtualBox and click **New**.
2. Set the name to **CentOS 9**, type to **Linux**, and version to **Red Hat (64-bit)**.
3. Allocate **1024 MB** RAM.
4. Create a virtual disk:
   - Select **VDI (Virtual Disk Image)**.
   - Choose **Dynamically allocated**.
   - Set **file location and size to 40 GB**.
5. Start the virtual machine, select the CentOS 9 ISO, and click **Start**.

## Installation

1. Choose **Install CentOS 9**.
2. Select **English > English (India) > Continue**.
3. Configure settings:
   - **Date & Time**: Asia/Kolkata > Done.
   - **Keyboard Layout**: English (India, with rupee) > Add English (US) > Done.
   - **Language Support**: English (India) > Done.
   - **Installation Source**: Verify ISO > Done.
   - **Software Selection**: Select **Server with GUI**.
4. Configure partitioning:
   - **Custom partitioning** > Done.
   - Create partitions:
     - `/boot` - **1024 MiB**, **ext4**, Standard.
     - `swap` - **4096 MiB**, Standard.
     - `/` - **XFS file system**, Standard.
   - Click **Done > Accept Changes**.
5. **KDUMP**: No changes.
6. **Network & Hostname**:
   - Enable **enp0s3**.
   - Configure IPv4 manually, disable IPv6, save settings.
   - Set hostname to **simran**.
7. **Security Policy**: No changes.
8. Click **Begin Installation**.
9. Set **root password** and create a user:
   - Full name: `simran`.
   - Username: `simran`.
   - Tick **Make this user administrator**.
10. Click **Done > Done**, then **Reboot**.
11. Accept **License Agreement**.
12. **Finish Configuration**.

## Install Drivers

1. Go to **Device > Network > Network Settings > Bridged Adapter**.
2. Run the following commands:
   ```bash
   yum install gcc
   yum install kernel-devel
   reboot
   ```
3. Insert Guest Additions CD:
   - Go to **Device > Insert Guest Additions CD Image > Run**.
   - Reboot the system.

### If Installation Fails, Use These Commands:

```bash
rpm -q kernel-devel
```
```bash
uname -r
```
```
yum update kernel-*
yum install epel-release.noarch
yum install gcc make perl kernel-devel kernel-headers bzip2 dkms
yum install make perl
yum install kernel-devel-$(uname -r)
yum install epel-release
reboot
device > Insert Guest Additions CD image > Run
reboot
```

## Verify MD5 Checksum for ISO

1. Download the **MD5 checksum** file for CentOS 9.
2. Open the command prompt and run:
   ```bash
   md5sum filename.iso
   ```
3. Compare the generated checksum with the official checksum.

## SSH Not Working on Windows 7

1. **Install PuTTY**:
   - Download from [PuTTY Official Site](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html).
   - Install it on your system.

2. **Launch PuTTY**:
   - Open **Start Menu**, search for **PuTTY**, and launch it.

3. **Connect to CentOS Server**:
   - In **PuTTY Configuration**:
     - Enter the **IP address** of your CentOS server.
     - Ensure **Port 22** is selected.
     - Click **Open**, then accept the security prompt.

4. **Login to the Server**:
   - Username: `root`
   - Password: `*****`
   - Assign a session name (e.g., `CentOS 9`).
