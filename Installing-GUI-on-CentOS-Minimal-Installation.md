# Installing GUI on CentOS Minimal Installation

CentOS Minimal provides a minimal set of packages, which is ideal for servers without a graphical user interface (GUI). If you need a GUI on your CentOS minimal system, you can install it manually. Below are the necessary steps to install the GNOME Desktop Environment and other useful packages.

---

## Installing GNOME Desktop Environment

### Step 1: Check Available Package Groups

First, list all available package groups to verify that the GNOME Desktop group is available.

```
yum grouplist
```

- This command displays all available package groups, including GUI-related ones.
- The `"GNOME Desktop Environment"` group is provided by the `baseos` and `appstream` repositories.

### Step 2: Install GNOME Desktop Environment

Install the GNOME Desktop Environment group packages.

```
yum group install "GNOME Desktop Environment"
```

- This command installs all necessary packages for GNOME.
- Ensure that both `baseos` and `appstream` repositories are enabled.

---

## Configuring the System to Boot into GUI

### Step 1: Check Current Default Target

Verify the current default system target (startup mode).

```
systemctl get-default
```

- **Possible Outputs**:
  - `multi-user.target` — Boots into command-line mode (no GUI).
  - `graphical.target` — Boots into GUI mode.

### Step 2: Set Default Target to Graphical

Set the system to boot into the graphical interface by default.

```
systemctl set-default graphical.target
```

- Sets `graphical.target` (GUI mode) as the default startup mode.
- After reboot, the system will start with a graphical login screen.

### Step 3: Start GUI Immediately Without Rebooting

To switch to GUI mode without rebooting:

```
systemctl isolate graphical.target
```

- Immediately starts the GUI.
- **Note**: This is temporary; after reboot, the system will use the default target set previously.

---

## Starting GUI Manually

If the default target is not set to graphical and you wish to start the GUI manually:

```
startx
```

- Initializes an X session and starts the default window manager or desktop environment.
- Useful if you prefer to boot into command-line mode but occasionally need a GUI.

---

## Reboot the System

After making changes, it's recommended to reboot the system to apply all settings.

```
reboot
```

---

## Alternative Desktop Environments

You can install other desktop environments based on your preferences.

### Install KDE Plasma Workspaces

```
yum group install "KDE Plasma Workspaces"
```
---

## Installing Additional Packages on Minimal Installation

Enhance your minimal CentOS installation by installing additional useful packages.

### Install Development Tools

```
yum group install "Development Tools"
```

- Installs essential development tools like compilers and debuggers.

### Install System Tools

```
yum group install "System Tools"
```

- Installs various system utilities for system administration.

### Install Shells

#### Install Bash Shell

```
yum install bash*
```

#### Install Z Shell (zsh)

```
yum install zsh*
```

### Install Vim Editor

```
yum install vim
```

### Install Network Tools

```
yum install net-tools
```

- Provides traditional networking tools like `ifconfig` and `netstat`.

