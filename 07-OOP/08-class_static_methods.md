🟢 Class and Static Methods in Python — Detailed Explanation

In Python, methods inside a class can be of three types:

Instance Methods → Work with instance objects (self).

Class Methods → Work with the class itself (cls).

Static Methods → Do not depend on the class or instance.

Here we focus on Class Methods and Static Methods.

🔹 1. Class Methods

A class method is a method that receives the class as the first argument instead of the instance. It is declared using the @classmethod decorator.

Syntax
class ClassName:
    @classmethod
    def method_name(cls, ...):
        pass

Key Points

First parameter is cls, representing the class.

Can access class attributes, not instance attributes.

Can be called using the class or instance.

Often used for factory methods.

Example — Class Method
class Employee:
    raise_amount = 1.10  # Class attribute

    def __init__(self, name, salary):
        self.name = name
        self.salary = salary

    @classmethod
    def set_raise_amount(cls, amount):
        cls.raise_amount = amount

    @classmethod
    def from_string(cls, emp_str):
        name, salary = emp_str.split("-")
        return cls(name, float(salary))

# Using class method to modify class attribute
Employee.set_raise_amount(1.20)
print(Employee.raise_amount)  # 1.2

# Using class method as a factory
emp_str = "Alice-50000"
new_emp = Employee.from_string(emp_str)
print(new_emp.name, new_emp.salary)  # Alice 50000.0


✅ Advantages of Class Methods

Can access and modify class-level data.

Useful for alternative constructors.

Can be called via class or instance.

🔹 2. Static Methods

A static method is a method that does not receive self or cls as the first argument. It is declared using the @staticmethod decorator.

Syntax
class ClassName:
    @staticmethod
    def method_name(...):
        pass

Key Points

Does not access instance or class attributes.

Behaves like a regular function inside a class.

Can be called using class or instance.

Often used for utility functions related to the class.

Example — Static Method
class MathOperations:

    @staticmethod
    def add(x, y):
        return x + y

    @staticmethod
    def multiply(x, y):
        return x * y

# Using static methods
print(MathOperations.add(5, 3))        # 8
print(MathOperations.multiply(4, 6))   # 24


✅ Advantages of Static Methods

Can be used without creating an instance.

Keeps the method related to the class logically.

Useful for utility/helper functions.

🔹 3. Differences Between Class and Static Methods
Feature	Class Method	Static Method
First Parameter	cls (class reference)	None
Access Class Attributes	Yes	No
Access Instance Attributes	No	No
Can be called with class	Yes	Yes
Can be called with instance	Yes	Yes
Use Case	Factory methods, modifying class	Utility/helper methods