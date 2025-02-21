# Memory Management in Linux

Memory management is crucial for monitoring system performance and troubleshooting issues. Below are essential commands for managing and analyzing memory usage in Linux.

## Checking Memory Usage with `free`

The `free` command displays available and used memory in the system. It shows memory usage in a human-readable format.

```bash
# free -g
```
Displays memory usage in gigabytes.

```bash
# free -m
```
Displays memory usage in megabytes.

```bash
# free -k
```
Displays memory usage in kilobytes.

---

## Monitoring System Performance with `vmstat`

The `vmstat` command provides detailed system performance statistics.

```bash
# vmstat
```
Displays CPU and memory usage statistics.

```bash
# vmstat -a
```
Shows active and inactive memory.

```bash
# vmstat -d
```
Displays disk statistics.

```bash
# vmstat -S k
```
Shows statistics in kilobytes.

```bash
# vmstat -S M
```
Shows statistics in megabytes.

```bash
# vmstat 4 5
```
Continuous Monitoring, Displays 5 reports every 4 seconds.

```bash
# vmstat -S M 4 5
```
Same as above but in megabytes.

```bash
# vmstat -t 4 5 -S M
```
Includes timestamp in the output, Displays output in megabytes with timestamps.

---

## Disk and CPU Performance with `iostat`

The `iostat` command helps analyze CPU and disk I/O performance.

### Install `iostat` if not available

```bash
# yum install sysstat
```

```bash
# iostat
```
Displays CPU and disk performance statistics.

```bash
# iostat 4 5
```
Updates the statistics 5 times, with a 4-second interval.

---

## Listing Open Files with `lsof`

The `lsof` (List Open Files) command displays files opened by processes.

### Install `lsof` if not installed

```bash
# yum install lsof
```

```bash
# lsof
```
Lists all open files.

```bash
# lsof -u root
```
Shows open files for root.

```bash
# lsof -u nikhil
```
Shows open files for user `nikhil`.

```bash
# lsof -u root -n
```
Displays open files for root, without resolving hostnames.

### Checking Network Connections with `lsof`

```bash
# lsof -i
```
Lists all open network connections.

```bash
# lsof -i -n
```
Shows open network connections, without resolving hostnames.

```bash
# lsof -n -i TCP
```
Filtering by Protocol, Lists open TCP connections.

```bash
# lsof -n -i UDP
```
Lists open UDP connections.

```bash
# lsof -n -i TCP:22
```
Shows processes using port 22 (SSH).

```bash
# lsof -n -i TCP:80,443,22
```
Lists connections on ports 80 (HTTP), 443 (HTTPS), and 22 (SSH).

```bash
# lsof -n -i TCP:80-500
```
Displays TCP connections within port range 80-500.

```bash
# lsof -n -i UDP:53
```
Shows UDP connections on port 53 (DNS).

```bash
# lsof -n -i -p 1571
```
Displays open network files for process 1571.

```bash
# lsof -n -i 4
```
Shows IPv4 connections.

```bash
# lsof -n -i 6
```
Shows IPv6 connections.

### Killing Processes Using `lsof`

```bash
# kill -9 'lsof -t -u nikhil'
```

---

## Summary of Memory Process Monitoring Commands

| Command | Purpose |
| ------- | ------- |
| `free -h` | Show memory usage in human-readable format |
| `vmstat 4 5` | Monitor CPU and memory stats every 4 seconds, 5 times |
| `iostat` | View CPU and disk performance |
| `lsof -u` | List files opened by user |
| `lsof -n -i TCP:22` | Show processes using port 22 (SSH) |
| `kill -9 'lsof -t -u nikhil'` | Kill all processes owned by `nikhil` |
```

This format is ready to be used on GitHub for proper markdown rendering!
