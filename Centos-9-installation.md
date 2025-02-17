# CentOS 9 Installation (GUI)

[Download CentOS 9 Stream ISO](https://mirror.stream.centos.org/9-stream/BaseOS/x86_64/iso/CentOS-Stream-9-20250210.0-x86_64-dvd1.iso)

---

### VirtualBox Setup

- Open VirtualBox and click **New**.  
  ![image](https://github.com/user-attachments/assets/5eabe75d-723f-4d79-8d4a-3bb3bbc09575)

- Set the name to **CentOS 9**, type to **Linux**, and version to **Red Hat (64-bit)**.  
  ![image](https://github.com/user-attachments/assets/9a484a55-7809-4108-92dd-09efb4368942)

- Allocate **4096 MB** RAM (According to requirement).  
  2 core CPU  
  ![image](https://github.com/user-attachments/assets/b119c7f5-3975-43f5-aa2e-f9d5495a5f79)

- Create a virtual disk:  
  - Select **VDI (Virtual Disk Image)**  
  - Choose **Dynamically allocated**  
  - Set **file location and size to 40 GB** (According to requirement)  
  ![image](https://github.com/user-attachments/assets/ac6a9800-7137-4b87-b917-f46799772583)

- Start the virtual machine, select the CentOS 9 ISO, and click **Start**.

---

## Installation

- Choose **Install CentOS 9**.  
  ![image](https://github.com/user-attachments/assets/55d6bd50-58c9-47a0-8d48-f177eede72b5)

- Select **English > English (India) > Continue**.  
  ![image](https://github.com/user-attachments/assets/a340f715-5e09-4866-8e12-ea1ea581e0f8)

- Configure settings:  
  - **Date & Time**: Asia/Kolkata > Done  
  - **Keyboard Layout**: English (India, with rupee) > Add English (US) > Done  
  - **Language Support**: English (India) > Done  
  ![image](https://github.com/user-attachments/assets/1eb792fe-0f9c-425c-bc30-225f958edb16)

- **Installation Source**: Verify ISO > Done  
  - Auto-Detect Media  
    Automatically detects bootable installation media (DVD, USB, ISO)  
  - Network Sources  
    Closest Mirror: Selects the fastest CentOS mirror  
    NFS: Installs from a shared network directory  
    HTTP/HTTPS: Fetches packages from online repositories via secure links  
    FTP: Downloads from an FTP server  
  - Custom Repositories  
    Allows specifying offline or private repositories for custom setups  
  - Manual Options  
    Change source, verify media, or fallback to network if no valid media is found  
  
  [for now select auto detect media]  
  ![image](https://github.com/user-attachments/assets/38a0a1d9-2f21-4122-8ca6-de09b11f8b70)

- **Software Selection**: Select **Server with GUI**  
  - Base Environment Options:  
    These define the primary purpose of the system.  
    -  Server with GUI: Installs a server environment with a graphical user interface (GNOME)  
    -  Server: Provides a CLI-based server setup with essential services  
    -  Minimal Install: A lightweight installation with the bare minimum required to run CentOS  
    -  Workstation: For desktop use with a GUI and development tools  
    -  Custom Operating System: A fully customized setup to meet specific requirements  
    -  Virtualization Host: Configured to host and manage virtual machines  

  [for now select Server With GUI]

  - Additional Software for Selected Environment:  
    -  Each base environment includes optional add-ons to enhance functionality  
    -  Examples:  
      -  Development Tools: Compiler and libraries  
      -  Web Server: Apache, Nginx  
      -  File Server: Samba, NFS utilities  
      -  System Administration Tools: Diagnostic and monitoring tools  
  
  [for now don't select anything]  
  ![image](https://github.com/user-attachments/assets/6c379981-3de0-4d08-b73a-50bb9757bd5b)

- Installation Destination  
  ![image](https://github.com/user-attachments/assets/614090ef-5e8e-4007-ac3f-eb6a8039b405)

  - **Custom partitioning** > Done  
  - Create partitions:  
    - `/boot` - **1024 MiB**, **ext4**, Standard  
    - `swap` - **4096 MiB**, Standard  
    - `/` - **XFS file system**, Standard  
  - Click **Done > Accept Changes**

  Selecting the Installation Device  
  When you reach the Installation Destination screen:  
  - Local Standard Disks:  
    -  Displays the available storage devices (e.g., HDD, SSD)  
    -  Select the disk where CentOS will be installed by clicking the checkbox next to it  
  - Specialized Storage Devices (optional):  
    -  Used for network-attached storage (NAS) or advanced configurations like iSCSI

  Storage Configuration Options  
  After selecting a device, choose a storage configuration mode:  
  a) Automatic Partitioning  
    - The installer automatically creates default partitions:  
      -  /boot (for bootloader files)  
      -  swap (used for virtual memory)  
      -  / (root directory for the OS)  
    - Suitable for beginners or general-purpose installations
  
  b) Custom Partitioning  
    - Provides full control over partitioning, allowing manual definition of partitions and their sizes  
    - Steps:  
      1. Partition Scheme:  
         § Standard Partition: Traditional partitioning (no LVM)  
         § LVM (Logical Volume Manager): Allows resizing, snapshots  
         § LVM Thin Provisioning: Dynamically allocates storage  
      2. Create Partitions:  
         § Recommended scheme:  
           -  /boot → 1 GB (Standard Partition)  
           -  swap → 4 GB (Standard Partition)  
           -  / → Remaining space (Standard Partition)  
           -  File System: ext4 or XFS  
      3. Encrypt My Data:  
         § Option to encrypt partitions for security  
      4. Additional Space:  
         § Reclaim space from existing partitions if needed  
  ![image](https://github.com/user-attachments/assets/09c94e55-bb73-4464-81bf-13c65872565d)

  Partition Details  
  /boot Partition  
  - Purpose: Stores bootloader files  

  swap Partition  
  - Purpose: Virtual memory when physical RAM is fully used  

  / (root) Partition  
  - Purpose: Main directory containing the OS and user files  

- **KDUMP**: No changes  
  Purpose: Configure KDUMP for kernel crash dumping  
  Features:  
  Enable/disable KDUMP  
  Specify memory allocation for crash dumps  
  [for now Keep it Enabled]

- **Network & Hostname**:  
  - Enable **enp0s3**  
  - Configure IPv4 manually, disable IPv6, save settings  
  - Set hostname to **Demo**  
  ![image](https://github.com/user-attachments/assets/52d61353-65f3-4fc3-b0e8-829220a011f5)

- **Security Policy**: No changes  
  Purpose: Apply predefined security policies to the system  
  Features:  
  Choose profiles like CIS or DISA STIG  
  Integrate system-wide security hardening  
  [for now Keep it disabled]

- 9. Set **root password** and create a user:  
  - Full name: `<demouser>`  
  - Username: `<demouser>`  
  - Tick **Make this user administrator**  
  ![image](https://github.com/user-attachments/assets/3daf92b9-b83a-492e-9647-a6208b0880aa)

  Lock the Root Account [for now Keep it disabled]  
  - Purpose:  
    -  Prevents the root account from being used directly for login  
    -  The root account remains available but can only be accessed through sudo

  Allow Root SSH Login with Password [for now Keep it enabled]  
  - Purpose:  
    -  Enables the root user to log in remotely via SSH using a password

  - User Creation  
    Create a non-root user for daily use  
  ![image](https://github.com/user-attachments/assets/7e7d9169-e363-48c6-85bd-40460a6678f5)

[click begin installation]

![image](https://github.com/user-attachments/assets/adeb0d27-feb0-490b-8265-fb215496e983)
