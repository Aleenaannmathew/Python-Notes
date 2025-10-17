🟢 Constructors and Destructors in Python — Detailed Explanation

Python uses constructors and destructors to manage the creation and destruction of objects. These are special methods that are automatically called at certain stages of an object's lifecycle.

🔹 1. Constructor (__init__)

A constructor is a special method called when an object is created. It is used to initialize attributes of the object.

Syntax
class ClassName:
    def __init__(self, parameters):
        # Initialize attributes
        self.attribute1 = value1
        self.attribute2 = value2


Always named __init__

self refers to the current instance

Can take additional parameters for initialization

Example: Basic Constructor
class Car:
    def __init__(self, make, model, year):
        self.make = make
        self.model = model
        self.year = year

car1 = Car("Toyota", "Corolla", 2023)

print(car1.make)   # Toyota
print(car1.model)  # Corolla
print(car1.year)   # 2023


Explanation:

car1 is created → __init__ is automatically called

Attributes make, model, and year are initialized

🔹 Constructor Overloading in Python

Python does not support multiple constructors like Java/C++.

You can achieve it using default parameters or *args / **kwargs.

class Person:
    def __init__(self, name, age=18):
        self.name = name
        self.age = age

p1 = Person("Alice")
p2 = Person("Bob", 25)

print(p1.age)  # 18
print(p2.age)  # 25

🔹 Types of Constructors

Default Constructor – No parameters except self

class Dog:
    def __init__(self):
        self.name = "Unknown"


Parameterized Constructor – Takes parameters to initialize attributes

class Dog:
    def __init__(self, name):
        self.name = name

🔹 2. Destructor (__del__)

A destructor is a special method called when an object is about to be destroyed.

Named __del__

Automatically invoked when all references to the object are deleted or program ends

Syntax
class ClassName:
    def __del__(self):
        # Cleanup code
        print("Object destroyed")

Example: Destructor
class Person:
    def __init__(self, name):
        self.name = name
        print(f"Person {self.name} created")

    def __del__(self):
        print(f"Person {self.name} destroyed")

p = Person("Alice")
del p  # Output: Person Alice destroyed


Notes:

Destructors are rarely used in Python because Python has automatic garbage collection

Mainly used to release external resources, e.g., file handles, network connections

🔹 Constructor vs Destructor
Feature	Constructor (__init__)	Destructor (__del__)
Purpose	Initialize an object	Cleanup before object destruction
Called automatically?	Yes, on object creation	Yes, on object deletion or garbage collection
Parameters	Can take parameters	Only self
Return	None	None
Usage	Set initial attribute values	Free resources (optional)
🔹 Practical Example: File Handler with Constructor & Destructor
class FileManager:
    def __init__(self, filename, mode):
        self.file = open(filename, mode)
        print("File opened")

    def write_data(self, data):
        self.file.write(data)

    def __del__(self):
        self.file.close()
        print("File closed")

fm = FileManager("example.txt", "w")
fm.write_data("Hello, Python!")
del fm  # Output: File closed


__init__ opens the file

__del__ ensures the file is closed automatically