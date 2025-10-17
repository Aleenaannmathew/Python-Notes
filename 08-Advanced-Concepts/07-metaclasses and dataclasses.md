🟢 Metaclasses in Python — Detailed Explanation
🔹 1. What is a Metaclass?

A metaclass is a class of a class.

Just as an object is an instance of a class, a class itself is an instance of a metaclass.

It defines how classes behave, i.e., it controls the creation of classes.

Key idea: If you want to customize class creation, you use a metaclass.

🔹 2. Default Metaclass

In Python, type is the default metaclass.

class MyClass:
    pass

print(type(MyClass))  # <class 'type'>
print(type(type))     # <class 'type'>


type creates classes dynamically.

🔹 3. Creating a Custom Metaclass
class MyMeta(type):
    def __new__(cls, name, bases, dct):
        print(f"Creating class {name}")
        return super().__new__(cls, name, bases, dct)

class Person(metaclass=MyMeta):
    pass

# Output: Creating class Person


Explanation:

__new__ is called when the class is created, not when an instance is created.

cls: metaclass itself

name: name of the class being created

bases: parent classes

dct: dictionary of attributes

🔹 4. Why Use Metaclasses?

Validation

Ensure classes have certain attributes or methods.

Automatic Registration

Automatically keep track of all subclasses.

Modification

Modify class attributes dynamically.

🔹 5. Example: Enforcing Attributes
class RequireNameMeta(type):
    def __new__(cls, name, bases, dct):
        if 'name' not in dct:
            raise TypeError("Class must have 'name' attribute")
        return super().__new__(cls, name, bases, dct)

class Person(metaclass=RequireNameMeta):
    name = "John"  # Required attribute

🟢 Data Classes in Python — Detailed Explanation
🔹 1. What is a Data Class?

Introduced in Python 3.7 (dataclasses module).

A data class is a class mainly used to store data with minimal boilerplate.

Automatically generates:

__init__

__repr__

__eq__

__hash__ (optional)

🔹 2. Basic Example
from dataclasses import dataclass

@dataclass
class Person:
    name: str
    age: int

p1 = Person("Alice", 25)
print(p1)  # Person(name='Alice', age=25)


No need to write __init__ or __repr__.

🔹 3. Default Values and Type Annotations
@dataclass
class Person:
    name: str
    age: int = 18
    city: str = "Unknown"

p2 = Person("Bob")
print(p2)  # Person(name='Bob', age=18, city='Unknown')


Default values work like normal Python classes.

Type annotations are mandatory for fields in data classes.

🔹 4. Post Initialization

Use __post_init__ to process or validate fields after __init__.

@dataclass
class Person:
    name: str
    age: int

    def __post_init__(self):
        if self.age < 0:
            raise ValueError("Age cannot be negative")

p = Person("Charlie", -5)  # Raises ValueError

🔹 5. Immutability with frozen=True
@dataclass(frozen=True)
class Person:
    name: str
    age: int

p = Person("Dave", 30)
# p.age = 35  -> Raises FrozenInstanceError


frozen=True makes the object immutable (read-only).

🔹 6. Comparison Operators

By default, data classes provide __eq__ method.

p1 = Person("Alice", 25)
p2 = Person("Alice", 25)
print(p1 == p2)  # True


Can add order=True to generate <, <=, >, >=:

@dataclass(order=True)
class Person:
    age: int
    name: str

print(Person(25,"Alice") < Person(30,"Bob"))  # True

🔹 7. Advantages of Data Classes

Less boilerplate code.

Cleaner and readable.

Supports comparison, hashing, and immutability.

Can be used with type hints for better clarity.

Summary:

Metaclasses → Control class creation, customize behavior at the class level.

Data Classes → Simplify creation of classes meant to store data with auto-generated methods.