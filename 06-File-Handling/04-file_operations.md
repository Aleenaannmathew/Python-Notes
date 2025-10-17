🟢 Python File Operations — Detailed Explanation

Python provides several ways to interact with files and directories, such as creating, deleting, renaming, copying, moving, and checking file properties. These operations are mostly handled using the os and shutil modules.

🔹 1. Checking if a File or Directory Exists

Before performing file operations, it’s important to check whether a file or directory exists:

import os

# Check if a file exists
if os.path.exists("example.txt"):
    print("File exists")
else:
    print("File does not exist")

# Check if it is a file or directory
print(os.path.isfile("example.txt"))  # True if it is a file
print(os.path.isdir("example_dir"))   # True if it is a directory

🔹 2. Creating Files
2.1 Using open()
# Create a file in write mode
with open("new_file.txt", "w") as f:
    f.write("This is a new file.")


'w' → write mode (creates a new file or overwrites existing file)

'x' → exclusive creation (fails if file exists)

'a' → append mode (creates file if not exists)

2.2 Using os module
# Using os to create an empty file
open("another_file.txt", "a").close()

🔹 3. Creating Directories
# Single directory
os.mkdir("my_folder")

# Nested directories
os.makedirs("parent_folder/child_folder")


os.mkdir() → creates a single directory

os.makedirs() → creates nested directories

🔹 4. Renaming Files and Directories
# Rename a file
os.rename("old_file.txt", "new_file.txt")

# Rename a directory
os.rename("old_folder", "new_folder")

🔹 5. Deleting Files and Directories
5.1 Deleting Files
# Delete a file
os.remove("unwanted_file.txt")

# Alternative using pathlib
from pathlib import Path
Path("unwanted_file.txt").unlink()

5.2 Deleting Directories
# Delete empty directory
os.rmdir("empty_folder")

# Delete directory with files
import shutil
shutil.rmtree("folder_with_files")

🔹 6. Copying and Moving Files

Python’s shutil module provides robust file operations:

import shutil

# Copy a file
shutil.copy("source.txt", "destination.txt")  # Copy content
shutil.copy2("source.txt", "destination.txt") # Copy content + metadata

# Copy a directory
shutil.copytree("source_dir", "destination_dir")

# Move file or directory
shutil.move("source.txt", "new_folder/")

🔹 7. Listing Files and Directories
# List all files and directories in current folder
print(os.listdir("."))

# List files with absolute paths
for file in os.listdir("."):
    print(os.path.abspath(file))


os.listdir(path) → returns names of files/directories

os.path.abspath(path) → gives full path

🔹 8. File Information
# File size
print(os.path.getsize("example.txt"))

# Last modified time
import time
print(time.ctime(os.path.getmtime("example.txt")))

# File creation time
print(time.ctime(os.path.getctime("example.txt")))


os.path.getsize() → size in bytes

os.path.getmtime() → last modified timestamp

os.path.getctime() → creation timestamp

🔹 9. File Permissions
# Check permissions
print(os.access("example.txt", os.R_OK))  # Readable?
print(os.access("example.txt", os.W_OK))  # Writable?
print(os.access("example.txt", os.X_OK))  # Executable?


os.R_OK, os.W_OK, os.X_OK → check read, write, execute permissions

🔹 10. Safe File Operations

Always check if file exists before deleting or moving

Use try/except to handle exceptions:

try:
    os.remove("nonexistent.txt")
except FileNotFoundError:
    print("File does not exist.")


Prefer with statement for reading/writing files to ensure they are closed properly