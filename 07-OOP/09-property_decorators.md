🟢 Property Decorators in Python — Detailed Explanation

In Python, property decorators allow you to use methods like attributes. They are commonly used to control access to instance attributes (get, set, delete) while keeping the syntax simple and readable.

🔹 1. Basic Concept

A property decorator lets you define getter, setter, and deleter for an attribute. This allows encapsulation without changing how you access the attribute.

Syntax Overview:

class ClassName:
    @property
    def attribute(self):
        # Getter method
        return value

    @attribute.setter
    def attribute(self, value):
        # Setter method
        pass

    @attribute.deleter
    def attribute(self):
        # Deleter method
        pass

🔹 2. Using @property — Getter

The @property decorator is used to access a method like an attribute.

Example — Getter
class Employee:
    def __init__(self, name, salary):
        self.name = name
        self._salary = salary  # underscore indicates 'protected' variable

    @property
    def salary(self):
        """Getter for salary"""
        return self._salary

emp = Employee("Alice", 50000)
print(emp.salary)  # Access like attribute, calls the getter


✅ Benefits:

Prevents direct access to private/protected attributes.

Allows computed values on access.

🔹 3. Using @<property>.setter — Setter

The @<property>.setter decorator allows you to modify the value of a property while controlling how it’s set.

Example — Setter
class Employee:
    def __init__(self, name, salary):
        self.name = name
        self._salary = salary

    @property
    def salary(self):
        return self._salary

    @salary.setter
    def salary(self, value):
        if value < 0:
            raise ValueError("Salary cannot be negative")
        self._salary = value

emp = Employee("Alice", 50000)
emp.salary = 60000   # Works fine
# emp.salary = -1000 # Raises ValueError


✅ Benefits:

Enforces validation when setting values.

Protects internal state of object.

🔹 4. Using @<property>.deleter — Deleter

The @<property>.deleter decorator lets you delete the attribute in a controlled way.

Example — Deleter
class Employee:
    def __init__(self, name, salary):
        self.name = name
        self._salary = salary

    @property
    def salary(self):
        return self._salary

    @salary.deleter
    def salary(self):
        print("Deleting salary...")
        del self._salary

emp = Employee("Alice", 50000)
del emp.salary   # Prints "Deleting salary..."


✅ Benefits:

Allows custom cleanup or logging before deletion.

🔹 5. Advantages of Property Decorators

Encapsulation: Control access to private attributes.

Clean Syntax: Access methods as if they were attributes.

Validation: Ensure attributes have valid values.

Computed Properties: Return calculated values dynamically.

🔹 6. Example — Computed Property
class Circle:
    def __init__(self, radius):
        self._radius = radius

    @property
    def radius(self):
        return self._radius

    @radius.setter
    def radius(self, value):
        if value < 0:
            raise ValueError("Radius cannot be negative")
        self._radius = value

    @property
    def area(self):
        # Computed property
        import math
        return math.pi * (self._radius ** 2)

c = Circle(5)
print(c.radius)  # 5
print(c.area)    # 78.5398...
c.radius = 10
print(c.area)    # 314.159...


Observation:
area is read-only, computed dynamically, and cannot be set directly.