🟢 Python Error Handling and Exceptions — In Depth
🧠 What is an Exception?

An exception is an event that occurs during the execution of a program that disrupts the normal flow of instructions.

In simpler words: Python raises exceptions when something goes wrong.

If not handled, the program stops execution and shows a traceback.

🔹 1. Types of Errors in Python
a) Syntax Errors (Compile-time errors)

Errors in the structure of code.

# SyntaxError example
if True
    print("Hello")  # ❌ Missing colon


Output:

SyntaxError: expected ':'

b) Exceptions (Run-time errors)

Errors that occur during execution. Examples:

Exception	Meaning
ZeroDivisionError	Dividing by zero
NameError	Using undefined variable
TypeError	Wrong data type operation
IndexError	List index out of range
KeyError	Accessing non-existing dictionary key
ValueError	Invalid value passed
FileNotFoundError	File not found in system
print(5 / 0)  # ❌ ZeroDivisionError

🔹 2. Basic Exception Handling — try-except

The try block is used to wrap code that may raise an exception.
The except block handles the exception.

try:
    x = int(input("Enter a number: "))
    print(10 / x)
except ZeroDivisionError:
    print("Cannot divide by zero!")
except ValueError:
    print("Invalid input! Enter a number only.")

🔹 3. Catching Multiple Exceptions

You can catch multiple exceptions in one except block:

try:
    x = int(input("Enter a number: "))
    result = 10 / x
except (ValueError, ZeroDivisionError) as e:
    print("Error occurred:", e)

🔹 4. Catch All Exceptions (Not Recommended)
try:
    print(10 / 0)
except Exception as e:
    print("An error occurred:", e)


⚠️ Best practice: Always catch specific exceptions instead of all exceptions.

🔹 5. The else Clause

else runs only if no exception occurs in the try block.

try:
    x = int(input("Enter a number: "))
    result = 10 / x
except ZeroDivisionError:
    print("Cannot divide by zero!")
else:
    print("Result is:", result)

🔹 6. The finally Clause

finally runs regardless of exception occurrence. Ideal for cleanup actions.

try:
    file = open("data.txt", "r")
    content = file.read()
except FileNotFoundError:
    print("File not found!")
finally:
    print("Closing file.")
    file.close()

🔹 7. Raising Exceptions

You can manually raise exceptions using raise.

def validate_age(age):
    if age < 0:
        raise ValueError("Age cannot be negative!")
    else:
        print("Valid age:", age)

validate_age(-5)


Output:

ValueError: Age cannot be negative!

🔹 8. Custom Exceptions

Create your own exceptions by inheriting from Exception.

class NegativeAgeError(Exception):
    pass

def validate_age(age):
    if age < 0:
        raise NegativeAgeError("Age cannot be negative!")
    else:
        print("Valid age:", age)

validate_age(-10)

🔹 9. Exception Hierarchy

Python exceptions are hierarchical.

BaseException
 └── Exception
      ├── ArithmeticError
      │    ├── ZeroDivisionError
      │    └── OverflowError
      ├── LookupError
      │    ├── IndexError
      │    └── KeyError
      ├── ValueError
      └── TypeError


Exception covers most user-defined exceptions.

BaseException is the parent of all exceptions (including SystemExit, KeyboardInterrupt).

🔹 10. Best Practices in Python Exception Handling

Catch specific exceptions, not all.

Avoid empty except blocks — always log or print the error.

Use finally for resource cleanup.

Prefer raising custom exceptions for clarity.

Avoid using exceptions for normal control flow — use them only for error cases.

🔹 11. Example — Combining Everything
class CustomError(Exception):
    pass

def divide(a, b):
    if b == 0:
        raise CustomError("Division by zero is forbidden!")
    return a / b

try:
    x = int(input("Enter numerator: "))
    y = int(input("Enter denominator: "))
    result = divide(x, y)
except ValueError:
    print("Invalid number!")
except CustomError as e:
    print("Custom Error:", e)
else:
    print("Division Result:", result)
finally:
    print("Execution completed.")