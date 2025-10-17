🟢 Classes and Objects in Python — Detailed Explanation

Python is an object-oriented programming (OOP) language, which means it allows you to model real-world entities using classes and objects. OOP helps organize code, promote reusability, and make programs more modular and maintainable.

🔹 1. What is a Class?

A class is a blueprint or template for creating objects. It defines attributes (data) and methods (functions) that the objects created from the class will have.

class Car:
    # Class attribute
    wheels = 4  

    # Constructor / initializer
    def __init__(self, make, model):
        self.make = make  # Instance attribute
        self.model = model

    # Method
    def display_info(self):
        print(f"{self.make} {self.model} has {Car.wheels} wheels.")


Key points:

class keyword defines a class.

__init__() is a constructor that initializes object attributes.

self represents the instance of the class (similar to this in other languages).

Attributes can be class-level (shared) or instance-level (unique to each object).

🔹 2. What is an Object?

An object is an instance of a class. Objects are the actual entities created using the class blueprint.

# Creating objects
car1 = Car("Toyota", "Corolla")
car2 = Car("Honda", "Civic")

# Accessing methods
car1.display_info()  # Output: Toyota Corolla has 4 wheels.
car2.display_info()  # Output: Honda Civic has 4 wheels.

# Accessing attributes
print(car1.make)  # Toyota
print(car2.model) # Civic


Key points:

Each object has its own instance attributes.

Objects share class attributes unless overridden.

🔹 3. Instance vs Class Attributes
class Dog:
    species = "Canine"  # Class attribute

    def __init__(self, name, age):
        self.name = name  # Instance attribute
        self.age = age

dog1 = Dog("Buddy", 3)
dog2 = Dog("Charlie", 5)

# Access class attribute
print(dog1.species)  # Canine
print(dog2.species)  # Canine

# Access instance attributes
print(dog1.name)     # Buddy
print(dog2.name)     # Charlie


Class attribute → shared among all instances

Instance attribute → unique to each instance

🔹 4. Methods in a Class
4.1 Instance Methods

Defined with self

Can access instance and class attributes

class Circle:
    pi = 3.14159

    def __init__(self, radius):
        self.radius = radius

    def area(self):
        return Circle.pi * self.radius ** 2

c = Circle(5)
print(c.area())  # 78.53975

4.2 Class Methods

Defined with @classmethod decorator

Receives cls parameter (class itself)

class Circle:
    pi = 3.14159

    @classmethod
    def change_pi(cls, new_pi):
        cls.pi = new_pi

Circle.change_pi(3.14)
print(Circle.pi)  # 3.14

4.3 Static Methods

Defined with @staticmethod decorator

Doesn’t take self or cls

Acts like a utility function within a class

class Math:
    @staticmethod
    def add(a, b):
        return a + b

print(Math.add(5, 3))  # 8

🔹 5. Accessing Attributes and Methods
class Student:
    def __init__(self, name):
        self.name = name

    def greet(self):
        print(f"Hello, my name is {self.name}")

s = Student("Alice")

# Access attribute
print(s.name)

# Modify attribute
s.name = "Bob"

# Call method
s.greet()


Use getattr(), setattr(), hasattr() for dynamic access:

print(getattr(s, "name"))  # Bob
setattr(s, "name", "Charlie")
print(hasattr(s, "name"))  # True

🔹 6. Object Deletion

Objects are automatically destroyed when no reference exists.

Explicit deletion using del:

s = Student("Alice")
del s


The __del__ method (destructor) can be defined:

class Test:
    def __del__(self):
        print("Object destroyed")

t = Test()
del t  # Output: Object destroyed

🔹 7. Encapsulation

Private attributes → prefix with __

Accessible via getter and setter methods

class BankAccount:
    def __init__(self, balance):
        self.__balance = balance  # Private

    def get_balance(self):
        return self.__balance

    def deposit(self, amount):
        self.__balance += amount

account = BankAccount(1000)
print(account.get_balance())  # 1000

🔹 8. Special (Magic) Methods

Predefined methods in Python classes

Examples: __str__, __repr__, __len__, __add__, etc.

class Book:
    def __init__(self, title, pages):
        self.title = title
        self.pages = pages

    def __str__(self):
        return f"{self.title} ({self.pages} pages)"

b = Book("Python Guide", 200)
print(b)  # Python Guide (200 pages)
