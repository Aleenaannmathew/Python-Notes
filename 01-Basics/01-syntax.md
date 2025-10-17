# Python Syntax

Python syntax defines the **set of rules** that determine how a Python program is written and interpreted.

---

## 🐍 1. First Python Program

Every Python program file has the extension `.py`.  
Let’s start with the classic example:

```python
print("Hello, World!")
Output:

Hello, World!
✅ print() is a built-in function used to display text or output.

📄 2. Comments in Python
Comments are used to explain code and are ignored by the interpreter.

Single-line comment:

# This is a single-line comment
Multi-line comment:

"""
This is a multi-line comment
spanning across multiple lines
"""
Or:


'''
This is also a valid multi-line comment
'''
🔠 3. Indentation
Python uses indentation (spaces or tabs) to define code blocks.
Unlike many languages that use { }, Python relies on indentation.


if True:
    print("This is indented properly")   # Correct
🚫 Incorrect:


if True:
print("This will cause an IndentationError")
✅ Recommended: Use 4 spaces per indentation level.

🧱 4. Statements and Line Continuation
Each line of code is typically one statement.
You can use \ to continue a statement on the next line.


x = 10 + 20 + 30 + \
    40 + 50
print(x)
Or use parentheses for automatic line continuation:


numbers = (
    1 + 2 +
    3 + 4
)
💬 5. Printing and Output Formatting
Use the print() function to display results.


name = "Alice"
age = 25
print("Name:", name, "Age:", age)
Using f-strings (Python 3.6+)

print(f"My name is {name} and I am {age} years old.")
🔤 6. Case Sensitivity
Python is case-sensitive.

name = "Alice"
Name = "Bob"
print(name)   # Alice
print(Name)   # Bob
⚠️ name and Name are treated as two different variables.

🔁 7. Multiple Statements on One Line
Multiple statements can be written on one line using semicolons ;
(but not recommended for readability).


x = 5; y = 10; print(x + y)
📦 8. Multiple Assignments
You can assign values to multiple variables in one line.


a, b, c = 10, 20, 30
print(a, b, c)
Or assign the same value to multiple variables:


x = y = z = 50
🧮 9. Keywords in Python
Keywords are reserved words with special meaning.


import keyword
print(keyword.kwlist)
Example output (Python 3.11+):



['False', 'None', 'True', 'and', 'as', 'assert', 'async', 'await', 
 'break', 'class', 'continue', 'def', 'del', 'elif', 'else', 'except', 
 'finally', 'for', 'from', 'global', 'if', 'import', 'in', 'is', 
 'lambda', 'nonlocal', 'not', 'or', 'pass', 'raise', 'return', 
 'try', 'while', 'with', 'yield']
📚 10. Input from User
Use the input() function to take input.


name = input("Enter your name: ")
print("Hello,", name)
By default, input is taken as a string.

🧩 11. Code Blocks and Scope
Indentation determines the scope of a block:



for i in range(3):
    print("Inside loop:", i)
print("Outside loop")
Output:

Inside loop: 0
Inside loop: 1
Inside loop: 2
Outside loop
⚙️ 12. Docstrings
Used to describe functions, classes, or modules.

def greet(name):
    """This function greets the person passed as a parameter."""
    print("Hello,", name)
Access it using:
print(greet.__doc__)


🧾 Summary
Concept	Description
Comments	Explain code, ignored by interpreter
Indentation	Defines blocks instead of braces {}
Line Continuation	Use \ or parentheses
Case Sensitivity	Variables are case-sensitive
Multiple Assignments	Assign multiple variables in one line
Input	Use input()
Docstrings	Used to document code