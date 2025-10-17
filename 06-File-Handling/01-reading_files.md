🟢 Python File Handling — Reading Files

In Python, reading files is one of the most common tasks. Python provides several ways to open, read, and handle files safely.

🔹 1. Opening a File

To read a file, you must open it first using the built-in open() function.

file = open("example.txt", "r")  # "r" mode = read

Syntax:
open(file_path, mode='r', buffering=-1, encoding=None)


file_path → path to the file

mode → mode to open the file (r, rb, rt, etc.)

buffering → buffering policy (default = system default)

encoding → encoding type, e.g., 'utf-8'

🔹 2. File Modes
Mode	Description
r	Read (default) – file must exist
rb	Read in binary mode
rt	Read in text mode (default)

⚠️ Important: Opening a file in 'r' mode will raise FileNotFoundError if the file does not exist.

🔹 3. Reading the Entire File
with open("example.txt", "r") as file:
    content = file.read()
    print(content)


.read() → Reads the entire content of the file into a single string.

Using with is recommended for automatic resource management (closes file automatically).

🔹 4. Reading Line by Line
4.1 Using readline()
with open("example.txt", "r") as file:
    line1 = file.readline()
    line2 = file.readline()
    print(line1)
    print(line2)


.readline() reads one line at a time.

Successive calls return the next line until end of file (EOF).

4.2 Using readlines()
with open("example.txt", "r") as file:
    lines = file.readlines()
    print(lines)


.readlines() returns a list of all lines.

Each line ends with a newline character \n.

4.3 Iterating Over the File Object
with open("example.txt", "r") as file:
    for line in file:
        print(line.strip())


Efficient for large files.

.strip() removes trailing \n characters.

🔹 5. Reading a Specific Number of Characters
with open("example.txt", "r") as file:
    content = file.read(10)  # read first 10 characters
    print(content)


.read(size) → Reads up to size characters.

Useful for large files or chunked reading.

🔹 6. Reading Binary Files
with open("image.png", "rb") as file:
    content = file.read()
    print(type(content))  # <class 'bytes'>


Binary mode (rb) returns bytes instead of string.

Useful for images, videos, or any non-text files.

🔹 7. Common Errors When Reading Files

FileNotFoundError → File does not exist.

PermissionError → No permission to read the file.

UnicodeDecodeError → Wrong encoding used to read the file.

Example:

with open("example.txt", "r", encoding="utf-8") as file:
    content = file.read()

🔹 8. Best Practices

Always use with open(...) → ensures automatic file closure.

Prefer iterating the file over .readlines() for large files.

Handle exceptions with try-except if the file may not exist:

try:
    with open("example.txt", "r") as file:
        print(file.read())
except FileNotFoundError:
    print("File not found!")