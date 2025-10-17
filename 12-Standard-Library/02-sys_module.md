🟢 Python os Module — Detailed Explanation

The os module in Python provides a way to interact with the operating system. It allows you to perform file, directory, and system-related operations in a platform-independent manner (works on Windows, Linux, macOS).

🔹 1. Importing os Module
import os


Once imported, you can access all its functions and constants.

🔹 2. Working with Directories
a) Get Current Working Directory
cwd = os.getcwd()
print("Current Working Directory:", cwd)

b) Change Directory
os.chdir("/path/to/directory")
print("Changed Directory:", os.getcwd())

c) List Directory Contents
contents = os.listdir(".")
print("Directory Contents:", contents)

d) Create Directory
os.mkdir("new_folder")         # Single directory
os.makedirs("folder1/folder2") # Nested directories

e) Remove Directory
os.rmdir("new_folder")          # Remove empty folder
os.removedirs("folder1/folder2") # Remove nested empty directories

🔹 3. Working with Files
a) Check File/Directory Existence
print(os.path.exists("example.txt"))  # True if exists
print(os.path.isfile("example.txt"))  # True if file
print(os.path.isdir("folder"))        # True if directory

b) Rename Files or Directories
os.rename("old_name.txt", "new_name.txt")

c) Remove Files
os.remove("example.txt")

🔹 4. Path Manipulations

The os.path submodule helps handle file paths reliably:

import os

path = "/home/user/file.txt"

print(os.path.basename(path))   # file.txt
print(os.path.dirname(path))    # /home/user
print(os.path.join("/home/user", "file.txt"))  # /home/user/file.txt
print(os.path.split(path))      # ('/home/user', 'file.txt')
print(os.path.exists(path))     # True/False
print(os.path.abspath("file.txt")) # Absolute path

🔹 5. Environment Variables

Access and modify environment variables using os.environ:

# Get environment variable
home = os.environ.get("HOME")
print("Home directory:", home)

# Set environment variable
os.environ["MY_VAR"] = "123"

# Delete environment variable
del os.environ["MY_VAR"]

🔹 6. Executing System Commands
os.system("echo Hello World")  # Executes shell command


⚠ Note: os.system runs commands directly; prefer subprocess module for safer execution.

🔹 7. File Permissions and Status
# Get file status
status = os.stat("example.txt")
print(status)

# Check permissions
print(os.access("example.txt", os.R_OK))  # Readable
print(os.access("example.txt", os.W_OK))  # Writable
print(os.access("example.txt", os.X_OK))  # Executable

🔹 8. Miscellaneous Useful Functions
Function	Purpose
os.name	Returns OS name (posix, nt, java)
os.sep	Directory separator (/ or \)
os.pathsep	Path separator (: on Linux, ; on Windows)
os.linesep	Line separator (\n, \r\n)
os.getpid()	Current process ID
os.urandom(n)	Returns n random bytes (useful for cryptography)
🔹 9. Best Practices

Use os.path.join() instead of manually joining paths with / or \.

Always check if a file or directory exists before performing operations.

For executing system commands, prefer the subprocess module for better security.

Use with open(...) as f: for file operations to avoid leaving files open.

✅ Summary:
The os module is essential for file, directory, and system interactions in Python. It provides a platform-independent interface for performing common tasks like creating directories, listing files, checking paths, managing environment variables, and executing system commands.