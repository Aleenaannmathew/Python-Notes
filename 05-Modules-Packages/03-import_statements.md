🟢 Python Import Statements — Detailed Guide

In Python, the import statement allows you to use code from other modules or packages. It’s a fundamental feature for code organization, reusability, and modular programming.

🔹 1. What is Importing?

Importing is bringing external Python code into your program so you can use its functions, classes, and variables.

Modules can be:

Built-in modules (e.g., math, os, sys)

Custom modules (your own .py files)

Third-party modules (installed via pip)

🔹 2. Basic Import Syntax
2.1 Import the entire module
import math

print(math.sqrt(16))  # Access function via module name


Advantage: Avoids name conflicts.

Disadvantage: Need to prefix functions with module name.

2.2 Import specific functions, classes, or variables
from math import sqrt, pi

print(sqrt(25))
print(pi)


Only imports what you need.

Avoids importing unnecessary symbols.

2.3 Import everything from a module
from math import *
print(sqrt(36))
print(pi)


Imports all public names.

Not recommended for large projects (risk of name conflicts).

2.4 Import with an alias
import numpy as np
import pandas as pd


Makes code concise and readable.

Common in third-party libraries.

🔹 3. Importing from Packages
3.1 Import a module from a package
import my_package.module1
my_package.module1.greet()

3.2 Import specific function from a module in a package
from my_package.module2 import welcome
welcome()

3.3 Import with alias from a package
from my_package.module1 import greet as g
g()

🔹 4. Relative Imports

Used in modules inside packages to import from the same package.

Single dot . – current package

Double dot .. – parent package

Triple dot ... – grandparent package

Example:

my_package/
├── __init__.py
├── module1.py
└── sub_package/
    ├── __init__.py
    └── module2.py

# Inside module2.py
from .module1 import greet        # Import from parent package
from ..module1 import greet       # Another way if nested

🔹 5. Dynamic Imports

You can import modules at runtime using importlib:

import importlib

module_name = "math"
math_module = importlib.import_module(module_name)
print(math_module.sqrt(49))


Useful for plugins or modular systems.

🔹 6. How Python Finds Modules

Python searches for modules in the following order:

Current directory – the directory from which the script is executed.

PYTHONPATH directories – environment variable paths.

Standard library directories – e.g., lib folder in Python installation.

Third-party packages – installed via pip.

You can see these paths:

import sys
print(sys.path)

🔹 7. Circular Imports

Occur when two modules import each other.

Can lead to errors like ImportError: cannot import name ....

Solutions:

Import inside functions instead of top-level.

Restructure modules to avoid circular dependency.

🔹 8. Best Practices

Use absolute imports wherever possible (clearer).

Avoid from module import * (risk of overwriting variables).

Use aliases for long module names.

Keep imports at the top of the file.

Separate standard library imports, third-party imports, and local imports:

# Standard library
import os
import sys

# Third-party
import numpy as np

# Local application
from my_package import module1