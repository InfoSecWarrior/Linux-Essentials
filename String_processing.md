# Linux String Processing Commands

Welcome to the **Linux String Processing** repository! This repository provides a comprehensive guide on various Linux command-line tools for handling text processing efficiently. The commands covered include:

- `head` - Display the beginning lines of a file
- `tail` - Display the ending lines of a file
- `grep` - Search for patterns in a file
- `awk` - Process and analyze text data
- `sed` - Perform text transformations and substitutions

## Table of Contents
- [1. Head Command](#1-head-command)
- [2. Tail Command](#2-tail-command)
- [3. Grep Command](#3-grep-command)
- [4. Awk Command](#4-awk-command)
- [5. Sed Command](#5-sed-command)
- [6. Additional Resources](#6-additional-resources)

---

## 1. Head Command
**Purpose:** Displays the first few lines of a file. Useful for previewing file contents without opening the entire file.

### Syntax:
```sh
head -n <number_of_lines> <filename>
```

### Example:
```sh
head -n 5 sample.txt
```
*Displays the first 5 lines of `sample.txt`.*

### Additional Options:
- `-c <bytes>`: Display the first specified number of bytes
- `-q`: Suppress headers when multiple files are used

---

## 2. Tail Command
**Purpose:** Displays the last few lines of a file. Commonly used to monitor log files in real-time.

### Syntax:
```sh
tail -n <number_of_lines> <filename>
```

### Example:
```sh
tail -n 5 sample.txt
```
*Displays the last 5 lines of `sample.txt`.*

### Additional Options:
- `-f`: Follow the file and display new lines as they are added (useful for logs)
- `-c <bytes>`: Display the last specified number of bytes

---

## 3. Grep Command
**Purpose:** Searches for a pattern in a file and displays matching lines.

### Syntax:
```sh
grep '<pattern>' <filename>
```

### Example:
```sh
grep 'error' log.txt
```
*Finds and displays lines containing 'error' in `log.txt`.*

### Additional Options:
- `-i`: Ignore case when searching
- `-v`: Invert match (show lines that do NOT match)
- `-c`: Count occurrences
- `-r`: Search recursively in directories
- `-w`: Match whole words only

---

## 4. Awk Command
**Purpose:** A powerful text-processing tool used for pattern scanning and processing. It can manipulate and analyze structured data efficiently.

### Syntax:
```sh
awk '{ action }' <filename>
```

### Example:
```sh
awk '{print $1, $3}' data.txt
```
*Prints the first and third column from `data.txt`.*

### Common Awk Patterns:
- `NR`: Current line number
- `NF`: Number of fields in a line
- `{print $0}`: Prints entire line
- `BEGIN {}`: Actions to perform before processing
- `END {}`: Actions to perform after processing

### Example:
```sh
awk 'BEGIN {print "Start Processing"} {print $0} END {print "End Processing"}' data.txt
```
*Prints each line with a header and footer message.*

---

## 5. Sed Command
**Purpose:** Stream editor for filtering and transforming text. It allows performing text replacement, deletion, and modification in files.

### Syntax:
```sh
sed 's/<old>/<new>/g' <filename>
```

### Example:
```sh
sed 's/apple/orange/g' fruits.txt
```
*Replaces all occurrences of 'apple' with 'orange' in `fruits.txt`.*

### Additional Options:
- `-i`: Edit file in place without outputting to a new file
- `-n`: Suppress default output and print only specified lines
- `/pattern/p`: Print lines matching a pattern

### Example:
```sh
sed -n '/error/p' log.txt
```
*Prints only lines that contain 'error' in `log.txt`.*

---

## 6. Additional Resources
If you want to explore more about text processing in Linux, check out these resources:
- [GNU Grep Manual](https://www.gnu.org/software/grep/manual/)
- [Awk User Guide](https://www.gnu.org/software/gawk/manual/)
- [Sed Tutorial](https://www.grymoire.com/Unix/Sed.html)

---

### 📌 Want to contribute?
Feel free to fork this repository and submit pull requests with improvements or additional examples!

### 📜 License
This project is licensed under the MIT License.
