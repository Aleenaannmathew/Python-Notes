🟢 Closures in Python — Detailed Explanation

A closure in Python is a function object that remembers values in enclosing scopes even if those scopes are no longer present. Closures are used to encapsulate data and can help in creating decorators, callbacks, and higher-order functions.

🔹 1. What is a Closure?

A closure occurs when:

There is an inner function nested inside an outer function.

The inner function references variables from the outer function.

The outer function returns the inner function.

The inner function retains access to the outer function’s variables even after the outer function has finished execution.

🔹 2. Example of a Closure
def outer_func(x):
    def inner_func(y):
        return x + y
    return inner_func

add_five = outer_func(5)  # outer_func returns inner_func
print(add_five(10))        # 15


Explanation:

outer_func(5) returns inner_func.

inner_func still remembers x = 5 even though outer_func has finished executing.

This is a closure because inner_func “closes over” x.

🔹 3. Identifying a Closure

A function is a closure if:

It is nested inside another function.

It references variables from the enclosing function.

It is returned or passed outside the enclosing function.

You can check closures using __closure__ attribute:

def outer(a):
    b = 10
    def inner(x):
        return x + a + b
    return inner

fn = outer(5)
print(fn.__closure__)  # (<cell at 0x...: int object at 0x...>, <cell at 0x...: int object at 0x...>)


Each cell in __closure__ contains a variable from the enclosing scope.

🔹 4. Use Cases of Closures

Data Hiding / Encapsulation

def make_counter():
    count = 0
    def counter():
        nonlocal count
        count += 1
        return count
    return counter

c = make_counter()
print(c())  # 1
print(c())  # 2


count is hidden from the global scope but maintained across calls.

Decorator Functions

Closures are widely used to create decorators that modify function behavior.

Callbacks / Functional Programming

Functions that return functions for deferred execution or callbacks.

🔹 5. nonlocal Keyword

To modify variables from an outer scope, use nonlocal.

Without nonlocal, the closure can read but cannot modify outer variables.

def outer():
    x = 10
    def inner():
        nonlocal x
        x += 5
        return x
    return inner

fn = outer()
print(fn())  # 15
print(fn())  # 20

🔹 6. Advantages of Closures

Encapsulation: Can hide variables from the global scope.

Maintain State: Useful for counters, accumulators, or caching.

Functional Programming: Can return functions with preserved state.

Decorators: Provide a foundation for Python decorators.

🔹 7. Summary

A closure is an inner function that remembers variables from its enclosing scope.

Used to encapsulate data, maintain state, and implement higher-order functions.

Closures are a key concept for decorators, callbacks, and functional programming in Python.