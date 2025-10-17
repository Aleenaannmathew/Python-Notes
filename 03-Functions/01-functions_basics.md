🟢 Functions in Python – Basics
🧠 What is a Function?

A function is a block of reusable code that performs a specific task.

Functions help in modularity, code reusability, and readability.

Python provides built-in functions and also allows you to define user-defined functions.

🔹 1. Function Syntax
def function_name(parameters):
    """
    Docstring (optional): Explain what the function does
    """
    # Function body
    statements
    return value  # optional


Example:

def greet(name):
    """Function to greet a person"""
    return f"Hello, {name}!"

print(greet("Alice"))  # Hello, Alice!

🔹 2. Calling a Function

Functions are called using their name and parentheses.

If the function has parameters, pass arguments.

def add(a, b):
    return a + b

result = add(5, 10)
print(result)  # 15

🔹 3. Types of Functions
a) Built-in Functions

Already provided by Python.

Examples: print(), len(), sum(), max(), min(), type(), range().

numbers = [1, 2, 3, 4, 5]
print(sum(numbers))  # 15

b) User-Defined Functions

Created by the user to perform a specific task.

def square(n):
    return n ** 2
print(square(4))  # 16

🔹 4. Function Arguments
a) Positional Arguments
def multiply(a, b):
    return a * b
print(multiply(2, 3))  # 6

b) Keyword Arguments
def greet(name, msg):
    return f"{msg}, {name}!"
print(greet(msg="Hi", name="Alice"))  # Hi, Alice!

c) Default Arguments
def greet(name, msg="Hello"):
    return f"{msg}, {name}!"
print(greet("Alice"))         # Hello, Alice!
print(greet("Bob", "Hi"))     # Hi, Bob!

d) Variable-Length Arguments
i) *args – Positional variable-length
def add(*args):
    return sum(args)
print(add(1, 2, 3, 4))  # 10

ii) **kwargs – Keyword variable-length
def show_info(**kwargs):
    for key, value in kwargs.items():
        print(f"{key}: {value}")
show_info(name="Alice", age=25)

🔹 5. Return Statement

Functions return a value using return.

If no return is specified, function returns None.

def square(n):
    return n**2

result = square(5)
print(result)  # 25

🔹 6. Function Scope

Local Scope: Variables defined inside a function.

Global Scope: Variables defined outside all functions.

x = 10  # global

def func():
    y = 5  # local
    print(x, y)

func()       # 10 5
print(y)     # Error: y is not defined


Use global keyword to modify a global variable inside a function:

x = 10
def change_global():
    global x
    x = 20
change_global()
print(x)  # 20

🔹 7. Lambda Functions (Preview)

Anonymous functions using lambda.

Can take any number of arguments but only one expression.

square = lambda x: x**2
print(square(5))  # 25

add = lambda a, b: a + b
print(add(2, 3))  # 5


Full details on lambda functions will be in 02-lambda_functions.md.

🔹 8. Recursion

Function calling itself is called recursion.

Must have a base case to stop recursion.

def factorial(n):
    if n == 0:
        return 1
    return n * factorial(n-1)

print(factorial(5))  # 120

🔹 9. Docstrings

Triple quotes """ """ are used to document the function.

Can access docstring via .__doc__.

def greet(name):
    """Greet a person with their name"""
    return f"Hello, {name}"

print(greet.__doc__)  # Greet a person with their name

🔹 10. Advantages of Functions

Code Reusability – write once, use multiple times.

Modular Programming – divide code into logical blocks.

Readability – makes code easier to understand.

Debugging – easier to test individual parts of code.

