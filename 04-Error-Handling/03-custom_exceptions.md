🟢 Custom Exceptions in Python — Detailed Explanation

Python provides a flexible way to create your own exceptions. This allows you to define errors specific to your application rather than using generic built-in exceptions.

🔹 1. Why Custom Exceptions?

To improve readability: Using meaningful exception names makes your code easier to understand.

To handle specific application logic: You can distinguish between standard errors and errors specific to your program.

To make debugging easier: Clear custom exceptions indicate the exact problem.

Example scenario:

class NegativeAgeError(Exception):
    pass

age = -5
if age < 0:
    raise NegativeAgeError("Age cannot be negative!")


Here, NegativeAgeError makes it immediately clear what went wrong.

🔹 2. Creating a Basic Custom Exception
class MyCustomError(Exception):
    pass

# Usage
try:
    raise MyCustomError("Something went wrong!")
except MyCustomError as e:
    print(f"Caught an error: {e}")


Exception is the base class for all exceptions.

We inherit from Exception to define a custom exception class.

🔹 3. Custom Exception with Constructor

You can pass additional information when raising exceptions:

class InvalidAgeError(Exception):
    def __init__(self, age, message="Age is invalid"):
        self.age = age
        self.message = message
        super().__init__(self.message)

# Usage
age = -10
try:
    if age < 0:
        raise InvalidAgeError(age)
except InvalidAgeError as e:
    print(f"Invalid age: {e.age} — {e}")


super().__init__(self.message) ensures the message is properly handled by Python’s exception system.

🔹 4. Multiple Custom Exceptions

You can define different exceptions for different scenarios:

class InsufficientBalanceError(Exception):
    pass

class InvalidTransactionError(Exception):
    pass

def withdraw(balance, amount):
    if amount > balance:
        raise InsufficientBalanceError("Not enough balance!")
    if amount <= 0:
        raise InvalidTransactionError("Amount must be positive!")
    balance -= amount
    return balance

# Usage
try:
    balance = 1000
    balance = withdraw(balance, 2000)
except InsufficientBalanceError as e:
    print(e)
except InvalidTransactionError as e:
    print(e)


Helps categorize errors for precise handling.

🔹 5. Custom Exception Hierarchy

You can create a hierarchy of custom exceptions for more structured error handling:

class AppError(Exception):
    """Base class for application errors"""
    pass

class DatabaseError(AppError):
    """Errors related to database"""
    pass

class NetworkError(AppError):
    """Errors related to network"""
    pass

# Usage
try:
    raise NetworkError("No internet connection")
except AppError as e:
    print(f"Caught application error: {e}")


Catching the base class allows you to handle all related errors together.

Catching subclasses allows more specific handling.

🔹 6. Raising Exceptions in Functions
def divide(a, b):
    if b == 0:
        raise ZeroDivisionError("Cannot divide by zero")
    return a / b

try:
    result = divide(10, 0)
except ZeroDivisionError as e:
    print(f"Error: {e}")


You can raise built-in exceptions in your functions, or your custom exceptions.

🔹 7. Best Practices for Custom Exceptions

Inherit from Exception, not from BaseException.

Use meaningful names ending with Error.

Include useful information in the exception message.

Keep it simple — don’t overcomplicate the hierarchy unless needed.

Use exception chaining if another exception caused your custom exception:

try:
    int("abc")
except ValueError as e:
    raise MyCustomError("Conversion failed") from e


from e keeps the original traceback intact.

🔹 8. Example — Complete Custom Exception Usage
class NegativeNumberError(Exception):
    def __init__(self, number):
        self.number = number
        super().__init__(f"Negative numbers not allowed: {self.number}")

def square_root(num):
    if num < 0:
        raise NegativeNumberError(num)
    return num ** 0.5

try:
    result = square_root(-25)
except NegativeNumberError as e:
    print(f"Error: {e}")
finally:
    print("Operation attempted.")


Flow:

User enters a negative number → NegativeNumberError is raised.

The exception is caught and handled gracefully.

finally block runs to indicate operation was attempted.

✅ Key Points to Remember