# Basic Linux Commands

1. **pwd**  
   Shows the current directory you are in.
   ```bash
   pwd
   ```

2. **ls**  
   Lists all files and directories in the current directory.
   ```bash
   ls
   ```

3. **info**  
   Provides detailed information about a command.
   ```bash
   info ls
   ```

4. **man**  
   Displays the manual or instructions on how to use a command.
   ```bash
   man ls
   ```

5. **ls --help**  
   Displays help information for the `ls` command, showing available options and their usage.
   ```bash
   ls --help
   ```

6. **ls -l**  
   Lists files and directories in long format, showing detailed information like file permissions, owner, size, and date modified.
   ```bash
   ls -l
   ```

7. **ls -a**  
   Lists all files, including hidden files (those starting with a dot `.`).
   ```bash
   ls -a
   ```

8. **ls -h**  
   Displays the file size in a human-readable format (e.g., MB, KB).
   ```bash
   ls -lh
   ```

9. **ls -R**  
   Lists files and directories recursively (i.e., shows the contents of subdirectories).
   ```bash
   ls -R
   ```

10. **ls -r**  
   Displays the directory contents in reverse order.
   ```bash
   ls -r
   ```

11. **cd**  
   Changes the current directory to the specified directory.
   ```bash
   cd downloads
   ```

12. **cd ..**  
   Moves one level up in the directory tree.
   ```bash
   cd ..
   ```

13. **mkdir foldername**  
   Creates a new directory with the specified name.
   ```bash
   mkdir new_folder
   ```

14. **clear**  
   Clears the terminal screen.
   ```bash
   clear
   ```

15. **/**  
   Refers to the root directory, the topmost directory in Linux.
   ```bash
   cd /
   ```

16. **touch filename**  
   Creates an empty file with the specified name.
   ```bash
   touch file.txt
   ```

17. **cat**  
   Displays the contents of a file in the terminal.
   ```bash
   cat file.txt
   ```

18. **cat > filename**  
   Allows you to create a file and add content to it. You can exit the editor by pressing `Ctrl + C`.
   ```bash
   cat > file.txt
   ```

19. **rmdir foldername**  
   Deletes an empty directory.
   ```bash
   rmdir foldername
   ```

20. **rm**  
   Deletes a file.
   ```bash
   rm file.txt
   ```

21. **rm -rf**  
   Forcefully deletes a directory and its contents, including subdirectories and files.
   ```bash
   rm -rf foldername
   ```

22. **mkdir -p**  
   Creates nested directories in a single command.
   ```bash
   mkdir -p folder1/folder2/folder3
   ```

23. **cp**  
   Copies files or directories.
   ```bash
   cp file.txt /home/user/
   ```

24. **cp -v**  
   Copies files with verbosity, showing each file as it's copied.
   ```bash
   cp -v file.txt /home/user/
   ```

25. **cp -f**  
   Forces copying, overwriting any existing files without asking for confirmation.
   ```bash
   cp -f file.txt /home/user/
   ```

26. **cp -r**  
   Copies directories recursively.
   ```bash
   cp -r folder1/ folder2/
   ```

27. **mv**  
   Moves or renames files and directories.
   ```bash
   mv oldname.txt newname.txt
   ```

28. **ln -s**  
   Creates a symbolic (soft) link to a file or directory.
   ```bash
   ln -s /path/to/file linkname
   ```

29. **ln**  
   Creates a hard link to a file or directory.
   ```bash
   ln /path/to/file hardlinkname
   ```

30. **less**  
   Displays file content page by page.
   ```bash
   less file.txt
   ```

31. **more**  
   Similar to `less`, but with limited scrolling capability.
   ```bash
   more file.txt
   ```

32. **date**  
   Displays the current date and time.
   ```bash
   date
   ```

33. **id**  
   Displays the current user's UID (User ID), GID (Group ID), and group memberships.
   ```bash
   id
   ```

34. **whoami**  
   Shows the username of the currently logged-in user.
   ```bash
   whoami
   ```

35. **who**  
   Displays who is logged into the system, along with information like login time and terminal.
   ```bash
   who
   ```

36. **who -a**  
   Displays detailed information about the logged-in users, including the last login time.
   ```bash
   who -a
   ```

37. **w**  
   Shows detailed information about the users logged into the system, including their current activity and last commands.
   ```bash
   w
   ```

38. **tty**  
   Displays the terminal device you are using.
   ```bash
   tty
   ```

39. **hostname**  
   Displays the current system's hostname.
   ```bash
   hostname
   ```

40. **hostname -a**  
   Displays all the hostnames associated with the system.
   ```bash
   hostname -a
   ```

41. **hostname -i**  
   Displays the IP address of the current machine.
   ```bash
   hostname -i
   ```

42. **hostname -I**  
   Displays all available IP addresses associated with the system.
   ```bash
   hostname -I
   ```

43. **ifconfig**  
   Displays network interface configurations, such as IP address, netmask, and MAC address.
   ```bash
   ifconfig
   ```

44. **uname**  
   Displays basic information about the system's kernel.
   ```bash
   uname
   ```

45. **uname -a**  
   Displays detailed system and kernel information.
   ```bash
   uname -a
   ```

46. **cat /etc/os-release**  
   Displays information about the current operating system.
   ```bash
   cat /etc/os-release
   ```

47. **lscpu**  
   Displays detailed information about the system's CPU architecture.
   ```bash
   lscpu
   ```

48. **lsusb**  
   Lists all USB devices connected to the system.
   ```bash
   lsusb
   ```

49. **lspci**  
   Displays information about the PCI devices connected to the system.
   ```bash
   lspci
   ```

50. **lsblk**  
   Lists all block devices, such as hard drives, partitions, and storage devices.
   ```bash
   lsblk
   ```

51. **cal**  
   Displays a calendar for the current month.  
   You can specify a year as an argument, like `cal 2020` to view the calendar for 2020.
   ```bash
   cal
   ```

52. **free -h**  
   Displays memory and swap usage in a human-readable format.
   ```bash
   free -h
   ```

53. **route -n**  
   Displays the system's routing table, including gateways and network interfaces.
   ```bash
   route -n
   ```

54. **cat /etc/resolv.conf**  
   Displays DNS nameserver information.
   ```bash
   cat /etc/resolv.conf
   ```

55. **history**  
   Shows a list of previously executed commands in the terminal.
   ```bash
   history
   ```

56. **uptime**  
   Displays the system's uptime, i.e., how long the system has been running.
   ```bash
   uptime
   ```

57. **exit / logout**  
   Logs out or exits the current session.
   ```bash
   exit
   ```

58. **shutdown**  
   Shuts down the system.  
   You can also use:
   - `shutdown -c` to cancel a shutdown.
   - `shutdown -P` for a proper shutdown.
   - `shutdown -h` for a halt shutdown (abrupt).
   - `shutdown -P now` for immediate shutdown.
   - `poweroff` to turn off the system.
   - `init 0` to shut the system down.
   - `init 6` to reboot the system.
   - `shutdown -r` to restart the system.

   ```bash
   shutdown
   ```

---


### **Compression and Archive Tools**

**What is Compression?**  
Compression reduces file size for easier storage and transfer.

### 1) **bzip2**
   **Install**:  
   ```bash
   yum install bzip2
   ```
   **Compress**:  
   ```bash
   bzip2 filename
   bzip2 file1 file2
   bzip2 *.log
   ```
   **Decompress**:  
   ```bash
   bunzip2 filename.bz2
   bunzip2 *.log.bz2
   ```

### 2) **gzip**
   **Install**:  
   ```bash
   yum install gzip
   ```
   **Compress**:  
   ```bash
   gzip filename
   gzip -r foldername  # Recursive compression
   ```
   **Decompress**:  
   ```bash
   gunzip filename.gz
   gunzip *.gz  # Multiple files
   ```

### 3) **zip**
   **Install**:  
   ```bash
   yum install zip
   ```
   **Compress**:  
   ```bash
   zip file.zip filename
   zip -r file.zip foldername  # Compress folder
   ```
   **Decompress**:  
   ```bash
   unzip file.zip
   unzip -d destination_folder file.zip
   ```

### 4) **p7zip**
   **Install**:  
   ```bash
   yum install p7zip
   ```
   **Compress**:  
   ```bash
   7za a file.7z filename
   7za a archive.7z file1 file2
   ```
   **Decompress**:  
   ```bash
   7za e archive.7z
   7za x archive.7z  # Extract recursive folders
   ```

### 5) **tar**
   **Create archive**:  
   ```bash
   tar -cvf archive.tar files
   tar -cvf archive.tar file1 file2
   ```
   **Extract**:  
   ```bash
   tar -xvf archive.tar
   ```
   **Create and Compress**:  
   ```bash
   tar -cvjf archive.tbz files  # with bzip2 compression
   tar -xvf archive.tbz  # To extract
   ```


### **Pipes and Redirections in Linux**

**1) Redirect Output (`>`)**  
This command redirects the output of a command to a file, overwriting it if the file already exists.

**Example:**  
If you want to save the list of files in the current directory to a file called `files.txt`, use:
```bash
ls > files.txt  # Saves the output of 'ls' (file list) to files.txt, replacing its contents
```

---

**2) Append Output (`>>`)**  
Appends the output of a command to the end of a file without replacing the existing content.

**Example:**  
To add the current directory listing to `files.txt` without deleting the previous contents:
```bash
ls >> files.txt  # Adds the output of 'ls' to the end of files.txt
```

---

**3) Redirect Error Output (`2>`)**  
Redirects error messages (stderr) from a command to a file.

**Example:**  
If you want to capture any error messages from a failed command in `error.txt`:
```bash
ls non_existent_folder 2> error.txt  # Saves error messages to error.txt
```

---

**4) Redirect Both Output and Error (`&>` or `2>&1`)**  
Redirects both standard output (stdout) and error messages (stderr) to the same file.

**Example:**  
To save both output and errors to `output.txt`:
```bash
ls valid_folder non_existent_folder &> output.txt  # Both output and errors are saved to output.txt
```

---

**5) Pipe (`|`)**  
Sends the output of one command as input to another command.

**Example:**  
To count the number of files in the current directory:
```bash
ls | wc -l  # Sends the output of 'ls' to 'wc' to count the number of files
```

---

**6) Pipe with Multiple Commands**  
Chains several commands together, passing the output of one as the input to the next.

**Example:**  
To search for a word in files and count how many times it appears:
```bash
cat file.txt | grep "word" | wc -l  # Outputs the number of occurrences of "word"
```

---

**7) Redirect Input (`<`)**  
Uses a file as the input for a command, instead of entering it manually.

**Example:**  
To count the number of lines in a file, use:
```bash
wc -l < file.txt  # Uses file.txt as input to count lines
```

---

**8) Redirect Input and Output Simultaneously**  
Redirects both input from a file and output to a different file.

**Example:**  
To sort the contents of `input.txt` and save the sorted output to `output.txt`:
```bash
sort < input.txt > output.txt  # Takes input from input.txt and writes sorted output to output.txt
```

---

**9) Output to Multiple Files (`tee`)**  
The `tee` command lets you view output and save it to a file simultaneously.

**Example:**  
To display the output and also save it to `file.txt`:
```bash
echo "Hello, World!" | tee file.txt  # Displays the output and saves it to file.txt
```

---

**10) Discard Output (`/dev/null`)**  
Sends the output (or errors) to `/dev/null`, effectively discarding it.

**Example:**  
To discard any output from a command:
```bash
ls > /dev/null  # Discards standard output
```

To discard only error messages:
```bash
ls non_existent_folder 2> /dev/null  # Discards error messages
```

---

**11) Redirect Error to Output (`2>&1`)**  
Redirects error messages (stderr) to the same place as standard output (stdout).

**Example:**  
To capture both the output and error messages from a command:
```bash
ls valid_folder non_existent_folder 2>&1  # Combines both stdout and stderr
```

---

**12) Combining Input and Output Redirection**  
Redirects both input from a file and output to a different file at the same time.

**Example:**  
To take input from `input.txt` and save output to `output.txt`:
```bash
cat < input.txt > output.txt  # Reads from input.txt and writes to output.txt
```

---


-------------------------------------------------------------------------------------------------------------------------


Here are the **5 MOST DANGEROUS COMMANDS**:

---

### **1) `rm -rf /`**  
This command will recursively and forcefully delete everything starting from the root directory (`/`), wiping out all system files, directories, and personal data. It will render the system completely unusable.

---

### **2) `sudo rm -rf /`**  
Running `rm -rf /` with `sudo` grants root privileges, bypassing any permission restrictions. This will delete the entire system, including important system files and directories, making the system unbootable.

---

### **3) `rm -rf ~/*`**  
This command will delete all files and directories in the current user's home directory (`~`), including personal files, configurations, and settings. It's particularly dangerous if run unintentionally in your home directory.

---

### **4) `rm -rf /dev/*`**  
The `/dev` directory contains critical device files for interacting with hardware. Deleting files from this directory will cause severe system issues, potentially making the system unable to access devices, such as storage and peripherals.

---

### **5) `rm -rf /bin /sbin /lib /lib64`**  
These directories contain essential system binaries and libraries. Removing these files will render the system unbootable, as these are required for basic system operations, including running commands and starting the system.

---

**Important Warning:** Always be extremely cautious with the `rm -rf` command, especially when using it as root. It can cause irreversible data loss or make the system unusable.
