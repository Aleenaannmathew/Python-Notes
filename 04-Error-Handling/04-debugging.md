🟢 Debugging in Python — Detailed Guide

Debugging is the process of identifying, analyzing, and fixing errors or bugs in your code. Python provides multiple tools and techniques for debugging, ranging from print statements to sophisticated interactive debuggers.

🔹 1. Types of Errors in Python

Before debugging, you must know the types of errors you might encounter:

Syntax Errors

Violations of Python’s grammar rules.

Example:

print("Hello World"


Output: SyntaxError: unexpected EOF while parsing

Runtime Errors (Exceptions)

Errors that occur while the program is running.

Example:

x = 10 / 0


Output: ZeroDivisionError: division by zero

Logical Errors

Program runs without crashing but produces incorrect results.

Example:

total = 10 + 20 * 2  # intended (10+20)*2

🔹 2. Basic Debugging Techniques
2.1 Using Print Statements

The simplest way to inspect variable values and program flow.

x = 5
y = 0
print("Before division")
print("x:", x, "y:", y)
result = x / y  # Runtime error


Limitations:

Can clutter the code.

Not ideal for large projects.

2.2 Using Assertions

Assertions are sanity checks in the code.

x = -10
assert x >= 0, "x must be non-negative"


If the condition fails, an AssertionError is raised.

Useful during development to catch logical errors early.

2.3 Using Logging

Better than print statements for real-world projects.

Can log messages at different levels: DEBUG, INFO, WARNING, ERROR, CRITICAL.

import logging

logging.basicConfig(level=logging.DEBUG)
x = 5
logging.debug(f"x value: {x}")


Advantages:

Can disable logging easily.

Can save logs to files.

Helps track application flow without breaking execution.

🔹 3. Python Debuggers

Python has built-in and external debuggers to inspect code execution step by step.

3.1 Built-in Debugger: pdb

Python's interactive debugger.

Allows stepping through code, inspecting variables, and evaluating expressions.

Example:
import pdb

def divide(a, b):
    pdb.set_trace()  # Execution stops here
    return a / b

result = divide(10, 0)

Common pdb Commands:
Command	Description
l	List source code around current line
n	Execute next line
s	Step into function call
c	Continue execution until next breakpoint
p var	Print value of variable
q	Quit debugger
3.2 Using IDE Debuggers (VSCode, PyCharm)

Modern IDEs provide graphical debugging tools:

Set breakpoints with a click.

Step over, step into, step out.

Inspect variables and call stack.

Evaluate expressions on the fly.

Example in VSCode:

Open your Python file.

Click next to the line number to set a breakpoint.

Press F5 to start debugging.

Use the Debug Panel to step, continue, or inspect variables.

3.3 Exception Traceback Analysis

Tracebacks show where an error occurred, including file name, line number, and call stack.

Example:

def func():
    return 1 / 0

func()


Output:

Traceback (most recent call last):
  File "example.py", line 4, in <module>
    func()
  File "example.py", line 2, in func
    return 1 / 0
ZeroDivisionError: division by zero


Reading tracebacks carefully is the first step in debugging.

🔹 4. Advanced Debugging Techniques
4.1 Using breakpoint() (Python 3.7+)

Replaces pdb.set_trace().

Example:

def add(a, b):
    breakpoint()  # Pauses execution here
    return a + b

add(5, 7)

4.2 Inspecting Objects

dir(): lists attributes/methods of an object.

type(): shows the type of an object.

Example:

x = [1, 2, 3]
print(dir(x))
print(type(x))

4.3 Using try-except for Debugging

Catch exceptions to prevent program crash and print debug info:

try:
    result = 10 / 0
except Exception as e:
    print(f"Error occurred: {e}")

4.4 Unit Testing as Debugging

Writing tests can catch errors early.

Modules: unittest, pytest

import unittest

def add(a, b):
    return a + b

class TestMath(unittest.TestCase):
    def test_add(self):
        self.assertEqual(add(2,3), 5)

unittest.main()

🔹 5. Best Practices for Debugging

Reproduce the problem consistently before trying fixes.

Read tracebacks carefully.

Use logging instead of print in production code.

Break the problem into smaller chunks.

Check variable types and values at each step.

Write tests to prevent recurring bugs.

Keep debugging statements temporary, clean up afterward.