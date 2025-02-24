# Network Configuration in Linux  
We will discuss tools or commands to manage network settings.

## Some important terms

- **enp0s3:** Ethernet interface (PCI-based naming)  
- **wlan0:** First Wi‑Fi interface  
- **lo:** Loopback (self‑communication)

## nmtui (NetworkManager Text User Interface)

`nmtui` is a curses-based TUI application for interacting with NetworkManager. It allows you to modify, create, delete, or activate network profiles as well as set the system hostname.

### Installation

- **RHEL/CentOS/Fedora:**

```
dnf install NetworkManager-tui
```

- **Debian/Ubuntu:**

```
apt install network-manager
```

### Main Options in nmtui

![image](https://github.com/user-attachments/assets/545329e0-b153-48cb-bf9d-bb7bc035870a)

### Modifying Connection Settings

![image](https://github.com/user-attachments/assets/c5bc344b-11db-4eec-9113-de2229d1ea49)

![image](https://github.com/user-attachments/assets/95573cf8-039d-4a49-96ed-5508c38a02d2)

When configuring a static IP address, change "IP Configuration" from Automatic to Manual. The available options typically include:

- **Ignore:** Disables the interface completely (no IP assigned).
- **Automatic:** Uses DHCP to automatically get IP, Gateway, and DNS.
- **Automatic (DHCP-Only):** Gets only the IP and Gateway from DHCP; DNS must be set manually.
- **Link-Local:** Assigns a self-generated IP (e.g., 169.254.x.x for IPv4, fe80::/10 for IPv6); no internet access.
- **Manual:** Requires manually setting IP, Gateway, and DNS (static IP setup).
- **Disable:** Turns off the interface completely (no network activity).

After making changes, restart the network by rebooting or using:

```
systemctl restart NetworkManager
```

## nmcli (NetworkManager Command Line Interface)

`nmcli` allows you to manage and configure network connections and works with NetworkManager. It provides commands to enable/disable connections, view network status, configure IP addresses, and manage Wi‑Fi, VPNs, and mobile broadband.

### Basic Commands

- **Check NetworkManager Status:**

```
nmcli general status
```

- **Check Device Status:**

```
nmcli device status
```

- **Show All Connections:**

```
nmcli connection show
```

- **Show Active Connections:**

```
nmcli connection show --active
```

- **Disable Networking (turns off all network interfaces managed by NetworkManager):**

```
nmcli networking off
```

- **Enable Networking:**

```
nmcli networking on
```

- **Bring a Specific Connection Up:**

```
nmcli connection up <connection_name>
```

- **Bring a Specific Connection Down:**

```
nmcli connection down <connection_name>
```

- **Show IP and DNS Information for a Device:**

```
nmcli device show enp0s3
```

- **Assign a Static IP to an Interface:**

```
nmcli connection modify enp0s3 ipv4.addresses 192.168.1.100/24 ipv4.gateway 192.168.1.1 ipv4.method manual
```

- **Set DNS Servers:**

```
nmcli connection modify enp0s3 ipv4.dns 8.8.8.8
```

- **Restart the Connection to Apply Changes:**

```
nmcli connection down enp0s3 && nmcli connection up enp0s3
```

## ip Command

The `ip` command is versatile. Note that short commands such as `ip a`, `ip add`, `ip addr` automatically map to `ip address`.

### Common Uses

- **Show All Interfaces (Active & Inactive):**

```
ip link show
```

- **Assign a Static IP Temporarily:**

```
ip addr add 192.168.1.100/24 dev enp0s3
```

- **Show Interfaces with Assigned IPs:**

```
ip addr show
```

- **Bring an Interface Down:**

```
ip link set enp0s3 down
```

- **Bring an Interface Up:**

```
ip link set enp0s3 up
```

- **Show Routing Table:**

```
ip route show
```

- **Add a Static Route to a Network:**

```
ip route add 192.168.2.0/24 via 192.168.1.1 dev enp0s3
```

- **Remove a Route:**

```
ip route del 192.168.1.0/24
```

- **Add a Default Gateway:**

```
ip route add default via 192.168.1.1 dev enp0s3
```

- **Display Routing Table Entries for a Specific Network Interface:**

```
ip route show dev enp0s3
```

- **Flush the Routing Table (Main Table):**

```
ip route flush table main
```

- **Flush Routes for a Specific Interface:**

```
ip route flush dev enp0s3
```

- **Flush All Routes (Including Local and Default Tables):**

```
ip route flush table all
```

## ifconfig (Deprecated)

The `ifconfig` command is deprecated in modern distributions and replaced by the `ip` command. However, it is still used in some older systems (or via the net-tools package).

### Common Uses

- **Show Active Interfaces Only:**

```
ifconfig
```

- **Show All Interfaces (Active & Inactive):**

```
ifconfig -a
```

- **Show Details of a Specific Interface:**

```
ifconfig enp0s3
```

- **Bring an Interface Up:**

```
ifconfig enp0s3 up
```

_or_

```
ifup enp0s3
```

- **Bring an Interface Down:**

```
ifconfig enp0s3 down
```

_or_

```
ifdown enp0s3
```

- **Assign a Static IP Address:**

```
ifconfig enp0s3 192.168.1.110
```

- **Assign a Static IP Address with Subnet:**

```
ifconfig enp0s3 192.168.1.100 netmask 255.255.255.0
```

_or_

```
ifconfig enp0s3 192.168.1.100/24
```

- **Restore the Original IP (by restarting NetworkManager):**

```
systemctl restart NetworkManager
```

_or_

```
ifconfig enp0s3 down && ifconfig enp0s3 up
```

- **Change the MAC Address (Spoofing):**

```
ifconfig enp0s3 hw ether 00:11:22:33:44:55
```

- **Set Maximum Transmission Unit (MTU Size):**

```
ifconfig enp0s3 mtu 1500
```

- **Enable Promiscuous Mode (to capture all packets on the network):**

```
ifconfig enp0s3 promisc
```

- **Disable Promiscuous Mode:**

```
ifconfig enp0s3 -promisc
```

- **Assign Multiple IP Addresses to a Single Interface (Alias/Secondary IPs):**

```
ifconfig enp0s3:1 192.168.1.101/24
```

- **Remove an Alias:**

```
ifconfig enp0s3:1 down
```

## route Command

The `route` command is used to view, add, delete, and modify network routing tables (works with both IPv4 and IPv6).

### Common Uses

- **Show Routing Table:**

```
route
```

- **Show Routing Table in Numeric Format:**

```
route -n
```

## hostname Command

The `hostname` command is used to display or set the system's hostname.

### Common Uses

- **Show Current Hostname:**

```
hostname
```

- **Show Fully Qualified Domain Name (FQDN):**

```
hostname -f
```

- **Show IP Addresses Assigned to Hostname:**

```
hostname -I
```

_or_

```
hostname -i
```

- **Change Hostname Temporarily (resets after reboot):**

```
hostname NEW_HOSTNAME
```

- **Change Hostname Permanently:**

```
hostnamectl set-hostname NEW_HOSTNAME
```

- **Show System Information (on systems supporting hostnamectl):**

```
hostnamectl status
```

## Viewing the Public IP Address

Several websites allow you to view your public IP:

### icanhazip.com  
  Show Public IP:

```
curl icanhazip.com
```

### ifconfig.me 
  Show Public IP:

```
curl ifconfig.me
```

  Show All Network Details:

```
curl ifconfig.me/all
```

  Show User Agent:

```
curl ifconfig.me/ua
```

### ipinfo.io  
  Show Public IP:

```
curl ipinfo.io/ip
```

  Show Public IP with Location Details:

```
curl ipinfo.io
```

## Manually Configuring Network Settings

### Viewing and Configuring DNS

- **View DNS Configuration:**

```
cat /etc/resolv.conf
```

*Note:* If managed by NetworkManager, changes may be overridden.

- **Temporary DNS Change:**

```
echo "nameserver 8.8.8.8" > /etc/resolv.conf
```

- **Permanent DNS Configuration:**

  - **Debian/Ubuntu (`/etc/network/interfaces`):**

    ```
    dns-nameservers 8.8.8.8 8.8.4.4
    ```

  - **RHEL/CentOS (in `/etc/NetworkManager/system-connections/XXXXX.nmconnection` file):**

    ```
    dns=8.8.8.8;8.8.4.4;
    ```

### Viewing and Modifying Hostname

- **View Hostname:**

```
cat /etc/hostname
```

### Checking Available Network Interfaces

```
cat /proc/net/dev
```

This command lists all network interfaces and their statistics, including packets received and transmitted.

### Configuring IP Address Using NetworkManager

Configuration can be done by editing the connection file in the NetworkManager directory. These files represent your network connections.

1. Navigate to the NetworkManager system connections directory:

```
cd /etc/NetworkManager/system-connections/
```

2. Open the connection file (for example, for enp0s3):

```
vim enp0s3.nmconnection
```

#### Static IP Configuration Examples

- **Debian/Ubuntu (`/etc/network/interfaces`):**

  ```
  auto enp0s3
  iface enp0s3 inet static
      address 192.168.1.34
      netmask 255.255.255.0
      gateway 192.168.1.1
      dns-nameservers 8.8.8.8 8.8.4.4
  ```

- **RHEL/CentOS**  
  - *Older versions:* `/etc/sysconfig/network-scripts/ifcfg-enp0s3`  
  - *Newer versions:* `/etc/NetworkManager/system-connections/`

  Example static configuration:

  ```
  [connection]
  id=enp0s3
  uuid=a32babc0-fbae-3089-b858-40d62bd6d445
  type=ethernet
  autoconnect-priority=-999
  interface-name=enp0s3
  timestamp=1739793171

  [ethernet]

  [ipv4]
  address1=192.168.1.34/24
  dns=8.8.8.8;8.8.4.4;
  gateway=192.168.1.1
  method=manual

  [ipv6]
  addr-gen-mode=eui64
  method=disabled

  [proxy]
  ```

#### Dynamic IP Configuration Example

```
[connection]
id=enp0s3
uuid=a32babc0-fbae-3089-b858-40d62bd6d445
type=ethernet
autoconnect-priority=-999
interface-name=enp0s3
timestamp=1739793171

[ethernet]

[ipv4]
method=auto

[ipv6]
addr-gen-mode=eui64
method=disabled

[proxy]
```

#### Assigning Multiple IPs to a Single Interface

```
[connection]
id=enp0s3
uuid=a32babc0-fbae-3089-b858-40d62bd6d445
type=ethernet
autoconnect-priority=-999
interface-name=enp0s3
timestamp=1739793171

[ethernet]

[ipv4]
address1=192.168.1.34/24
address2=192.168.1.35/24
address3=192.168.1.36/24
address4=192.168.1.37/24
dns=8.8.8.8;8.8.4.4;
gateway=192.168.1.1
method=manual

[ipv6]
addr-gen-mode=eui64
method=disabled

[proxy]
```

#### Possible Values for method in .nmconnection Files

| Value       | Function                                  | Use Case                     |
| ----------- | ----------------------------------------- | ---------------------------- |
| auto        | Uses DHCP                                 | Default (Dynamic IP)         |
| manual      | Static IP                                 | Servers, fixed IPs           |
| link-local  | Self-assigned (169.254.x.x or fe80::/10)    | When no DHCP is available    |
| shared      | Acts as NAT router                        | Internet sharing             |
| disabled    | No IP assignment                          | Bridging, VLAN-only setups   |

For IPv6, additional values include:

| Value      | Function                     | Use Case                |
| ---------- | ---------------------------- | ----------------------- |
| auto       | SLAAC/DHCPv6                 | Default IPv6 setting    |
| manual     | Static IPv6                  | Servers                 |
| dhcp       | DHCPv6 only                  | ISP configurations      |
| link-local | Self-assigned (fe80::/64)      | When no IPv6 network    |
| ignore     | Disables IPv6                | IPv4-only networks      |
