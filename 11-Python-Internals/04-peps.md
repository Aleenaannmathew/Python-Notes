🟢 PEP 8 — Python Enhancement Proposal 8 (Coding Style Guide)
🔹 1. What is PEP 8?

PEP 8 stands for Python Enhancement Proposal 8.

It is the official style guide for writing Python code.

Provides guidelines for formatting Python code to improve readability and maintainability.

Helps developers write consistent code in projects with multiple contributors.

🔹 2. Importance of PEP 8

Readability: Makes code easier to read and understand.

Consistency: Standardizes code style across Python projects.

Collaboration: Helps teams maintain a uniform codebase.

Professionalism: Writing code according to PEP 8 is considered best practice.

🔹 3. Key Guidelines of PEP 8
3.1 Indentation

Use 4 spaces per indentation level (not tabs).

Example:

def greet(name):
    print(f"Hello, {name}")

3.2 Maximum Line Length

Limit lines to 79 characters (for code) and 72 characters (for docstrings/comments).

# Good
message = "This is a short message that fits within 79 characters."

# Avoid
message = "This is a very long message that exceeds seventy-nine characters which is discouraged in PEP8."

3.3 Blank Lines

Top-level functions/classes: 2 blank lines before.

Methods inside classes: 1 blank line before.

class MyClass:
    def method_one(self):
        pass

    def method_two(self):
        pass

3.4 Imports

Imports should be on separate lines.

Order: Standard library → Third-party → Local imports.

Example:

import os
import sys

import requests

from mymodule import helper

3.5 Naming Conventions
Type	Convention	Example
Variables/functions	lowercase_with_underscores	user_name, calculate_sum()
Constants	UPPERCASE_WITH_UNDERSCORES	PI = 3.14
Classes	CapitalizedWords (PascalCase)	MyClass
Modules	lowercase	mymodule.py
Packages	lowercase	mypackage/
3.6 Whitespace in Expressions

Avoid extra spaces:

# Good
x = 5
y = x + 2

# Bad
x    = 5
y = x+2


Do not put spaces inside brackets, braces, or parentheses:

# Good
my_list = [1, 2, 3]

# Bad
my_list = [ 1, 2, 3 ]

3.7 Comments

Use comments to explain why code exists, not what it does.

Inline comments: use # with at least 2 spaces before.

x = x + 1  # Increment x by 1

3.8 Docstrings

Use triple quotes for docstrings.

Describe function/class/module purpose.

def greet(name):
    """
    Greets the user by name.
    
    Parameters:
    name (str): Name of the user
    """
    print(f"Hello, {name}")

3.9 Avoid Trailing Whitespace

No spaces at the end of lines.

3.10 Use is and is not for comparisons with None
# Good
if value is None:
    pass

# Bad
if value == None:
    pass

🔹 4. Tools to Check PEP 8 Compliance

pycodestyle: Command-line tool for checking PEP 8 violations.

flake8: Linter for style and errors.

black: Autoformatter that formats Python code according to PEP 8.

IDE Integration: PyCharm, VS Code, and other editors can show PEP 8 warnings.

🔹 5. Summary

PEP 8 defines how Python code should be formatted.

Focuses on indentation, naming, spacing, line length, comments, and imports.

Following PEP 8 improves readability, consistency, and collaboration in Python projects.