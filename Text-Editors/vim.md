# **`vim` Text Editor**  

The `vim` (Vi IMproved) editor is a powerful, highly configurable text editor used for programming and general text editing. It is an enhanced version of `vi`, offering more features like syntax highlighting, undo levels, and plugins.  


## **`vim`**  

### **Syntax**  
```
vim [OPTIONS] filename
```

### **Examples**  

- Open a file for editing:  
  ```
  vim file.txt
  ```

- Open a file in **read-only mode**:  
  ```
  vim -R file.txt
  ```

- Open a file and jump to a specific line:  
  ```
  vim +10 file.txt
  ```

- Open multiple files:  
  ```
  vim file1.txt file2.txt
  ```
  (Use :n to go to the next file and :N to go to the previous file.) 

- Open a file in **diff mode** (compare two files):  
  ```
  vim -d file1.txt file2.txt
  ```


## **`Vim` Modes**  

Vim operates in **different modes**, each designed for specific tasks.  

### **1. Normal Mode (Esc Mode)**  
- This is the **default mode** when Vim starts.  
- Used for navigation, editing, and executing commands.  
- To enter **Normal Mode**, press:  
  ```
  Esc
  ```
- Example commands in Normal Mode:  
  - Move to the beginning of a line: `0`  
  - Move to the end of a line: `$`  
  - Move to line 50: `50G`  
  - Delete a line: `dd`  
  - Copy (yank) a line: `yy`  
  - Paste copied text: `p`  
  - Save file: `:w`  
  - Quit Vim: `:q`  
  - Force quit without saving: `:q!`  

---

### **2. Insert Mode**  
- Used for **writing and editing** text.  
- To enter **Insert Mode**, press one of the following keys in Normal Mode:  
  - `i` → Insert at cursor position  
  - `I` → Insert at the beginning of the line  
  - `a` → Append after cursor  
  - `A` → Append at the end of the line  
  - `o` → Open a new line below  
  - `O` → Open a new line above  
- To exit **Insert Mode**, press:  
  ```
  Esc
  ```  

---

### **3. Replace Mode**  
- Used to **overwrite existing text**.  
- To enter **Replace Mode**, press:  
  ```
  R
  ```
- Example:  
  - Press `R`, then type new text → **replaces** characters instead of inserting.  
  - Press `Esc` to return to Normal Mode.  

---

### **4. Visual Mode**  
- Used for **selecting text** to copy, delete, or edit.  
- To enter **Visual Mode**, press:  
  - `v` → Start **character-wise** selection  
  - `V` → Start **line-wise** selection  
  - `Ctrl + v` → Start **block selection (column mode)**  
- Example:  
  - Select multiple lines and copy:  
    ```
    V (select lines) → y
    ```
  - Select and delete text:  
    ```
    v (select text) → d
    ```
  - Select and replace text:  
    ```
    v (select text) → c (change text)
    ```
- To exit **Visual Mode**, press:  
  ```
  Esc
  ```  


## **Basic `Vim` Commands**  

- **Save file**: `:w`  
- **Quit Vim**: `:q`  
- **Save and quit**: `:wq` or `ZZ`  
- **Quit without saving**: `:q!`  
- **Find and replace**: `:%s/old/new/g`  
- **Undo last change**: `u`  
- **Redo last change**: `Ctrl + r`  

