🟢 Python File Handling — Context Managers

Context managers in Python provide a clean, safe, and efficient way to handle resources like files. They ensure that resources are properly acquired and released, even if errors occur.

🔹 1. What is a Context Manager?

A context manager is a Python construct that automatically manages setup and teardown operations.

In file handling, it opens and closes the file automatically:

with open("example.txt", "r") as file:
    content = file.read()


with → starts the context

file → file object

After the block, file is automatically closed, no need for file.close().

✅ Using context managers prevents resource leaks and ensures safe file handling.

🔹 2. Why Use Context Managers for Files?

Automatically closes files, even on exceptions.

Reduces boilerplate code: no need for try/finally.

Makes code cleaner and more readable.

Without context manager:

file = open("example.txt", "r")
try:
    content = file.read()
finally:
    file.close()


With context manager:

with open("example.txt", "r") as file:
    content = file.read()


The with statement internally handles try/finally.

🔹 3. File Handling Modes with Context Managers

You can use any file mode with with:

# Writing
with open("example.txt", "w") as f:
    f.write("Hello, World!")

# Appending
with open("example.txt", "a") as f:
    f.write("\nAppending new line")

# Reading
with open("example.txt", "r") as f:
    print(f.read())


✅ No need to explicitly call f.close(); it's automatic.

🔹 4. Multiple Files in One Context

You can manage multiple files in a single with statement:

with open("input.txt", "r") as infile, open("output.txt", "w") as outfile:
    for line in infile:
        outfile.write(line.upper())


Automatically closes both files after the block.

🔹 5. Using contextlib for Custom Context Managers

Python provides the contextlib module to create custom context managers.

5.1 Using @contextmanager
from contextlib import contextmanager

@contextmanager
def open_file(file_name, mode):
    f = open(file_name, mode)
    try:
        yield f
    finally:
        f.close()

with open_file("example.txt", "w") as file:
    file.write("Custom context manager")


yield → provides the resource to the with block

finally → ensures resource cleanup

5.2 Using a Class
class FileManager:
    def __init__(self, filename, mode):
        self.filename = filename
        self.mode = mode

    def __enter__(self):
        self.file = open(self.filename, self.mode)
        return self.file

    def __exit__(self, exc_type, exc_val, exc_tb):
        self.file.close()

with FileManager("example.txt", "w") as f:
    f.write("Using class-based context manager")


__enter__ → runs at the start of with block

__exit__ → runs at the end of with block, handles exceptions if any

🔹 6. Advantages of Context Managers

Automatic resource management

Cleaner, readable code

Reduces errors like forgetting to close a file

Works with any resource: files, network connections, database connections, locks, etc.

🔹 7. Exceptions Handling in Context Managers

__exit__ can handle exceptions.

class FileManager:
    def __init__(self, filename, mode):
        self.filename = filename
        self.mode = mode

    def __enter__(self):
        self.file = open(self.filename, self.mode)
        return self.file

    def __exit__(self, exc_type, exc_value, traceback):
        self.file.close()
        if exc_type:
            print(f"An exception occurred: {exc_value}")
        return True  # Suppresses exception


Returning True → suppresses exception

Returning False → exception propagates normally