
# **Pipes (`|`) and Redirection (`>`, `<`, `>>`) in Linux**  

## **1. Pipe (`|`)**  

- A **pipe (`|`)** allows the **output of one command** to be used as **input for another command**.  
- Useful for **filtering and processing data** efficiently.  

### **Example Usage**  

#### **1. Filtering Output**  
```bash
ls -l | grep ".txt"
```  
- `ls -l` lists all files.  
- `grep ".txt"` filters files containing `.txt`.  

#### **2. Counting Lines in a File**  
```bash
cat file.txt | wc -l
```  
- `cat file.txt` prints the content of `file.txt`.  
- `wc -l` counts the number of lines.  

#### **3. Sorting and Removing Duplicates**  
```bash
cat names.txt | sort | uniq
```  
- `sort` arranges lines in order.  
- `uniq` removes duplicates.  

---

## **2. Output Redirection (`>`, `>>`)**  

| Operator | Description |
|----------|------------|
| `>` | Redirects output **to a file**, **overwriting** existing content. |
| `>>` | Redirects output **to a file**, **appending** to existing content. |

### **Example Usage**  

#### **1. Overwriting a File (`>`)**  
```bash
echo "Hello, Linux!" > output.txt
```  
- Saves `"Hello, Linux!"` to `output.txt`.  
- If `output.txt` exists, it **overwrites** the file.  

#### **2. Appending to a File (`>>`)**  
```bash
echo "New Line Added" >> output.txt
```  
- Adds `"New Line Added"` **to the end** of `output.txt`.  

---

## **3. Input Redirection (`<`)**  

| Operator | Description |
|----------|------------|
| `<` | Takes input **from a file** instead of the keyboard. |

### **Example Usage**  

#### **1. Using a File as Input (`<`)**  
```bash
wc -w < file.txt
```  
- Reads `file.txt` and counts the words.  

---

## **4. Combining Pipes and Redirection**  

#### **1. Save Filtered Output to a File**  
```bash
ls -l | grep ".txt" > txt_files.txt
```  
- Filters `.txt` files and **saves the output** to `txt_files.txt`.  

#### **2. Count Number of `.log` Files and Save the Result**  
```bash
ls | grep ".log" | wc -l > log_count.txt
```  
- Counts `.log` files and **writes the count** to `log_count.txt`.  

---

## **5. Summary of Pipes and Redirection**  

| Symbol | Example | Description |
|--------|---------|------------|
| `|` | `command1 | command2` | Passes output from one command to another. |
| `>` | `command > file.txt` | Redirects output to a file (overwrites). |
| `>>` | `command >> file.txt` | Redirects output to a file (appends). |
| `<` | `command < file.txt` | Takes input from a file. |
