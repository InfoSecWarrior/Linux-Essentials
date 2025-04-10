## Go Configuration (Manual Installation)

### Step 1: Remove Existing Go Version (if installed via APT)
```bash
sudo apt remove golang-go
```

### Step 2: Download and Install Go
```bash
cd /home/nandlal/Downloads/
wget https://go.dev/dl/go1.23.4.linux-amd64.tar.gz
sudo rm -rf /usr/local/go
sudo tar -C /usr/local -xzf go1.23.4.linux-amd64.tar.gz
```

### Step 3: Verify Installation
```bash
ls /usr/local/go
/usr/local/go/bin/go version
```

### Step 4: Set Go Environment Variables

#### For ZSH users (`.zshrc`)
```bash
echo "export PATH=\$PATH:/usr/local/go/bin:\$HOME/go/bin" >> ~/.zshrc
echo "export GOROOT=/usr/local/go" >> ~/.zshrc
```

#### For Bash users (`.bashrc`)
```bash
echo "export PATH=\$PATH:/usr/local/go/bin:\$HOME/go/bin" >> ~/.bashrc
echo "export GOROOT=/usr/local/go" >> ~/.bashrc
```

> Repeat above exports for both `root` and `nandlal` users

### Step 5: Reload Shell
```bash
source ~/.zshrc   # if using zsh
source ~/.bashrc  # if using bash
```

## Install Go Tools Script (After Configuring Go)

### Step 1: Download the Go Tools Installer
```bash
cd /opt
sudo wget https://raw.githubusercontent.com/InfoSecWarrior/Offensive-Pentesting-Scripts/main/Gotools-Install/gotools-install.sh
sudo chmod +x gotools-install.sh
sudo ./gotools-install.sh
```

### Step 2: Verify Installed Tools
```bash
cd /usr/local/bin
ls -lh
```

## Python Configuration

### Step 1: Check Existing Versions
```bash
python -V
python2.7 -V
pip -V
pip2.7 -V
```

### Step 2: Install pip for Python 2.7
```bash
cd /home/nandlal/Downloads/
wget https://bootstrap.pypa.io/pip/2.7/get-pip.py -O get-pip.py
python2.7 get-pip.py
pip2.7 -V
```

### Step 3: Install pip for Default Python
```bash
wget https://bootstrap.pypa.io/pip/get-pip.py -O get-pip.py
python get-pip.py
```

### Step 4: Install pip and Python packages
```bash
pip install beautifulsoup4
pip3 install beautifulsoup4
```

### Step 5: Install Full Python3 and venv Support
```bash
sudo apt install python3.13-venv
sudo apt install python3-full
```

### Step 6: Create Python Virtual Environment
```bash
mkdir /opt/python-environment
python3 -m venv /opt/python-environment
/opt/python-environment/bin/python get-pip.py
```

### Step 7: Configure System to Use Environment pip
```bash
sudo rm -f /usr/local/bin/pip
sudo ln -s /opt/python-environment/bin/pip /usr/local/bin/pip
```

### Step 8: Add Python venv to PATH

#### For ZSH users
```bash
echo "export PATH=\$PATH:/opt/python-environment/bin" >> ~/.zshrc
```

#### For Bash users
```bash
echo "export PATH=\$PATH:/opt/python-environment/bin" >> ~/.bashrc
```

> Repeat for both `root` and `nandlal` users

## Final Checks

Run these commands to confirm successful setup:
```bash
# Python and pip
python -V
python2.7 -V
pip -V
pip2.7 -V
pip3 -V

# Check pip path
which pip
which pip2.7
which pip3
```

