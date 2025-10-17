🟢 *args and **kwargs in Python
🧠 What are *args and **kwargs?

In Python, when defining functions, you can use special symbols:

*args → Non-keyworded variable-length arguments (tuple)

**kwargs → Keyworded variable-length arguments (dictionary)

They allow functions to accept an arbitrary number of arguments, making them flexible and reusable.

🔹 1. Understanding *args (Variable-Length Positional Arguments)
🧩 Syntax
def function_name(*args):
    # args is a tuple


*args lets you pass any number of positional arguments.

Inside the function, args behaves like a tuple.

✅ Example
def add_numbers(*args):
    print(args)         # Tuple of all arguments
    print(type(args))   # <class 'tuple'>
    return sum(args)

print(add_numbers(1, 2, 3))         # 6
print(add_numbers(4, 5, 6, 7, 8))   # 30

🧩 Iterating Over *args
def greet_people(*args):
    for name in args:
        print(f"Hello, {name}!")

greet_people("Alice", "Bob", "Charlie")


Output:

Hello, Alice!
Hello, Bob!
Hello, Charlie!

🧩 Mixing *args with Normal Arguments
def multiply(multiplier, *numbers):
    return [multiplier * n for n in numbers]

print(multiply(2, 1, 2, 3, 4))
# [2, 4, 6, 8]


Here, multiplier is a fixed argument, and all remaining arguments go into numbers as a tuple.

🔹 2. Understanding **kwargs (Variable-Length Keyword Arguments)
🧩 Syntax
def function_name(**kwargs):
    # kwargs is a dictionary


**kwargs allows passing any number of keyword arguments.

Inside the function, it’s treated as a dictionary.

✅ Example
def display_info(**kwargs):
    print(kwargs)        # Dictionary of all keyword arguments
    for key, value in kwargs.items():
        print(f"{key}: {value}")

display_info(name="Alice", age=25, city="New York")


Output:

{'name': 'Alice', 'age': 25, 'city': 'New York'}
name: Alice
age: 25
city: New York

🔹 3. Combining Normal Arguments, *args, and **kwargs

You can mix all three in a single function definition.

✅ Example
def order_summary(order_id, *items, **details):
    print(f"Order ID: {order_id}")
    print("Items:", items)
    print("Details:", details)

order_summary(
    101,
    "Shirt", "Jeans", "Shoes",
    payment="UPI",
    address="Bangalore"
)


Output:

Order ID: 101
Items: ('Shirt', 'Jeans', 'Shoes')
Details: {'payment': 'UPI', 'address': 'Bangalore'}

🔹 4. Order of Parameters in a Function

The correct order when combining parameters is:

def func(positional, *args, keyword_only, **kwargs):


✅ Example

def example(a, b, *args, c=10, **kwargs):
    print(a, b, args, c, kwargs)

example(1, 2, 3, 4, c=20, x=5, y=6)
# Output: 1 2 (3, 4) 20 {'x': 5, 'y': 6}

🔹 5. Argument Unpacking

You can also unpack lists, tuples, and dictionaries when calling a function.

🧩 Using * for lists/tuples
def add(a, b, c):
    return a + b + c

nums = (1, 2, 3)
print(add(*nums))  # 6

🧩 Using ** for dictionaries
def introduce(name, age):
    print(f"My name is {name} and I am {age} years old.")

person = {"name": "Alice", "age": 25}
introduce(**person)
# My name is Alice and I am 25 years old.

🔹 6. Real-World Use Cases
🧩 a) Logging or Debugging Functions
def debug(*args, **kwargs):
    print("ARGS:", args)
    print("KWARGS:", kwargs)

debug(1, 2, 3, mode="test", level="debug")

🧩 b) Forwarding Arguments to Another Function

Used when writing wrapper or decorator functions.

def logger(func):
    def wrapper(*args, **kwargs):
        print(f"Calling {func.__name__} with {args} and {kwargs}")
        return func(*args, **kwargs)
    return wrapper

@logger
def add(a, b):
    return a + b

add(5, 10)

🧩 c) Handling Flexible APIs
def create_user(**kwargs):
    default_data = {"role": "user", "active": True}
    default_data.update(kwargs)
    return default_data

user = create_user(name="Alice", email="alice@example.com")
print(user)
# {'role': 'user', 'active': True, 'name': 'Alice', 'email': 'alice@example.com'}

🔹 7. Using Both *args and **kwargs Together
def show_all(*args, **kwargs):
    print("Positional:", args)
    print("Keyword:", kwargs)

show_all(1, 2, 3, name="Alice", age=22)


Output:

Positional: (1, 2, 3)
Keyword: {'name': 'Alice', 'age': 22}

🔹 8. Advanced Example — Dynamic Function Caller
def power(base, exponent):
    return base ** exponent

def dynamic_call(func, *args, **kwargs):
    return func(*args, **kwargs)

print(dynamic_call(power, 2, 3))  # 8

🔹 9. Advantages of Using *args and **kwargs

✅ Flexibility: Handle variable numbers of arguments.
✅ Reusability: Write functions that can accept many inputs.
✅ Dynamic: Useful for decorators, logging, and wrappers.
✅ Clean Code: Avoids long parameter lists.

🔹 10. Best Practices

Always name them *args and **kwargs for clarity (though technically you can name them anything).

Avoid mixing too many parameter types — maintain readability.

Use unpacking only when necessary to keep code clean.

When combining:

def func(positional_args, *args, default_args, **kwargs)

🏁 Key Takeaways
Feature	*args	**kwargs
Accepts	Variable positional args	Variable keyword args
Type	Tuple	Dictionary
Usage	*args → values only	**kwargs → key-value pairs
Unpacking	Works with list/tuple	Works with dict
Common Use	Flexible functions, decorators	Dynamic keyword handling
✅ Quick Recap
def sample_func(a, b, *args, **kwargs):
    print("a:", a)
    print("b:", b)
    print("args:", args)
    print("kwargs:", kwargs)

sample_func(1, 2, 3, 4, x=10, y=20)
# a: 1
# b: 2
# args: (3, 4)
# kwargs: {'x': 10, 'y': 20}