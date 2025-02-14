## CentOS 9 Installation (Minimal)

[Download CentOS 9 Minimal ISO](https://mirror.stream.centos.org/9-stream/BaseOS/x86_64/iso/CentOS-Stream-9-20250210.0-x86_64-boot.iso)

### VirtualBox Setup

1. Open VirtualBox and click **New**.
2. Set the name to **centos-mini**, type to **Linux**, and version to **Red Hat (64-bit)**.
3. Allocate **1024 MB** RAM (According to requirement).
4. Create a virtual disk:
   - Select **VDI (Virtual Disk Image)**.
   - Choose **Dynamically allocated**.
   - Set **file location and size to 40 GB** (According to requirement).
5. Start the virtual machine, select the CentOS 9 ISO, and click **Start**.

---

## Installation

1. Choose **Install CentOS 9**.
2. Select **English > English (India) > Continue**.
3. Configure settings:
   - **Date & Time**: Asia/Kolkata > Done.
   - **Keyboard Layout**: English (India, with rupee) > Add English (US) > Done.
   - **Language Support**: English (India) > Done.
   - **Installation Source**: Verify ISO > Done.
   - **Software Selection**: Select **Minimal Install**.
4. Configure partitioning:
   - **Custom partitioning** > Done.
   - Choose **Standard Partition**.
   - Click **"Click here to create them automatically"** > Done.
   - Accept Changes.
5. **KDUMP**: No changes.
6. **Network & Hostname**:
   - Enable **enp0s3**.
   - Configure IPv4 manually, disable IPv6, save settings.
   - Set hostname to **centos**.
7. **Security Policy**: No changes.
8. Click **Begin Installation**.
9. Set **root password** and create a user:
   - Full name: `<demouser>`.
   - Username: `<demouser>`.
   - Tick **Make this user administrator**.
10. Click **Done > Done**, then **Reboot**.

---

## Configuration

```bash
nmtui
```

```bash
ip add
```

```bash
ip a
```

```bash
yum repolist all
```

```bash
yum search epel
```

```bash
yum install epel-release.noarch
```

```bash
yum repolist all
```

### Optional Repositories

```bash
rpm -ivh https://rpms.remirepo.net/enterprise/remi-release-7.rpm
```

```bash
rpm -ivh https://mirrors.ustc.edu.cn/rpmfusion/free/el/rpmfusion-free-release-7.noarch.rpm
```

```bash
rpm -ivh https://www.elrepo.org/elrepo-release-7.el7.elrepo.noarch.rpm
```

```bash
rpm -ivh https://repo.ius.io/ius-release-el7.rpm
```

```bash
yum repolist all
```

```bash
yum search bash
```

```bash
yum install bash-completion.noarch
```

```bash
yum install bash*
```

```bash
yum install vim
```

```bash
yum install net-tools
```

```bash
reboot
```

---

## Group Installations

```bash
yum groups list
```

```bash
yum grouplist
```

```bash
yum groups info "Development and Creative Workstation"
```

```bash
yum groups summary "Development and Creative Workstation"
```

```bash
yum groups install "Development and Creative Workstation"
```

```bash
yum groups remove "Development and Creative Workstation"
```

```bash
yum groups install "Server with GUI"
```

```bash
reboot
```

---

## GUI Setup

```bash
startx
```

```bash
systemctl get-default
```

```bash
systemctl set-default graphical.target
```

```bash
systemctl isolate graphical.target
```

```bash
reboot
```

---

## Additional Server with GUI Commands

```bash
nmtui
```

```bash
yum search epel
```

```bash
yum install epel-release.noarch
```

```bash
rpm -ivh https://rpms.remirepo.net/enterprise/remi-release-7.rpm
```

```bash
rpm -ivh https://mirrors.ustc.edu.cn/rpmfusion/free/el/rpmfusion-free-release-7.noarch.rpm
```

```bash
rpm -ivh https://www.elrepo.org/elrepo-release-7.el7.elrepo.noarch.rpm
```

```bash
rpm -ivh https://repo.ius.io/ius-release-el7.rpm
```

```bash
yum repolist all
```

```bash
yum search bash
```

```bash
yum install bash*
```

```bash
yum install vim
```

```bash
yum install net-tools
```

```bash
yum groups install "MATE Desktop"
```

```bash
yum groups install "Server with GUI"
```

```bash
reboot
```

```bash
startx
```

```bash
systemctl get-default
```

```bash
systemctl set-default graphical.target
```

```bash
systemctl isolate graphical.target
```

```bash
reboot
```
