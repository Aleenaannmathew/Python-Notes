🟢 Monkey Patching in Python — Detailed Explanation

Monkey Patching is the dynamic (runtime) modification of a class or module in Python. It allows you to change or extend the behavior of libraries, classes, or functions without altering the original source code.

🔹 1. What is Monkey Patching?

It is a technique used to add, modify, or override attributes or methods of classes or modules at runtime.

Often used for testing, debugging, or extending functionality.

Key Idea: Modify code behavior without touching the original codebase.

🔹 2. Basic Example
class Dog:
    def bark(self):
        return "Woof!"

# Normal behavior
d = Dog()
print(d.bark())  # Woof!

# Monkey patching the method
def new_bark(self):
    return "Meow!"

Dog.bark = new_bark
print(d.bark())  # Meow!


Explanation:

Original Dog.bark method is replaced by new_bark at runtime.

All instances of Dog use the new behavior.

🔹 3. Monkey Patching Functions

You can also patch functions in modules:

import math

# Original sqrt
print(math.sqrt(16))  # 4.0

# Monkey patch
math.sqrt = lambda x: "patched!"
print(math.sqrt(16))  # patched!


Useful for testing when you want to mock or override functionality temporarily.

🔹 4. Use Cases of Monkey Patching

Testing / Mocking

Replace functions or methods in tests to simulate behavior.

Hotfixes

Quickly patch third-party libraries without editing source code.

Extending functionality

Add methods to existing classes dynamically.

Debugging / Logging

Override functions to add logging or debugging features.

🔹 5. Risks and Disadvantages

Maintenance Difficulty

Future updates to the library may break your patch.

Unexpected Side Effects

Patching globally affects all instances, possibly causing bugs.

Hard to Debug

Changes are runtime-only, not visible in source code.

Not Recommended in Production

Use cautiously; better suited for testing or prototyping.

🔹 6. Example with a Module
# module: greetings.py
def hello():
    return "Hello!"

# main.py
import greetings

# Normal behavior
print(greetings.hello())  # Hello!

# Monkey patch
greetings.hello = lambda: "Hi there!"
print(greetings.hello())  # Hi there!


The original module is untouched.

All calls to greetings.hello() now return "Hi there!".

🔹 7. Patching Instance Methods vs Class Methods
class Person:
    def greet(self):
        return "Hi!"

p1 = Person()
p2 = Person()

# Patch instance method
p1.greet = lambda: "Hello from p1"
print(p1.greet())  # Hello from p1
print(p2.greet())  # Hi!  (unaffected)

# Patch class method
Person.greet = lambda self: "Hello from class"
print(p2.greet())  # Hello from class


Patching instance method affects only that instance.

Patching class method affects all instances.

🔹 8. Summary

Monkey Patching is a runtime modification of classes or modules.

Useful for testing, debugging, or extending code without altering original sources.

Must be used carefully, especially in production environments, due to potential side effects.