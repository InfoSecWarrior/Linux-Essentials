
# 🐧 **Linux Shells & Command-Line Enhancements** 🚀  

A **shell** in Linux is a **command-line interface (CLI)** that allows users to interact with the **operating system**. It acts as an **intermediary between the user and the kernel**, executing commands, running scripts, and automating tasks. There are multiple **types of shells**, each with unique features and capabilities.

Linux में शेल एक command-line interface है, जो users को operating system से interact करने का मौका देता है। यह user और kernel के बीच एक intermediary के रूप में काम करता है, जिससे commands execute हो सकती हैं, scripting की जा सकती है, और automation की प्रक्रिया handle की जा सकती है। Linux में कई types के shells होते हैं, जिनके अलग-अलग features और capabilities होती हैं।

---

## 🔄 **1. Common Shells in Linux**  

| 🐚 **Shell** | 🌟 **Purpose** | ⚡ **Key Features** |
|-------------|--------------|------------------|
| **sh (Bourne Shell)** | Basic command execution & scripting | Supports loops, conditionals, & redirection |
| **Bash (Bourne Again Shell)** | Default shell in most Linux distros | Command history, tab completion, scripting |
| **Ksh (Korn Shell)** | Combines features of `sh` and `csh` | High-performance scripting |
| **Tcsh (TENEX C Shell)** | Enhanced `C Shell (csh)` | Command-line editing & spelling correction |
| **Fish (Friendly Interactive Shell)** | User-friendly interactive shell | Syntax highlighting, autosuggestions |
| **Zsh (Z Shell)** | Highly customizable shell | Shared history, spell-checking, themes |
| **Dash (Debian Almquist Shell)** | Lightweight & fast shell | Used for scripting in `/bin/sh` |

---

## 📂 **2. Checking Available Shells (`/etc/shells`)**
To see the shells available on your system:

#### **🔹 Command:**
```bash
cat /etc/shells
```

#### **📌 Output Example:**
```bash
/bin/sh
/bin/bash
/usr/bin/sh
/usr/bin/bash
```
✅ Lists all installed **shells** that can be used by users.

---

## 🏠 **3. Navigating Linux File System**
### 📌 **Change Directory to Root (`/`)**
```bash
cd /
```
🔹 Switches the current directory to the **root directory (`/`)**, which is the top-level of the Linux file system.

---

## 📁 **4. Listing Files in Root Directory (`ls -lh`)**
### 📌 **List Root Directory in Human-Readable Format**
```bash
ls -lh
```
#### **📌 Output Example:**
```bash
total 88K
drwxr-xr-x  2 root root 4.0K bin
drwxr-xr-x  3 root root 4.0K etc
drwxr-xr-x  2 root root 4.0K home
lrwxrwxrwx  1 root root   33 lib -> /usr/lib
drwxr-xr-x  7 root root 4.0K usr
```
✅ Displays **file sizes, permissions, owners, and modification times**.

---

## 🔄 **5. Switching Shells & Checking Active Shell**
### 📌 **Check Current Shell**
```bash
echo $SHELL
```
#### **📌 Output Example:**
```bash
/bin/bash
```
✅ Confirms that **Bash** is the currently active shell.

### 📌 **Switch to `sh` Shell**
```bash
sh
```
#### **📌 Output Example:**
```bash
sh-5.1#
```
✅ Now running inside **`sh` shell**.

### 📌 **Check Shell Again**
```bash
echo $SHELL
```
#### **📌 Output Example:**
```bash
/bin/bash
```
✅ The `$SHELL` variable **still shows Bash**, indicating that we only changed the **interactive shell**, not the default shell.

---

## 📦 **6. Installing & Managing Shell Packages with YUM**
### 📌 **Install All Bash-Related Packages**
```bash
yum install bash*
```
✅ Installs **all packages** related to Bash.

### 📌 **Search for Bash Packages**
```bash
yum search bash
```
✅ Lists **all available Bash-related packages**.

### 📌 **Install Bash Color Prompt**
```bash
yum install bash-color-prompt.noarch
```
✅ Adds **color support** to the Bash prompt.

---

## 🎨 **7. Installing & Using `grc` (Generic Colourizer)**
📌 **`grc` (Generic Colourizer) is a tool that enhances terminal output with colors**.

### 📌 **Download `grc` from GitHub**
```bash
wget https://github.com/garabik/grc/archive/refs/tags/v1.13.tar.gz
```
✅ Downloads `grc` **version 1.13**.

### 📌 **Move `grc` to `/opt/` Directory**
```bash
mv -v grc-1.13 /opt/
```
✅ Moves **grc package** to `/opt/`.

### 📌 **List Files in `/opt/grc-1.13/`**
```bash
cd /opt/grc-1.13/
ls -lh
```
✅ Displays **grc files**.

### 📌 **Use `grc` for Colorized Command Output**
```bash
grc ping 8.8.8.8
```
✅ Runs the `ping` command with **color-enhanced output**.

---

## ⚡ **8. Installing & Using Zsh**
### 📌 **Check Installed Zsh Version**
```bash
zsh --version
```
#### **📌 Output Example:**
```bash
zsh 5.8 (x86_64-redhat-linux-gnu)
```
✅ Displays **installed Zsh version**.

### 📌 **Find Zsh Path**
```bash
which zsh
```
#### **📌 Output Example:**
```bash
/usr/bin/zsh
```
✅ Displays **Zsh executable path**.

### 📌 **Edit Zsh Configuration (`.zshrc`)**
```bash
nano /root/.zshrc
```
✅ Opens **Zsh settings** for customization.

### 📌 **Change Default Shell to Zsh**
```bash
chsh -s $(which zsh)
```
✅ Sets **Zsh as the default shell** for the user.

---

## 🎯 **9. Summary of Key Commands**
| 🛠️ **Command** | 📌 **Description** |
|---------------|----------------|
| `cat /etc/shells` | Lists available shells |
| `cd /` | Navigates to root directory |
| `ls -lh` | Lists files with detailed info |
| `echo $SHELL` | Shows current shell |
| `sh` | Switches to `sh` shell |
| `yum install bash*` | Installs Bash-related packages |
| `yum search bash` | Searches for Bash packages |
| `wget [URL]` | Downloads files from the internet |
| `grc ping 8.8.8.8` | Runs `ping` with colorized output |
| `zsh --version` | Shows installed Zsh version |
| `which zsh` | Finds Zsh path |
| `nano /root/.zshrc` | Edits Zsh configuration |
| `chsh -s $(which zsh)` | Changes default shell to Zsh |

---
