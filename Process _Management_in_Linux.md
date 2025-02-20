**Process Management in Linux**

Process management is crucial for monitoring and controlling system performance. Linux provides various commands to manage processes efficiently.

### **Running Commands in the Background & Foreground**

- **Run a command in the foreground:**  
  ```bash
  ping 8.8.8.8
  ```
  This command runs `ping` and keeps it active in the current terminal.

- **Run a command in the background:**  
  ```bash
  ping 8.8.8.8 &
  ```
  The `&` symbol runs the command in the background, allowing the terminal to be free for other tasks.

- **Bringing a background job to the foreground:**  
  ```bash
  fg
  ```
  This command brings the last background job to the foreground.

- **Bringing a specific job to the foreground:**  
  ```bash
  fg 2
  ```
  This brings job number 2 to the foreground.

### **Viewing and Managing Jobs**

- **List all background jobs in the current terminal:**  
  ```bash
  jobs
  ```

### **Viewing Processes with `ps` Command**

- **Show processes running in the current shell session:**  
  ```bash
  ps
  ```

- **Display more details about running processes:**  
  ```bash
  ps -L
  ```

- **List all processes with CPU and memory usage (BSD-style format):**  
  ```bash
  ps -aux
  ```

- **List all processes using standard syntax:**  
  ```bash
  ps -e
  ```

- **Display processes in a hierarchical tree format:**  
  ```bash
  ps -axjf
  ```

- **Show processes owned by root:**  
  ```bash
  ps -U root -u root u
  ```

- **Show processes owned by a specific user (e.g., armour):**  
  ```bash
  ps -U armour -u armour
  ```

### **Monitoring Processes in Real-Time**

- **Display real-time system processes:**  
  ```bash
  top
  ```

- **Better alternative to `top`: Install and use `htop`**
  ```bash
  apt install htop  # Debian/Ubuntu
  yum install htop  # RHEL/CentOS
  htop
  ```

- **Show tree structure in `htop`:**  
  ```bash
  htop -t
  ```

- **Display processes for a specific user (e.g., armour):**  
  ```bash
  htop -t -u armour
  ```

- **Show details of a specific process by PID (e.g., 2780):**  
  ```bash
  htop -t -p 2780
  ```

### **Killing Processes**

- **Terminate a process using its PID (e.g., 2526):**  
  ```bash
  kill 2526
  ```

- **Forcefully kill a process (e.g., 7500):**  
  ```bash
  kill -9 7500
  ```

- **Kill all instances of a process (e.g., `sed`):**  
  ```bash
  yum install psmisc
  killall seq
  ```

- **Kill all processes with names matching a pattern (e.g., `firefox`):**  
  ```bash
  killall -r firefox
  ```

- **Kill all processes owned by a specific user (e.g., armour):**  
  ```bash
  killall -u armour
  ```

- **Kill all `ping` processes using `pkill`:**  
  ```bash
  pkill ping
  ```

- **Kill all processes owned by a user (e.g., armour):**  
  ```bash
  pkill -u armour
  ```

- **Kill an exact process owned by a user (e.g., `ping` owned by armour):**  
  ```bash
  pkill -u armour -x ping
  ```

