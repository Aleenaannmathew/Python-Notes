🟢 Python try-except — Detailed Explanation

In Python, errors and exceptions occur when the code encounters unexpected conditions. Rather than crashing the program, we can handle these exceptions gracefully using try-except.

🔹 1. Basic Syntax
try:
    # Code that may raise an exception
    num = int(input("Enter a number: "))
except ValueError:
    # Code to handle the exception
    print("Invalid input! Please enter an integer.")


Explanation:

try block: Code that might cause an exception.

except block: Handles the exception and prevents program crash.

If no exception occurs, except is skipped.

🔹 2. Catching Specific Exceptions

You can catch specific exceptions to handle different errors differently:

try:
    x = int(input("Enter a number: "))
    result = 10 / x
except ValueError:
    print("Invalid input! Not an integer.")
except ZeroDivisionError:
    print("Cannot divide by zero!")


Explanation:

ValueError: Raised if input is not an integer.

ZeroDivisionError: Raised if we divide by zero.

Best practice: Always catch specific exceptions rather than a generic Exception unless necessary.

🔹 3. Catching Multiple Exceptions in One Line
try:
    num = int(input("Enter a number: "))
    result = 10 / num
except (ValueError, ZeroDivisionError) as e:
    print(f"Error occurred: {e}")


(ValueError, ZeroDivisionError) catches either of the exceptions.

as e gives the exception object to get more info.

🔹 4. Generic Exception Handling
try:
    x = 5 / 0
except Exception as e:
    print(f"Some error occurred: {e}")


Exception catches any exception.

Useful for logging errors in production, but not recommended for debugging because it hides specific errors.

🔹 5. The else Block

else runs only if no exception occurs:

try:
    num = int(input("Enter a number: "))
except ValueError:
    print("Invalid input!")
else:
    print(f"You entered: {num}")


Helps separate normal execution from exception handling.

🔹 6. The finally Block

finally runs always, regardless of exceptions:

try:
    file = open("data.txt", "r")
    data = file.read()
except FileNotFoundError:
    print("File not found!")
finally:
    print("Closing file...")
    file.close()


Used for cleanup, like closing files, releasing resources, or network connections.

🔹 7. Raising Exceptions

You can raise your own exceptions using raise:

age = int(input("Enter your age: "))
if age < 0:
    raise ValueError("Age cannot be negative!")


Can raise built-in exceptions or custom exceptions (we will cover custom exceptions in another section).

🔹 8. Nested try-except

You can have nested exception handling for complex cases:

try:
    num = int(input("Enter a number: "))
    try:
        result = 10 / num
    except ZeroDivisionError:
        print("Cannot divide by zero!")
except ValueError:
    print("Invalid input!")


Useful for handling different levels of exceptions separately.

🔹 9. Catching All Exceptions But Preserving Stack Trace

Sometimes you want to log an exception without stopping the program:

import traceback

try:
    x = 5 / 0
except Exception as e:
    print("An error occurred")
    traceback.print_exc()


traceback.print_exc() prints the full error stack, useful for debugging.

🔹 10. Best Practices for try-except

Catch specific exceptions whenever possible.

Avoid bare except (except:) unless absolutely necessary.

Use finally for resource cleanup.

Log exceptions for debugging.

Avoid using exceptions for normal control flow (expensive).

Chain exceptions for custom handling:

try:
    x = int("abc")
except ValueError as e:
    raise RuntimeError("Failed to convert string to int") from e

🔹 11. Example — Comprehensive try-except
def divide_numbers():
    try:
        a = int(input("Enter numerator: "))
        b = int(input("Enter denominator: "))
        result = a / b
    except ValueError:
        print("Invalid input! Enter integers only.")
    except ZeroDivisionError:
        print("Error: Cannot divide by zero.")
    else:
        print(f"Result is {result}")
    finally:
        print("Operation completed.")

divide_numbers()


Flow:

If user enters wrong type → ValueError handled.

If denominator is 0 → ZeroDivisionError handled.

If no exception → else block executed.

finally always runs.