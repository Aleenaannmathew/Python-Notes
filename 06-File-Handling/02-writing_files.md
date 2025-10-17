🟢 Python File Handling — Writing Files

Writing files in Python is as common as reading files. Python provides several ways to create, write, and append data to files.

🔹 1. Opening a File for Writing

To write to a file, you must open it in write mode (w) or append mode (a).

file = open("example.txt", "w")  # "w" mode = write

File Modes for Writing
Mode	Description
w	Write – creates a new file or overwrites existing file
a	Append – writes at the end of the file, preserves existing data
x	Create – creates a new file, fails if file exists
wb	Write in binary mode
ab	Append in binary mode

⚠️ Opening a file in 'w' mode overwrites the file content if it exists.

🔹 2. Writing Text to a File
2.1 Using .write()
with open("example.txt", "w") as file:
    file.write("Hello, Python!\n")
    file.write("Welcome to file handling.\n")


.write(string) → writes a string to the file.

Does not add a newline automatically, so you must include \n manually.

2.2 Using .writelines()
lines = ["Python\n", "is\n", "awesome!\n"]

with open("example.txt", "w") as file:
    file.writelines(lines)


.writelines(list_of_strings) → writes multiple lines from a list.

Does not add \n automatically, each string should include it.

🔹 3. Appending to a File
with open("example.txt", "a") as file:
    file.write("This line is appended.\n")


Appending mode 'a' keeps existing content and writes at the end.

Useful for logs or incremental writing.

🔹 4. Writing Binary Files
data = b"Python binary data"

with open("example.bin", "wb") as file:
    file.write(data)


Binary mode (wb) is used for non-text files like images or audio.

Accepts bytes objects, not strings.

🔹 5. Using print() to Write Files
with open("example.txt", "w") as file:
    print("Hello using print!", file=file)


Redirects standard output to a file.

Automatically adds a newline at the end.

🔹 6. Common Errors When Writing Files

PermissionError → no write permission for the file/directory.

FileNotFoundError → occurs in modes like 'x' if the file already exists.

TypeError → writing non-string data without converting (e.g., integers).

Example:

with open("example.txt", "w") as file:
    file.write(str(123))  # convert numbers to string before writing

🔹 7. Best Practices

Always use with open(...) → automatically closes the file.

Use 'a' mode for logs or incremental writing.

For large files, consider writing in chunks.

Handle exceptions:

try:
    with open("example.txt", "w") as file:
        file.write("Safe writing")
except PermissionError:
    print("Cannot write to file!")