# **CHOWN** and **CHMOD**


## **1. Changing Ownership with `chown`**  

The `chown` command is used to change the **owner** and/or **group** of a file or directory.  

### **Check the Current Owner and Group**  
To see the ownership of a file:  
```sh
ls -l filename
```
Example output:  
```sh
-rw-r--r-- 1 user1 group1 1234 Feb 14 10:00 file.txt
```
- **First `user1`** → File owner  
- **Second `group1`** → File group  

### **Change the Owner of a File**  
To assign a new owner to a file:  
```sh
chown newuser filename
```

### **Change the Group of a File**  
To change only the group:  
```sh
chown :newgroup filename
```

### **Change Both Owner and Group**  
To change both owner and group:  
```sh
chown newuser:newgroup filename
```

### **Change Ownership Recursively**  
To apply changes to all files inside a directory:  
```sh
chown -R newuser:newgroup directory/
```

---

## **2. Changing Permissions with `chmod`**  

The `chmod` command modifies **read (r), write (w), and execute (x)** permissions for the **user (u), group (g), and others (o)**.  

### **Permission Structure**  
| Symbol | User | Permission Type | Numeric Value |
|--------|------|----------------|---------------|
| `r` | Read | Can read the file | `4` |
| `w` | Write | Can modify the file | `2` |
| `x` | Execute | Can execute the file | `1` |

To check permissions:  
```sh
ls -l filename
```
Example output:  
```sh
-rwxr-xr-- 1 user group 1234 Feb 14 10:00 script.sh
```
- `rwx` → Owner can read, write, execute  
- `r-x` → Group can read and execute  
- `r--` → Others can only read  

### **Change Permissions Using Numeric (Octal) Mode**  
```sh
chmod 755 script.sh
```
- **Owner (`7`)** → `rwx` (4+2+1)  
- **Group (`5`)** → `r-x` (4+0+1)  
- **Others (`5`)** → `r-x` (4+0+1)  

### **Change Permissions Using Symbolic Mode**  
```sh
chmod u+rwx,g+rx,o+r script.sh
```
- `u+rwx` → User gets **read, write, execute**  
- `g+rx` → Group gets **read and execute**  
- `o+r` → Others get **read-only**  

### **Common Permission Settings**  
| Command | Meaning |
|---------|---------|
| `chmod 777 file` | Everyone can read, write, and execute (**⚠️ Security risk**) |
| `chmod 755 file` | Owner can read, write, execute; others can read and execute |
| `chmod 644 file` | Owner can read/write, others can only read |
| `chmod 600 file` | Only owner can read/write |
| `chmod 400 file` | Only owner can read (no write/execute) |
| `chmod 000 file` | No one can access the file |

### **Change Permissions Recursively**  
```sh
chmod -R 755 directory/
```
- Applies permissions to **all files and subdirectories** inside `directory/`.

---


---

## **Conclusion**  
- **Use `chown`** to change file ownership.  
- **Use `chmod`** to modify file permissions.  
- **Use octal (`755`) or symbolic (`u+x`) notation** for permission changes.  
- **Be careful with `chmod 777`**—it gives **everyone** full control!  
- **Use `-R`** for recursive changes.  

---
