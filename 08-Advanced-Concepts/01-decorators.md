🟢 Decorators in Python — Detailed Explanation

A decorator in Python is a function or class that modifies the behavior of another function or method without changing its code. Decorators allow for code reusability, abstraction, and cleaner syntax.

🔹 1. Why Use Decorators?

Add functionality to an existing function/method.

Avoid code repetition.

Implement cross-cutting concerns like:

Logging

Authentication

Timing

Caching

🔹 2. Functions Are First-Class Citizens

In Python:

Functions can be passed as arguments.

Functions can be returned from other functions.

def greet(name):
    return f"Hello, {name}!"

def shout(func):
    return func("Alice").upper()

print(shout(greet))  # Output: HELLO, ALICE!


This is the foundation for decorators.

🔹 3. Basic Decorator Syntax
def decorator(func):
    def wrapper():
        print("Before function call")
        func()
        print("After function call")
    return wrapper

@decorator
def say_hello():
    print("Hello!")

say_hello()


Output:

Before function call
Hello!
After function call


Explanation:

@decorator is equivalent to:

say_hello = decorator(say_hello)


wrapper() adds behavior before and after the original function.

🔹 4. Decorators with Arguments
def decorator(func):
    def wrapper(name):
        print(f"Hello, {name}!")
        func(name)
    return wrapper

@decorator
def greet(name):
    print(f"Welcome, {name}!")

greet("Alice")


Output:

Hello, Alice!
Welcome, Alice!

🔹 5. Decorators with Return Values
def double_result(func):
    def wrapper(*args, **kwargs):
        result = func(*args, **kwargs)
        return result * 2
    return wrapper

@double_result
def add(a, b):
    return a + b

print(add(5, 10))  # Output: 30


The wrapper can accept arguments (*args, **kwargs) and return values.

🔹 6. Chaining Decorators

You can apply multiple decorators to a single function:

def uppercase(func):
    def wrapper(*args, **kwargs):
        return func(*args, **kwargs).upper()
    return wrapper

def greet_decorator(func):
    def wrapper(*args, **kwargs):
        return f"*** {func(*args, **kwargs)} ***"
    return wrapper

@uppercase
@greet_decorator
def greet(name):
    return f"Hello, {name}"

print(greet("Alice"))  # Output: *** HELLO, ALICE ***


Order matters:

The decorator closest to the function executes first.

🔹 7. Decorators with Parameters
def repeat(times):
    def decorator(func):
        def wrapper(*args, **kwargs):
            for _ in range(times):
                func(*args, **kwargs)
        return wrapper
    return decorator

@repeat(3)
def greet(name):
    print(f"Hello {name}")

greet("Alice")


Output:

Hello Alice
Hello Alice
Hello Alice

🔹 8. Using functools.wraps

When you decorate a function, the original function’s metadata (like __name__ and __doc__) is lost.

functools.wraps preserves it.

from functools import wraps

def decorator(func):
    @wraps(func)
    def wrapper(*args, **kwargs):
        print("Calling function...")
        return func(*args, **kwargs)
    return wrapper

@decorator
def greet():
    """Greet function"""
    print("Hello!")

print(greet.__name__)  # Output: greet
print(greet.__doc__)   # Output: Greet function

🔹 9. Common Use Cases of Decorators

Logging:

def log(func):
    def wrapper(*args, **kwargs):
        print(f"Function {func.__name__} called")
        return func(*args, **kwargs)
    return wrapper


Timing execution:

import time
def timer(func):
    def wrapper(*args, **kwargs):
        start = time.time()
        result = func(*args, **kwargs)
        end = time.time()
        print(f"Time taken: {end - start} seconds")
        return result
    return wrapper


Authentication / Access control

Caching / Memoization

🔹 10. Summary

Decorator = a function that wraps another function to extend its behavior.

Can handle:

Arguments

Return values

Multiple decorators

Parameterized decorators

Use @decorator syntax for readability.

functools.wraps preserves original function metadata.