### **Short Explanation of `grep` Command in Linux**  

The `grep` command (**Global Regular Expression Print**) is used in Linux/Unix to search for text patterns in files and command outputs.  

#### **Basic Syntax:**  
```bash
grep [OPTIONS] PATTERN [FILE...]
```

---

### **Common `grep` Usage & Examples**  

1️⃣ **Search for a string in a file**  
```bash
grep "error" file.txt
```
✔ Finds and displays lines containing `"error"` in `file.txt`.

2️⃣ **Recursive search in directories**  
```bash
grep -r "error" /path/to/directory
```
✔ Searches `"error"` in all files within a directory.

3️⃣ **Case-insensitive search (`-i`)**  
```bash
grep -i "error" file.txt
```
✔ Matches `error`, `ERROR`, `Error`, etc.

4️⃣ **Show line numbers (`-n`)**  
```bash
grep -n "error" file.txt
```
✔ Displays matching lines along with their line numbers.

5️⃣ **Count occurrences (`-c`)**  
```bash
grep -c "error" file.txt
```
✔ Outputs how many lines contain `"error"`.

6️⃣ **Invert match (`-v`)**  
```bash
grep -v "error" file.txt
```
✔ Displays lines that **do not** contain `"error"`.

7️⃣ **Match whole words (`-w`)**  
```bash
grep -w "error" file.txt
```
✔ Matches `"error"`, but not `"errors"`, `"errored"`.

8️⃣ **Use regular expressions (`-E`)**  
```bash
grep -E "error|warning" file.txt
```
✔ Matches either `"error"` or `"warning"`.

9️⃣ **Display filenames with matches (`-l`)**  
```bash
grep -l "error" *.txt
```
✔ Lists filenames containing `"error"`.

🔟 **Highlight matches (`--color`)**  
```bash
grep --color "error" file.txt
```
✔ Highlights `"error"` in the output.

---

### **Using Wildcards in `grep`**  
✅ **Search in all `.txt` files:**  
```bash
grep "error" *.txt
```
✅ **Search in files with a specific pattern:**  
```bash
grep "error" log[1-3].txt
```
✅ **Search and exclude certain file types:**  
```bash
grep -r "error" --exclude="*.log" /path/
```
✅ **Search with wildcard patterns (`.*`)**  
```bash
grep "err.*" file.txt
```
✔ Matches `err`, `error`, `erroneous`.

---

### **Combining `grep` with Other Commands**  
🔹 **Find processes related to SSH:**  
```bash
ps aux | grep "ssh"
```
🔹 **Filter logs to show only errors:**  
```bash
cat system.log | grep "error"
```
🔹 **Count failed login attempts:**  
```bash
grep -c "failed" auth.log
```

---

