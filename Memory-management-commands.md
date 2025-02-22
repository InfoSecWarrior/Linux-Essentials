# Memory Management and System Performance Commands

## 1. Memory Management Commands

1. **Free Command:**
   - `free -h`: Display memory usage in human-readable format (KB, MB, GB).
     ```bash
     free -h
     ```

   - `free -g`: Display memory usage in gigabytes.
     ```bash
     free -g
     ```

   - `free -m`: Display memory usage in megabytes.
     ```bash
     free -m
     ```

   - `free -k`: Display memory usage in kilobytes.
     ```bash
     free -k
     ```

---

## 2. System Performance Commands

1. **Vmstat Command:**
   - `vmstat`: Display basic system performance stats (memory, CPU, processes, etc.).
     ```bash
     vmstat
     ```

   - `vmstat -a`: Show active memory and swap usage.
     ```bash
     vmstat -a
     ```

   - `vmstat -d`: Display disk statistics.
     ```bash
     vmstat -d
     ```

   - `vmstat -s`: Display summary of memory, swap, and disk statistics.
     ```bash
     vmstat -s
     ```

   - `vmstat 4 5`: Display performance stats every 4 seconds for 5 iterations.
     ```bash
     vmstat 4 5
     ```

   - `vmstat -s m 4 5`: Display memory statistics every 4 seconds for 5 iterations.
     ```bash
     vmstat -s m 4 5
     ```

2. **Iostat Command:**
   - `iostat`: Display input/output statistics for devices and partitions.
     ```bash
     iostat
     ```

   - Install `iostat` if not installed:
     ```bash
     yum install sysstat
     ```

   - `iostat 4 5`: Display I/O statistics every 4 seconds for 5 iterations.
     ```bash
     iostat 4 5
     ```

---

3. **Listing Open Files with `lsof`**

   - Install `lsof` Command (if not installed):
     ```bash
     yum install lsof
     ```

   - To list open files by the user `root`:
     ```bash
     lsof -u root
     ```

   - To list network files (all types of network connections):
     ```bash
     lsof -N -i
     ```

   - To list open UDP network connections:
     ```bash
     lsof -n -i UDP
     ```

   - To list open TCP network connections:
     ```bash
     lsof -n -i TCP
     ```

   - To list open TCP port 22 (usually SSH):
     ```bash
     lsof -n -i TCP:22
     ```

   - To list open UDP ports 22, 443, and 90:
     ```bash
     lsof -n -i UDP:22,443,90
     ```

   - To list open UDP ports in the range 80-220:
     ```bash
     lsof -n -i UDP:80-220
     ```

   - To list open files for process ID 6029:
     ```bash
     lsof -n -p 6029
     ```

   - To list open IPv4 network connections:
     ```bash
     lsof -n -i 4
     ```

   - To list open IPv6 network connections:
     ```bash
     lsof -n -i 6
     ```

   - To get process IDs (PIDs) of files opened by the user `Armour`:
     ```bash
     lsof -t -u Armour
     ```
---

## 3. Killing Processes Using `kill`

   - To kill processes opened by the user `Armour` using the process IDs (PIDs) retrieved from `lsof`:
     ```bash
     kill -9 $(lsof -t -u Armour)
     ```
___
