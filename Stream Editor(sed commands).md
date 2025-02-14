# sed (Stream Editor)

The `sed` command (short for Stream Editor) is a powerful text manipulation tool in Linux/Unix. It is used to perform basic text transformations on an input stream (a file or input from a pipeline). `sed` is commonly used for tasks such as search-and-replace, text insertion, deletion, and more.

### **Basic Syntax of `sed`**:

```bash
sed 'command' filename

```

- **command**: The operation `sed` should perform.
- **filename**: The file on which the `sed` operation is to be applied.

### **Common Uses of `sed`**

### 1. **Substitute (Search and Replace)**:

The most common use of `sed` is for search and replace, using the `s` command. The basic syntax is:

```bash
sed 's/old_text/new_text/' filename

```

- This will replace the first occurrence of `old_text` with `new_text` in each line.

### Example:

```bash
sed 's/hello/world/' file.txt

```

- This replaces the first occurrence of "hello" with "world" in each line of `file.txt`.

### 2. **Global Replacement**:

To replace all occurrences of a pattern in a line, use the `g` flag:

```bash
sed 's/old_text/new_text/g' filename

```

### Example:

```bash
sed 's/hello/world/g' file.txt

```

- This replaces every occurrence of "hello" with "world" in each line of `file.txt`.

### 3. **In-place Editing**:

To modify the file directly without needing to redirect the output to a new file, use the `-i` option:

```bash
sed -i 's/old_text/new_text/' filename

```

- This changes the file `filename` in place.

### Example:

```bash
sed -i 's/hello/world/g' file.txt

```

- This will replace every occurrence of "hello" with "world" directly in `file.txt`.

### 4. **Delete Lines**:

You can delete lines that match a specific pattern using the `d` command.

```bash
sed '/pattern/d' filename

```

- This will delete any line containing the word `pattern`.

### Example:

```bash
sed '/error/d' file.txt

```

- This deletes all lines that contain the word "error" in `file.txt`.

### 5. **Print Specific Lines**:

To print only specific lines (using line numbers), use the `-n` option in conjunction with the `p` command:

```bash
sed -n '5p' filename

```

- This will print the 5th line of the file `filename`.

### Example:

```bash
sed -n '3,6p' file.txt

```

- This will print lines 3 through 6 from `file.txt`.

### 6. **Replace Text on Specific Line Number**:

You can also replace text only on a specific line or range of lines by specifying the line number:

```bash
sed '3s/old_text/new_text/' filename

```

- This will replace `old_text` with `new_text` only on the 3rd line.

### Example:

```bash
sed '2,4s/hello/world/' file.txt

```

- This will replace "hello" with "world" in lines 2 through 4 of `file.txt`.

### 7. **Insert Text**:

You can insert a line before or after a matching line with the `i` (insert) or `a` (append) commands.

- **Insert before a line**:
    
    ```bash
    sed '/pattern/i\new_line' filename
    
    ```
    
    - This inserts `new_line` before every line containing `pattern`.

### Example:

```bash
sed '/error/i\This is an error message' file.txt

```

- This inserts "This is an error message" before every line containing "error".
- **Append after a line**:
    
    ```bash
    sed '/pattern/a\new_line' filename
    
    ```
    
    - This appends `new_line` after every line containing `pattern`.

### Example:

```bash
sed '/error/a\Please check this error' file.txt

```

- This appends "Please check this error" after every line containing "error".

### 8. **Change Text**:

To change a line, you can use the `c` command:

```bash
sed '3c\new_line' filename

```

- This changes the 3rd line of the file to `new_line`.

### Example:

```bash
sed '3c\This is the new line' file.txt

```

- This changes the 3rd line to "This is the new line."

### 9. **Using Regular Expressions**:

`sed` supports regular expressions (regex) for more advanced pattern matching.

- **Match any character**:
    
    ```bash
    sed 's/./X/' file.txt
    
    ```
    
    - This replaces the first character of each line with "X".
- **Match one or more digits**:
    
    ```bash
    sed 's/[0-9]\+/NUMBER/' file.txt
    
    ```
    
    - This replaces one or more digits with the word "NUMBER".

### 10. **Multiple Commands**:

You can combine multiple `sed` commands using the `-e` option or by separating commands with semicolons.

```bash
sed -e 's/old_text/new_text/' -e 's/foo/bar/' filename

```

- This applies two commands in sequence: replacing `old_text` with `new_text` and `foo` with `bar`.

### Example:

```bash
sed 's/hello/world/; s/foo/bar/' file.txt

```

- This replaces "hello" with "world" and "foo" with "bar" in the same pass.

---

### **Examples of `sed` Commands**

1. **Replace "cat" with "dog" in a file**:
    
    ```bash
    sed 's/cat/dog/' file.txt
    
    ```
    
2. **Replace all occurrences of "cat" with "dog"**:
    
    ```bash
    sed 's/cat/dog/g' file.txt
    
    ```
    
3. **Delete lines that contain "error"**:
    
    ```bash
    sed '/error/d' file.txt
    
    ```
    
4. **Print lines 1 to 5**:
    
    ```bash
    sed -n '1,5p' file.txt
    
    ```
    
5. **Insert "This is a new line" before every line containing "pattern"**:
    
    ```bash
    sed '/pattern/i\This is a new line' file.txt
    
    ```
    
6. **Change line 2 to "This is a changed line"**:
    
    ```bash
    sed '2c\This is a changed line' file.txt
    
    ```
    
7. **Replace digits with the word "number"**:
    
    ```bash
    sed 's/[0-9]\+/number/' file.txt
    
    ```
    
8. **Replace only on the 3rd line**:
    
    ```bash
    sed '3s/old_text/new_text/' file.txt
    
    ```
    
9. **In-place editing**:
    
    ```bash
    sed -i 's/old_text/new_text/' file.txt
    
    ```
    

---

### **Summary of Common `sed` Commands**

| **Command** | **Description** | **Example** |
| --- | --- | --- |
| `s/old_text/new_text/` | Substitute `old_text` with `new_text` | `sed 's/cat/dog/' file.txt` |
| `d` | Delete lines matching a pattern | `sed '/error/d' file.txt` |
| `i\new_line` | Insert `new_line` before lines matching a pattern | `sed '/error/i\This is an error' file.txt` |
| `a\new_line` | Append `new_line` after lines matching a pattern | `sed '/error/a\Please check this error' file.txt` |
| `c\new_line` | Change lines to `new_line` | `sed '3c\New line' file.txt` |
| `-i` | Edit the file in place (without creating a new file) | `sed -i 's/cat/dog/' file.txt` |
| `-n` | Suppress automatic output, useful for selective printing | `sed -n '3p' file.txt` |
| `g` | Global replacement (replace all occurrences in a line) | `sed 's/cat/dog/g' file.txt` |

`sed` is a powerful and efficient tool for text manipulation in Unix-like systems. It is particularly useful for batch processing, scripting, and automation tasks involving text files.
