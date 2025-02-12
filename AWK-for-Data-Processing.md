# **🖥️ AWK Command Guide 📜** #

AWK is a powerful text-processing tool used for pattern scanning and data manipulation. It is widely used for analyzing structured text, extracting information, and automating reports.

## **📌 What is AWK?** ##

AWK is a programming language designed for text processing and is used mainly in Unix/Linux environments. It allows users to:

✔️ Search and filter text 📑

✔️ Process and manipulate structured data 📊

✔️ Generate reports automatically 📜

## 🚀 Getting Started with AWK
AWK processes text line by line and operates on fields within each line. The default delimiter is whitespace, but you can specify custom delimiters.


 **awk 'pattern { action }' file.txt** 

👉 pattern: Defines when the action should execute.

👉 action: Specifies what AWK should do with the matched text.

## 🌟 AWK Command Basics ##


1️⃣    Print Specific Columns


       awk '{print $1, $3}' file.txt


✨ Prints the 1st and 3rd columns from file.txt.


2️⃣    Filter Rows Based on a Condition


       awk '$3 > 50' file.txt


✅ Prints rows where the 3rd column is greater than 50.


3️⃣    Using a Delimiter (CSV Files)


      awk -F, '{print $1, $2}' file.csv


📌 Specifies a comma (,) as the delimiter and prints the 1st and 2nd columns.


4️⃣    Print Line Numbers


      awk '{print NR, $0}' file.txt


📄 Prints each line with its line number (NR).


5️⃣    Count Number of Lines


      awk 'END {print NR}' file.txt


🔢 Prints the total number of lines in the file.


6️⃣    Find Sum of a Column


      awk '{sum += $2} END {print sum}' file.txt


➕ Computes the sum of the 2nd column.


7️⃣    Find Average of a Column


     awk '{sum += $2; count++} END {print sum/count}' file.txt


📊 Computes the average of the 2nd column.


8️⃣    Replace a Word in a File


    awk '{gsub(/old/, "new"); print}' file.txt


🔄 Replaces occurrences of "old" with "new".


9️⃣    Print Only Matching Lines


    awk '/pattern/' file.txt


🔍 Prints lines that contain "pattern".


🔟    Execute Commands on Matching Lines


     awk '/error/ {print $0 > "errors.log"}' file.txt


🚨 Redirects lines containing "error" to errors.log.





## 🎯 Why Use AWK? ##

✅ Lightweight and built-in on most Linux/Unix systems

✅ Powerful for data extraction and formatting

✅ Ideal for log file analysis, reports, and data transformation


## 📚 Advanced AWK Features ##
🔥 Using Variables:

       awk '{ sum += $3 } END { print "Total:", sum }' data.txt
       
✔️ Computes the sum of the third column in data.txt.


🔥 Using Regular Expressions:


        awk '/error/ {print $0}' logfile.txt
        
✔️ Prints lines containing the word "error" in a log file.


🔥 Formatted Output:

        awk '{printf "User: %s, Age: %d\n", $1, $2}' users.txt
        
✔️ Formats output in a structured way.


## 🌟 Conclusion ##

AWK is an essential tool for text processing, data manipulation, and automation. It’s widely used by system administrators, data analysts, and developers.
