🟢 Modules in Python — Detailed Guide

A module in Python is a file containing Python code (functions, classes, variables) that can be reused in other Python programs. Modules help in organizing code, improving readability, and avoiding duplication.

🔹 1. What is a Module?

Any Python file with a .py extension is a module.

Example:

# my_module.py

def greet(name):
    return f"Hello, {name}!"

pi = 3.14159


You can import this module in another file:

# main.py
import my_module

print(my_module.greet("Alice"))
print(my_module.pi)

🔹 2. Why Use Modules?

Code Reusability

Write once, use anywhere.

Organized Code

Break large programs into smaller manageable files.

Namespace Management

Prevent naming conflicts.

Standard Library Usage

Python provides built-in modules for common tasks.

🔹 3. Importing Modules

Python provides several ways to import modules:

3.1 Basic Import
import math
print(math.sqrt(16))

3.2 Import with Alias
import numpy as np
arr = np.array([1,2,3])

3.3 Import Specific Attributes
from math import sqrt, pi
print(sqrt(25))
print(pi)

3.4 Import All (Not Recommended)
from math import *
print(sin(0))


⚠️ Can overwrite existing names, use sparingly.

🔹 4. Built-in Modules

Python comes with many built-in modules, like:

Module	Purpose	Example
math	Mathematical functions	math.sqrt(16)
random	Generate random numbers	random.randint(1,10)
os	Interact with operating system	os.listdir('.')
sys	Access Python runtime environment	sys.version
datetime	Work with dates and times	datetime.datetime.now()
json	JSON parsing and serialization	json.dumps({"a":1})
re	Regular expressions	re.findall(r'\d+', 'abc123')
🔹 5. Creating Your Own Modules

Step 1: Create a Python file

# greetings.py
def hello(name):
    return f"Hello, {name}"


Step 2: Import and use it

# main.py
import greetings

print(greetings.hello("Alice"))


Step 3: Use __name__ for execution control

# greetings.py
def hello(name):
    return f"Hello, {name}"

if __name__ == "__main__":
    print(hello("World"))


Code inside if __name__ == "__main__" executes only when run directly, not when imported.

🔹 6. Python Module Search Path

When you import a module, Python searches for it in the following order:

Current directory

Directories in PYTHONPATH environment variable

Standard library directories

Site-packages (installed packages)

You can see the search path using:

import sys
print(sys.path)

🔹 7. Python Packages

A package is a collection of modules in a directory.

Directory must contain an __init__.py file (can be empty).

my_package/
│
├── __init__.py
├── module1.py
└── module2.py


Usage:

from my_package import module1
module1.function_name()

🔹 8. Reloading a Module

If a module is modified after import, Python does not reload automatically.

Use importlib.reload():

import my_module
from importlib import reload

reload(my_module)

🔹 9. Standard Library Modules Examples
9.1 os Module
import os
print(os.getcwd())  # Current working directory
print(os.listdir('.'))  # List files

9.2 sys Module
import sys
print(sys.version)  # Python version
print(sys.path)     # Search paths

9.3 math Module
import math
print(math.factorial(5))
print(math.ceil(3.2))

9.4 random Module
import random
print(random.randint(1, 100))
print(random.choice(['apple', 'banana']))

🔹 10. Best Practices with Modules

Keep modules focused: One module = one responsibility.

Use clear names: Avoid generic names like temp.py.

Avoid circular imports: Don’t import modules that import each other.

Use if __name__ == "__main__" for test code.

Use virtual environments for installed modules (pip, venv).