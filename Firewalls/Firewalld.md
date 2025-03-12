Update Firewalld.md
# Firewalld Configuration and Management: A Practical Guide

Firewalld is a dynamic firewall management tool offering a user-friendly alternative to iptables. It uses a zone-based architecture for managing firewall rules. This guide provides a comprehensive reference for configuring and managing firewalld, including all necessary commands, best practices, and troubleshooting techniques.

---

## 1. Basic Firewalld Control Commands

- Check if firewalld is running:
  ```
  systemctl status firewalld
  ```
- Start firewalld:
  ```
  systemctl start firewalld
  ```
- Stop firewalld:
  ```
  systemctl stop firewalld
  ```
- Restart firewalld:
  ```
  systemctl restart firewalld
  ```
- Enable firewalld at startup:
  ```
  systemctl enable firewalld
  ```
- Disable firewalld at startup:
  ```
  systemctl disable firewalld
  ```
- Check firewalld state:
  ```
  firewall-cmd --state
  ```

---

## 2. Installation and Package Information

- Check if firewalld is installed:
  ```
  rpm -qa | grep firewalld
  ```
- Get detailed package information:
  ```
  rpm -qi firewalld
  ```
- Install firewalld (if not installed):
  ```
  yum install firewalld -y
  ```

---

## 3. Zones Management

Firewalld uses zones (e.g., public, internal, dmz, trusted, external, work) to apply rules based on trust levels. Changes with the --permanent flag persist across reboots; otherwise, they are temporary.

- List all available zones:
  ```
  firewall-cmd --get-zones
  ```
- Show active zones and interfaces:
  ```
  firewall-cmd --get-active-zones
  ```
- Get the default zone:
  ```
  firewall-cmd --get-default-zone
  ```
- Set a new default zone (permanent):
  ```
  firewall-cmd --set-default-zone=work --permanent
  firewall-cmd --reload
  ```
- Assign an interface to a zone (permanent):
  ```
  firewall-cmd --zone=home --change-interface=eth0 --permanent
  firewall-cmd --reload
  ```
- Remove an interface from a zone (permanent):
  ```
  firewall-cmd --zone=home --remove-interface=eth0 --permanent
  firewall-cmd --reload
  ```
- List all rules in a zone:
  ```
  firewall-cmd --zone=public --list-all
  ```

---

## 4. Managing Services

- List all available services:
  ```
  firewall-cmd --get-services
  ```
- List allowed services in a zone:
  ```
  firewall-cmd --zone=public --list-services
  ```
- Allow a service in a zone (permanent):
  ```
  firewall-cmd --zone=public --add-service=http --permanent
  firewall-cmd --reload
  ```
- Remove a service from a zone (permanent):
  ```
  firewall-cmd --zone=public --remove-service=http --permanent
  firewall-cmd --reload
  ```

---

## 5. Managing Ports

- Open a specific port (permanent):
  ```
  firewall-cmd --zone=public --add-port=8080/tcp --permanent
  firewall-cmd --reload
  ```
- Close a specific port (permanent):
  ```
  firewall-cmd --zone=public --remove-port=8080/tcp --permanent
  firewall-cmd --reload
  ```

---

## 6. Managing Rich Rules (Advanced Filtering)

Rich rules allow advanced filtering beyond simple port or service rules.

- Add a rich rule (block an IP permanently):
  ```
  firewall-cmd --zone=public --add-rich-rule='rule family="ipv4" source address="192.168.1.100" reject' --permanent
  firewall-cmd --reload
  ```
- Allow a specific IP (permanent):
  ```
  firewall-cmd --zone=public --add-rich-rule='rule family="ipv4" source address="192.168.1.100" accept' --permanent
  firewall-cmd --reload
  ```
- List all rich rules:
  ```
  firewall-cmd --list-rich-rules
  ```
- Get a specific rich rule:
  ```
  firewall-cmd --get-rich-rule=<rule_number>
  ```
- Remove a rich rule (permanent):
  ```
  firewall-cmd --zone=public --remove-rich-rule='rule family="ipv4" source address="192.168.1.100" reject' --permanent
  firewall-cmd --reload
  ```

---

## 7. ICMP (Ping) Filtering

- List blocked ICMP types:
  ```
  firewall-cmd --zone=public --list-icmp-blocks
  ```
- Block ICMP echo requests (ping) permanently:
  ```
  firewall-cmd --zone=public --add-icmp-block=echo-request --permanent
  firewall-cmd --reload
  ```
- Remove the ICMP block permanently:
  ```
  firewall-cmd --zone=public --remove-icmp-block=echo-request --permanent
  firewall-cmd --reload
  ```
- Block other ICMP types (replace `<icmp_type>` with desired type):
  ```
  firewall-cmd --zone=public --add-icmp-block=<icmp_type> --permanent
  firewall-cmd --reload
  ```

---

## 8. Masquerading and Forwarding (NAT & Routing)

- Enable IP masquerading (permanent):
  ```
  firewall-cmd --zone=public --add-masquerade --permanent
  firewall-cmd --reload
  ```
- Disable IP masquerading (permanent):
  ```
  firewall-cmd --zone=public --remove-masquerade --permanent
  firewall-cmd --reload
  ```
- Set up port forwarding (permanent):
  ```
  firewall-cmd --zone=public --add-forward-port=port=8080:proto=tcp:toport=80 --permanent
  firewall-cmd --reload
  ```
- Configure masquerading with source specification (permanent):
  ```
  firewall-cmd --zone=public --add-masquerade --permanent --source=<source_ip>
  firewall-cmd --reload
  ```
- Configure masquerading with source subnet specification (permanent):
  ```
  firewall-cmd --zone=public --add-masquerade --permanent --source=<source_subnet>/<mask>
  firewall-cmd --reload
  ```

---

## 9. Saving and Restoring Rules

- Save runtime changes permanently:
  ```
  firewall-cmd --runtime-to-permanent
  ```
- Reset firewalld to defaults:
  ```
  firewall-cmd --reset-default-zone
  firewall-cmd --reload
  firewall-cmd --complete-reload
  ```

---

## 10. Debugging and Logs

- Check logs for dropped packets:
  ```
  journalctl -xe | grep firewalld
  ```
- Enable logging for denied packets:
  ```
  firewall-cmd --set-log-denied=all
  ```
- View active connections:
  ```
  firewall-cmd --get-active-connections
  ```

---

## 11. Direct Rules (iptables/nftables)

Direct rules bypass firewalld's normal filtering and add rules directly to iptables or nftables.

- Add a direct rule (permanent):
  ```
  firewall-cmd --direct --add-rule ipv4 filter INPUT 0 -p tcp --dport 3306 -j ACCEPT --permanent
  firewall-cmd --reload
  ```
- List direct rules:
  ```
  firewall-cmd --direct --get-all-rules
  ```
- Remove a direct rule (permanent):
  ```
  firewall-cmd --direct --remove-rule ipv4 filter INPUT 0 -p tcp --dport 3306 -j ACCEPT --permanent
  firewall-cmd --reload
  ```

---

## 12. Default Zone

The default zone is applied to new network interfaces unless specified otherwise; if an interface is in a different zone, that zone’s rules apply. To change the default zone permanently:
```
firewall-cmd --set-default-zone=<zone> --permanent
firewall-cmd --reload
```

---

## 13. Disabling Firewalld and Using iptables (If Needed)

If you wish to disable firewalld and revert to iptables:
```
systemctl stop firewalld
systemctl disable firewalld
yum install iptables-services -y
systemctl enable iptables
systemctl start iptables
iptables -L -v -n
```

---

## Best Practices

- Start with minimal rules; add only what is necessary.
- Regularly review and update firewall rules.
- Use zones appropriately to segregate network trust.
- Use the `--permanent` flag to make changes persistent, and always reload firewalld after changes.
- Back up your firewall configuration before making significant modifications.
- Test changes thoroughly to avoid locking yourself out.
- Use `firewall-cmd --complete-reload` when a standard reload is not sufficient.

---

## Troubleshooting

- Check logs to diagnose issues:
  ```
  journalctl -xe | grep firewalld
  ```
- Verify network connectivity and review active connections:
  ```
  firewall-cmd --get-active-connections
  ```
- Check for conflicting rules with:
  ```
  firewall-cmd --list-all
  ```
- If you encounter persistence issues, use direct rules with caution and verify with:
  ```
  firewall-cmd --direct --get-all-rules
  ```
