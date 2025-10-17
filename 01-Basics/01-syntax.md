# Python Syntax

Python syntax defines the **set of rules** that determine how a Python program is written and interpreted.

---

## 🐍 1. First Python Program

Every Python program file has the extension `.py`.  
Let’s start with the classic example:

```python
print("Hello, World!")
Output:
Copy code
Hello, World!
✅ print() is a built-in function used to display text or output.

📄 2. Comments in Python
Comments are used to explain code and are ignored by the interpreter.

Single-line comment:
python
Copy code
# This is a single-line comment
Multi-line comment:
python
Copy code
"""
This is a multi-line comment
spanning across multiple lines
"""
Or:

python
Copy code
'''
This is also a valid multi-line comment
'''
🔠 3. Indentation
Python uses indentation (spaces or tabs) to define code blocks.
Unlike many languages that use { }, Python relies on indentation.

python
Copy code
if True:
    print("This is indented properly")   # Correct
🚫 Incorrect:

python
Copy code
if True:
print("This will cause an IndentationError")
✅ Recommended: Use 4 spaces per indentation level.

🧱 4. Statements and Line Continuation
Each line of code is typically one statement.
You can use \ to continue a statement on the next line.

python
Copy code
x = 10 + 20 + 30 + \
    40 + 50
print(x)
Or use parentheses for automatic line continuation:

python
Copy code
numbers = (
    1 + 2 +
    3 + 4
)
💬 5. Printing and Output Formatting
Use the print() function to display results.

python
Copy code
name = "Alice"
age = 25
print("Name:", name, "Age:", age)
Using f-strings (Python 3.6+)
python
Copy code
print(f"My name is {name} and I am {age} years old.")
🔤 6. Case Sensitivity
Python is case-sensitive.

python
Copy code
name = "Alice"
Name = "Bob"
print(name)   # Alice
print(Name)   # Bob
⚠️ name and Name are treated as two different variables.

🔁 7. Multiple Statements on One Line
Multiple statements can be written on one line using semicolons ;
(but not recommended for readability).

python
Copy code
x = 5; y = 10; print(x + y)
📦 8. Multiple Assignments
You can assign values to multiple variables in one line.

python
Copy code
a, b, c = 10, 20, 30
print(a, b, c)
Or assign the same value to multiple variables:

python
Copy code
x = y = z = 50
🧮 9. Keywords in Python
Keywords are reserved words with special meaning.

python
Copy code
import keyword
print(keyword.kwlist)
Example output (Python 3.11+):

bash
Copy code
['False', 'None', 'True', 'and', 'as', 'assert', 'async', 'await', 
 'break', 'class', 'continue', 'def', 'del', 'elif', 'else', 'except', 
 'finally', 'for', 'from', 'global', 'if', 'import', 'in', 'is', 
 'lambda', 'nonlocal', 'not', 'or', 'pass', 'raise', 'return', 
 'try', 'while', 'with', 'yield']
📚 10. Input from User
Use the input() function to take input.

python
Copy code
name = input("Enter your name: ")
print("Hello,", name)
By default, input is taken as a string.

🧩 11. Code Blocks and Scope
Indentation determines the scope of a block:

python
Copy code
for i in range(3):
    print("Inside loop:", i)
print("Outside loop")
Output:

arduino
Copy code
Inside loop: 0
Inside loop: 1
Inside loop: 2
Outside loop
⚙️ 12. Docstrings
Used to describe functions, classes, or modules.

python
Copy code
def greet(name):
    """This function greets the person passed as a parameter."""
    print("Hello,", name)
Access it using:

python
Copy code
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