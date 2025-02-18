# 🖧 IFCONFIG/IP 

## 🌍 Ifconfig Command 

The `ifconfig` (interface configuration) command is used to configure network interfaces. It is now **deprecated** in most Linux distributions in favor of the `ip` command, but it is still available for legacy systems.

### 📌 Display Network Interfaces
```bash
ifconfig
```
🔍 Lists all active network interfaces, showing details such as **IP addresses, MAC addresses, and network status**.

#### 🔄 Display all interfaces, including inactive ones
```bash
ifconfig -a
```

### 📡 View a Specific Interface
🔍 Displays details for the `enp0s3` interface.
```bash
ifconfig enp0s3
```

### 🎯 Assign an IP Address
📌 Assign the IP address `192.168.1.40` to `enp0s3`.
```bash
ifconfig enp0s3 192.168.1.40
```
📌 Assign the IP address `192.168.1.35` with a `/24` subnet mask.
```bash
ifconfig enp0s3 192.168.1.35 netmask 255.255.255.0
```
📌 Assign the IP address `192.168.1.42` with a `/20` subnet mask.
```bash
ifconfig enp0s3 192.168.1.42/20
```

### 🔄 Restart the Network
```bash
systemctl restart network-online.target
```

### 🚀 Enable or Disable an Interface
❌ Disable the `enp0s3` interface.
```bash
ifconfig enp0s3 down
```
✅ Enable the `enp0s3` interface.
```bash
ifconfig enp0s3 up
```

### 🔗 Assign Multiple IP Addresses to One Interface
🆕 Create a virtual interface `enp0s3:1` with IP `192.168.1.42`.
```bash
ifconfig enp0s3:1 192.168.1.42
```
🆕 Create another virtual interface `enp0s3:2` with IP `192.168.1.43`.
```bash
ifconfig enp0s3:2 192.168.1.43
```

### 🚦 Disable and Enable Network Interfaces
❌ Disable the `enp0s3` interface.
```bash
ifdown enp0s3
```
✅ Enable the `enp0s3` interface.
```bash
ifup enp0s3
```

## 🔥 Using `ip` Command (Recommended)
Since `ifconfig` is **deprecated**, the `ip` command is the modern alternative! 🏆

### 📌 Display Network Interfaces
```bash
ip addr show
```

### 🎯 Assign an IP Address
📌 Assign `192.168.1.40` to `enp0s3`.
```bash
ip addr add 192.168.1.40/24 dev enp0s3
```

### 🚀 Disable/Enable an Interface
❌ Disable the `enp0s3` interface.
```bash
ip link set enp0s3 down
```
✅ Enable the `enp0s3` interface.
```bash
ip link set enp0s3 up
```

### 🛤️ Display the Routing Table
```bash
ip route
```

### 🛣️ Add a New Route
To manually add a route to a specific network:
```bash
ip route add 192.168.29.42 via 192.168.29.1 dev enp0s3
```

### 🗑️ Delete a Route
```bash
ip route del 192.168.29.42/24
```

### 🌎 Set a Default Gateway
```bash
ip route add default via 192.168.29.1 dev enp0s3
```

### 📡 Show Routes for a Specific Interface
```bash
ip route show dev enp0s3
```

### 🔄 Flush All Routes
```bash
ip route flush table main
```

## 🛠️ Network Diagnostics: `ping`, `traceroute`, and `tracepath`
Network diagnostic tools help test **connectivity** and analyze **network paths**. 🚀

### 📶 `ping` Command
The `ping` command sends ICMP Echo Request packets to a host to check connectivity.

#### 🔍 Send continuous pings to Google's public DNS server
```bash
ping 8.8.8.8
```

#### 🎯 Send only two packets
```bash
ping 8.8.8.8 -c 2
```

#### 🚀 Sending Large Packet Size
Sends a 65,504-byte packet to `192.168.1.1` (default is 56 bytes).
```bash
ping 192.168.1.1 -s 65500
```

## 🌍 `traceroute` Command
Traceroute maps the path packets take to reach a destination. 🗺️

### 🛠️ Installation
#### 🖥️ RHEL/CentOS
```bash
yum install traceroute
```
#### 💻 Debian/Ubuntu
```bash
apt install traceroute
```

### 📌 Show the Route Packets Take
```bash
traceroute 8.8.8.8
```

### 🎯 Trace the Route to `armourinfosec.io`
```bash
traceroute armourinfosec.io
```

## 🚀 `tracepath` Command
### 🛠️ Installation
#### 🖥️ RHEL/CentOS
```bash
yum install iputils iputils-tracepath
```
#### 💻 Debian/Ubuntu
```bash
apt install iputils-tracepath
```

### 📌 Trace the Path to `8.8.8.8`
```bash
tracepath 8.8.8.8
```

## 🔥 Common `ping` Options
| Option | Description |
|--------|-------------|
| `-i` | Interval ⏳ |
| `-c` | Packet Count 📦 |
| `-p` | Payload 🛠️ |
| `-s` | Packet Size 📏 |
| `-I` | Interface 🔌 |

## 📝 Editing Network Configuration Files
```bash
cd /etc/sysconfig/network-scripts

vim /etc/sysconfig/network-scripts/ifcfg-enp0s3
```

🎉 Happy Networking! 🚀
