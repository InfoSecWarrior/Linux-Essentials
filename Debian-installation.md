# Step-by-Step Guide: Installing Debian on VirtualBox

## 1. Download Required Files ✅

### Download Debian ISO
- Visit the official Debian website: [Debian Download](https://www.debian.org/download)

## 2. Create a New Virtual Machine (VM)

1. Open VirtualBox and click **"New"**.
2. Enter the following details:
   - **Name**: Debian
   - **Type**: Linux
   - **Version**: Debian (64-bit)
3. Click **Next**.

## 3. Configure Virtual Machine Settings

### 🖥️ Allocate RAM
- **Recommended**: At least **2048 MB (2 GB)**, or **4096 MB (4 GB)** for better performance.

### 💽 Create Virtual Hard Disk
1. Select **"Create a virtual hard disk now"** → Click **Create**.
2. Choose **"VDI (VirtualBox Disk Image)"** → Click **Next**.
3. **Storage type**:
   - Choose **"Dynamically allocated"**.
4. **Set disk size**:
   - **Recommended**: 40 GB or more.
5. Click **Create**.

## 4. Load Debian ISO in VirtualBox

1. Select your **Debian VM** in VirtualBox.
2. Click **Settings** → **Storage**.
3. Under **Controller: IDE**, click **Empty**.
4. Click **Choose a disk** → Select the **Debian ISO** file you downloaded.
5. Click **OK**.

## 5. Start Debian Installation

1. Click **Start** to boot the VM.
2. Choose **"Graphical Install"** or **"Install"**.

## 6. Select Language, Location, and Keyboard

- **Language**: Choose your preferred language.
- **Location**: Select your country.
- **Keyboard**: Choose the layout (default: US).

## 7. Configure Network

- If using **bridged networking** or **NAT**, it will auto-detect.
- If using **Wi-Fi**, connect and enter your password.
- Set a **hostname** (e.g., `debian-vm`).
- Leave the **domain name empty** (or set one if needed).

## 8. Create User and Password

- **Set Root Password** .
- **Create a new user**:
  - Enter **full name**, **username**, and **password**.

## 9. Partition the Disk (Manual Method)

1. Select **"Manual"** partitioning.
2. Select the **virtual hard disk**.
3. Delete any existing partitions (if any).
4. **Create the following partitions manually**:

   **(If disk size is 40 GB)**

   🔹 **Boot Partition (`/boot`)**
   - Size: **4 GB**
   - Type: **Primary**
   - Filesystem: **ext4**
   - Mount point: **/boot**

   🔹 **Swap Partition**
   - Size: **2 GB** (or equal to RAM)
   - Type: **Logical**
   - Use as: **Swap area**

   🔹 **Root Partition (`/`)**
   - Size: **Remaining size**
   - Type: **Primary**
   - Filesystem: **ext4**
   - Mount point: **/**

## 10. Install the Base System

- Wait while Debian installs the base system.

## 11. Select Software

1. Select a **desktop environment**:
   - **GNOME** (default), KDE, XFCE, LXDE, Cinnamon, etc.
2. Select **"Standard system utilities"**.
3. Choose **"SSH Server"** if you want remote access.
4. Click **Continue** to install.

## 12. Install GRUB Bootloader

- Select **Yes** to install **GRUB**.

## 13. Finish Installation & Reboot



---

  # 🎉 **Debian is now installed on VirtualBox!**
