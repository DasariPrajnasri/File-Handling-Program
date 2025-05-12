# File-Handling-Program
A C program demonstrating various file operations
Here's a complete C program demonstrating file operations such as:

Creating and writing to a file

Reading from a file

Appending data to a file

Explanation:

fopen("filename", "w"): Creates or overwrites a file.

fopen("filename", "r"): Opens a file for reading.

fopen("filename", "a"): Opens a file for appending.

fgets() safely reads input with spaces.

fgetc() reads characters one by one until EOF.


⚠️ Common Reasons and Fixes:
No Write Permission in Directory

🔧 Fix: Make sure you have permission to write in the directory.

Try saving the file to a known writable location, e.g.,:

scanf("%s", filename);
// Instead, test with:
strcpy(filename, "output.txt");
File Path Issues (on Windows)


❌ File names like "con.txt", "nul.txt", or "aux.txt" are reserved.

🔧 Fix: Use names like "myfile.txt" or "data.txt".

Compiler Doesn't Have Access / Antivirus Blocking

🔧 Fix: Run the program as Administrator or move it to a different folder (like C:\Users\YourName\Documents).

Directory Doesn’t Exist (if using a path like folder/file.txt)

🔧 Fix: Ensure the directory exists.


✅ Debugging Tip
Modify this line in writeFile() to print the exact reason:

FILE *fp = fopen(filename, "w");
if (fp == NULL) {
    perror("Error opening file");  // This will print the system error
    return;
}
If the error is due to permissions or invalid path, this will tell you exactly what.


✅ Safer Version for Testing (No scanf input filename)
Try this version of main() just to confirm file creation works:

int main() {
    const char *filename = "test_output.txt";
    writeFile(filename);
    readFile(filename);
    return 0;
}
If this works, then your file I/O is fine and the issue is likely with user input or path.
 What to Expect
If the program fails to write, you'll see:

bash
Copy
Edit
Error creating/writing file: Permission denied
If the program succeeds, you’ll see:

vbnet
Copy
Edit
✅ Data written to 'test_output.txt' successfully.
🔐 File Safe Path Tip:
If you still want custom filenames, ensure they are not reserved (e.g., con.txt, nul.txt on Windows), and the directory exists.


🧪 Sample Run

Using file: test_output.txt

📁 File Operation Menu:
1. Write (create/overwrite)
2. Read file
3. Append to file
4. Exit
Enter your choice: 1
Enter data to write to the file: Hello, world!
✅ Data written to 'test_output.txt' successfully.

📁 File Operation Menu:
1. Write (create/overwrite)
2. Read file
3. Append to file
4. Exit
Enter your choice: 2
📄 Contents of 'test_output.txt':
Hello, world!

📁 File Operation Menu:
1. Write (create/overwrite)
2. Read file
3. Append to file
4. Exit
Enter your choice: 3
Enter data to append to the file: This is extra text.
✅ Data appended to 'test_output.txt' successfully.

📁 File Operation Menu:
1. Write (create/overwrite)
2. Read file
3. Append to file
4. Exit
Enter your choice: 2
📄 Contents of 'test_output.txt':
Hello, world!
This is extra text.

📁 File Operation Menu:
1. Write (create/overwrite)
2. Read file
3. Append to file
4. Exit
Enter your choice: 4
Exiting.

💡 File Content After Program Ends
If you open test_output.txt after the above session, the contents will be:

Hello, world!
This is extra text.
