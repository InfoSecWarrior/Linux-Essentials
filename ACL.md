
# **Access Control List (ACL) in Linux**  

## **Overview**  
Access Control List (ACL) provides a more flexible way to define file and directory permissions beyond the traditional **owner-group-other** model in Linux. ACLs allow administrators to assign specific access rights (**read, write, execute**) to individual users or groups, ensuring finer control over permissions.  

---

## **Why Use ACL?**  

- Assign specific permissions to multiple users or groups for the same file or directory.  
- Extend beyond standard **rwx** permissions for more complex access control scenarios.  
- Allow finer-grained control over permissions when the default **owner-group-other** model is insufficient.  

---

## **Key ACL Commands**  

### **1. Enable ACL on a File System**  
Ensure the file system supports ACL (e.g., `ext4`, `xfs`).  

- Remount the file system with ACL support:  
    ```bash
    mount -o remount,acl /mount_point
    ```
- To make this change persistent, edit `/etc/fstab`:  
    ```ini
    /dev/sda1 / ext4 defaults,acl 0 1
    ```

---

### **2. View ACL of a File or Directory**  
Use the `getfacl` command to check ACL settings:  
```bash
getfacl filename
```  
#### **Example Output:**  
```
# file: filename
# owner: root
# group: root
user::rw-
user:john:rw-
group::r--
mask::rw-
other::r--
```

---

### **3. Set ACL for a User**  
Assign permissions to a specific user using `setfacl`:  
```bash
setfacl -m u:username:permissions filename
```  
#### **Example:**  
Grant **read and write** permissions to user `john` for `myfile.txt`:  
```bash
setfacl -m u:john:rw- myfile.txt
```

---

### **4. Set ACL for a Group**  
Assign permissions to a specific group using `setfacl`:  
```bash
setfacl -m g:groupname:permissions filename
```  
#### **Example:**  
Grant **read-only** access to the `developers` group for `myfile.txt`:  
```bash
setfacl -m g:developers:r-- myfile.txt
```

---

### **5. Remove ACL for a User or Group**  

#### **Remove ACL for a Specific User:**  
```bash
setfacl -x u:username filename
```  
#### **Example:**  
Remove ACL for user `john`:  
```bash
setfacl -x u:john myfile.txt
```

#### **Remove All ACL Entries (Reset to Default Permissions):**  
```bash
setfacl -b filename
```

---

### **6. Set Default ACL for Directories**  
Default ACL ensures that new files or subdirectories inherit specified permissions.  

```bash
setfacl -m d:u:username:permissions directory
```  
#### **Example:**  
Ensure all new files in `/shared_directory` allow `john` to **read and write**:  
```bash
setfacl -m d:u:john:rw- /shared_directory
```

---

## **ACL Permission Syntax**  
ACL permissions follow the standard **rwx** model:  

| Permission | Meaning |
|------------|----------|
| `r--` | Read-only |
| `rw-` | Read and write |
| `rwx` | Read, write, and execute |

---

## **Practical Examples**  

### **Example 1: Allow a User to Edit a File**  
```bash
# Grant user 'john' read and write permissions to 'report.txt'
setfacl -m u:john:rw- report.txt

# Verify ACL
getfacl report.txt
```

### **Example 2: Allow a Group to Read a Directory**  
```bash
# Grant group 'team' read-only access to the directory
setfacl -m g:team:r-- /data/projects

# Verify ACL
getfacl /data/projects
```

### **Example 3: Set Default ACL for New Files in a Directory**  
```bash
# Ensure all new files in '/data/shared' allow 'john' to read and write
setfacl -m d:u:john:rw- /data/shared
```

---

## **Conclusion**  
ACLs in Linux provide a powerful method for **fine-grained access control** over files and directories. They extend the traditional permission system, allowing administrators to manage complex access scenarios efficiently. By implementing ACLs, system administrators can improve security and access management in multi-user environments.  
