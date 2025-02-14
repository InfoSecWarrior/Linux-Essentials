#   ***CentOS Installation in VirtualBox***
## 📹 **Installation Video**
To watch the full installation video, click on the link below:  
### *[CentOS Installation in VirtualBox](https://www.youtube.com/watch?v=ZqyVrfW2c6g)*


---


Follow the steps below to successfully install CentOS in VirtualBox. This guide will walk you through each step with clear instructions.

---

### *Step 1: Download CentOS ISO*
1. Visit the [CentOS website](https://www.centos.org/download/).
2. Download the *ISO image* that corresponds to your system architecture (e.g., x86_64).
   - Choose the *Minimal ISO* for a lighter installation or the *DVD ISO* for a complete installation.

---

### *Step 2: Create a New Virtual Machine in VirtualBox*
1. *Open VirtualBox* and click on *New* to start creating a new VM.
2. Set the *Name* of your VM (e.g., "CentOS VM").
3. Choose *Linux* for the *Type* and *Red Hat (64-bit)* for the *Version*.
4. Set *Memory (RAM)* allocation: 2GB or more is recommended for optimal performance.
   - Example: 2048MB (2GB) or 4096MB (4GB) depending on your system’s capacity.

---

### *Step 3: Configure the Virtual Machine’s Storage*
1. *Go to the Storage tab* in VM settings.
2. Under *Controller: IDE, click **Empty*.
3. *Attach the CentOS ISO*:
   - Click the *disk icon* next to *Optical Drive* and select *Choose a disk file*.
   - Browse and select the *CentOS ISO* you downloaded in Step 1.

---

### *Step 4: Start the Virtual Machine*
1. *Click Start* to boot the VM from the attached CentOS ISO.
2. The CentOS installation screen should now appear. Select *Install CentOS* and press *Enter* to begin the installation process.

---

### *Step 5: Install CentOS*
1. *Language and Keyboard Layout*:
   - Select your desired *Language* and *Keyboard Layout*.
2. *Installation Destination*:
   - Select the hard disk where CentOS will be installed (usually the default one).
   - You can choose *Automatic Partitioning* for simplicity.
3. *Network Configuration*:
   - Set up your *Network* and ensure it’s *enabled* for internet access.
4. *User Configuration*:
   - Set a *root password* and create a *user account* with administrative privileges.
5. Once the installation completes, click *Reboot*.

---

### *Step 6: Post-Installation Setup*
1. *Initial Boot*:
   - After rebooting, log in using the credentials you created during the installation.
2. *Update CentOS*:
   - Open the *Terminal* and run the following command to update CentOS:
     
     sudo yum update -y
     
3. *Install Additional Software*:
   - Install any necessary software packages using yum or dnf (for newer CentOS versions).

---

### *Additional Tips*
- *Enable Network Adapter*:
   - If you don’t have internet access, ensure your *network settings* are configured correctly. Use *NAT* or *Bridged Adapter* to enable internet.
- *Install VirtualBox Guest Additions*:
   - For better integration (shared folders, enhanced graphics), install *VirtualBox Guest Additions* after logging into CentOS.
   - You can find the option to install it in *Devices > Insert Guest Additions CD image*.

---

## ⚡ *Congratulations!* 
You have successfully installed CentOS on VirtualBox! Enjoy exploring your new virtual machine and getting familiar with CentOS.

---
