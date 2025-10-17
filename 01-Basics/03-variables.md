🧮 Python Variables

A variable in Python is a name that refers to a value stored in memory.
It acts as a container for data — you can store, update, and use it throughout your program.

⚙️ What Is a Variable?

In Python:

You don’t need to declare the type of a variable explicitly.

The data type is inferred at runtime.

A variable can change its type during execution (Python is dynamically typed).

x = 10          # integer
x = "Hello"     # now x refers to a string

🪶 Variable Declaration

A variable is created when you assign a value to it using the = operator.

name = "Aleena"
age = 21
price = 99.99


You can assign multiple variables in one line:

a, b, c = 10, 20, 30


Or assign the same value to multiple variables:

x = y = z = 0

🧠 Variable Naming Rules

✅ Allowed:

Must start with a letter or underscore (_).

Can contain letters, digits, and underscores.

Are case-sensitive (Age, age, and AGE are different).

❌ Not Allowed:

Cannot start with a digit.

Cannot use reserved keywords as variable names (like class, for, if, etc.).

_name = "Aleena"     # ✅ valid
name1 = "John"       # ✅ valid
1name = "Invalid"    # ❌ invalid
for = 5              # ❌ invalid (keyword)

🔠 Naming Conventions (PEP 8)
Style	Example	Usage
snake_case	user_name, total_amount	✅ Recommended for variables and functions
UPPER_CASE	PI = 3.14	Used for constants
camelCase	userName	Sometimes used in classes or JS-style code
_leading_underscore	_internal_var	Used for internal/private variables
🧾 Dynamic Typing Example

Python allows reassignment with different data types:

x = 10
print(type(x))   # <class 'int'>

x = "Python"
print(type(x))   # <class 'str'>

💡 Variable Casting

You can change (cast) the type of a variable manually:

a = int(5.8)       # 5
b = float("10")    # 10.0
c = str(25)        # "25"

📍 Constants

Python doesn’t have a true constant type,
but by convention, variables written in UPPERCASE are treated as constants.

PI = 3.14159
GRAVITY = 9.8

🔄 Memory Reference

In Python, variables are references to objects in memory, not fixed memory locations like in C.

x = [1, 2, 3]
y = x      # both point to the same list
y.append(4)
print(x)   # [1, 2, 3, 4]


To create a copy, use:

z = x.copy()


🧠 Visual Diagram
+-----------------+       +------------------+
| Variable Name   | ---> |   Memory Object  |
+-----------------+       +------------------+
| x               | ----> | [1, 2, 3, 4]     |
| y               | ----> | [1, 2, 3, 4]     |
| z               | ----> | [1, 2, 3]        |
+-----------------+       +------------------+


Explanation:

x and y point to the same object (shared reference).

z points to a different copy.

🧩 id() and type()

id() → returns the unique memory address of an object.

type() → returns the data type of the variable.

x = 10
print(id(x))     # e.g., 140711524123456
print(type(x))   # <class 'int'>

🧮 Example Summary
# variable assignment
name = "Aleena"
age = 21
height = 5.4

# printing variables
print("Name:", name)
print("Age:", age)
print("Height:", height)


Output:

Name: Aleena
Age: 21
Height: 5.4
