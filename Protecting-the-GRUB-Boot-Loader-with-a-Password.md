
# **Protecting the GRUB Boot Loader with a Password (CentOS 9/Linux)**  

The GRUB (Grand Unified Bootloader) is responsible for loading the Linux operating system. Protecting it with a password prevents unauthorized users from modifying kernel parameters, booting into single-user mode, or accessing system recovery options.  

---

## **1. Why Secure the GRUB Boot Loader?**  
- Prevent **unauthorized users** from modifying boot parameters.  
- Restrict access to **single-user mode**, which can be used to reset passwords.  
- Protect the system from **boot-time attacks** and unauthorized changes.  

---

## **2. Steps to Secure GRUB with a Password**  

### **Step 1: Install the Required Package**  
By default, GRUB should be installed, but ensure it is present on your system.  

```bash
dnf install grub2-tools
```  

---

### **Step 2: Generate an Encrypted GRUB Password**  

1. Use the `grub2-mkpasswd-pbkdf2` command to create an encrypted password.  
   
   ```bash
   grub2-mkpasswd-pbkdf2
   ```  

2. You will be prompted to enter a new password. **Enter and confirm the password** securely.  

3. The system generates an encrypted password (PBKDF2 hash), similar to:  

   ```
   grub.pbkdf2.sha512.10000.XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
   ```

4. **Copy this password**, as it will be used in the next step.  

---

### **Step 3: Edit the GRUB Configuration File**  

1. Open the GRUB configuration file for editing:  

   ```bash
   nano /etc/grub.d/40_custom
   ```  

2. Add the following lines at the **end of the file**:  

   ```bash
   set superusers="admin"
   password_pbkdf2 admin grub.pbkdf2.sha512.10000.XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
   ```

   - Replace `"admin"` with your desired **GRUB username**.  
   - Replace `"grub.pbkdf2.sha512...` with your **generated password hash** from Step 2.  

3. Save the file and exit (`CTRL + X`, then `Y`, and press `Enter`).  

---

### **Step 4: Update the GRUB Configuration**  

After modifying the configuration file, update GRUB so changes take effect.  

1. Run the following command to update the GRUB configuration:  

   ```bash
   grub2-mkconfig -o /boot/grub2/grub.cfg
   ```

2. Verify that the new password entry appears in `/boot/grub2/grub.cfg`:  

   ```bash
   cat /boot/grub2/grub.cfg | grep "password_pbkdf2"
   ```

---

### **Step 5: Testing GRUB Password Protection**  

1. **Reboot the system:**  

   ```bash
   reboot
   ```  

2. At the **GRUB boot menu**, try **editing a boot entry** by pressing `e`.  
3. The system should **prompt for authentication** before allowing edits.  
4. Enter the **username and password** you set up in Step 3.  

---

## **3. Additional Security Measures**  

- **Restrict BIOS Access:** Set a **BIOS/UEFI password** to prevent booting from external devices.  
- **Enable Secure Boot:** Helps prevent unauthorized modifications to the bootloader.  
- **Disable USB Boot:** Prevents attackers from using live USBs to bypass security.  

---

## **4. Summary of Key Commands**  

| **Action** | **Command** |
|------------|------------|
| Install GRUB tools | `dnf install grub2-tools` |
| Generate GRUB password | `grub2-mkpasswd-pbkdf2` |
| Edit GRUB custom config | `nano /etc/grub.d/40_custom` |
| Update GRUB configuration | `grub2-mkconfig -o /boot/grub2/grub.cfg` |
| Verify password entry in GRUB | `cat /boot/grub2/grub.cfg | grep "password_pbkdf2"` |
| Reboot system | `reboot` |

---

By following these steps, you have successfully secured the **GRUB boot loader** with a **password**, enhancing your system's security against unauthorized modifications. 
