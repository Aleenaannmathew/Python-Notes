🟢 Inheritance in Python — Detailed Explanation

Inheritance is a core concept in Object-Oriented Programming (OOP). It allows a class (child/subclass) to reuse attributes and methods of another class (parent/superclass). This promotes code reusability and hierarchical classification.

🔹 1. Basics of Inheritance

The parent class (also called base class or superclass) contains common attributes and methods.

The child class (subclass) inherits these attributes and methods and can also add its own.

Syntax
class Parent:
    def parent_method(self):
        print("This is a parent method")

class Child(Parent):  # Inherits from Parent
    def child_method(self):
        print("This is a child method")

c = Child()
c.parent_method()  # Accessing parent method
c.child_method()   # Accessing child method


Output:

This is a parent method
This is a child method

🔹 2. Types of Inheritance

Python supports several types of inheritance:

1. Single Inheritance

A child class inherits from one parent class.

class Parent:
    pass

class Child(Parent):
    pass

2. Multiple Inheritance

A child class inherits from more than one parent class.

class Mother:
    def skills_mother(self):
        print("Cooking")

class Father:
    def skills_father(self):
        print("Driving")

class Child(Mother, Father):
    pass

c = Child()
c.skills_mother()  # Cooking
c.skills_father()  # Driving

3. Multilevel Inheritance

A class inherits from a child class, forming a chain.

class Grandparent:
    def wisdom(self):
        print("Wisdom from Grandparent")

class Parent(Grandparent):
    pass

class Child(Parent):
    pass

c = Child()
c.wisdom()  # Wisdom from Grandparent

4. Hierarchical Inheritance

Multiple child classes inherit from one parent class.

class Parent:
    def greet(self):
        print("Hello from Parent")

class Child1(Parent):
    pass

class Child2(Parent):
    pass

c1 = Child1()
c2 = Child2()
c1.greet()  # Hello from Parent
c2.greet()  # Hello from Parent

5. Hybrid Inheritance

A combination of two or more types of inheritance.

Example: Multiple + Multilevel

class A:
    pass

class B(A):
    pass

class C(A):
    pass

class D(B, C):
    pass

🔹 3. Overriding Methods

A child class can override a method of the parent class to provide a new implementation.

class Parent:
    def greet(self):
        print("Hello from Parent")

class Child(Parent):
    def greet(self):
        print("Hello from Child")  # Overridden

c = Child()
c.greet()  # Hello from Child

🔹 4. Using super()

super() allows access to parent class methods or constructors in the child class.

Example: Calling Parent Constructor
class Parent:
    def __init__(self, name):
        self.name = name
        print(f"Parent initialized: {self.name}")

class Child(Parent):
    def __init__(self, name, age):
        super().__init__(name)  # Call parent constructor
        self.age = age
        print(f"Child initialized: {self.age}")

c = Child("Alice", 20)


Output:

Parent initialized: Alice
Child initialized: 20

Example: Calling Parent Method
class Parent:
    def greet(self):
        print("Hello from Parent")

class Child(Parent):
    def greet(self):
        print("Hello from Child")
        super().greet()  # Call parent method

c = Child()
c.greet()


Output:

Hello from Child
Hello from Parent

🔹 5. Multiple Inheritance & Method Resolution Order (MRO)

Python uses MRO to determine which parent’s method to call in multiple inheritance.

You can check the MRO using ClassName.__mro__ or help(ClassName).

class A:
    def show(self):
        print("A")

class B(A):
    def show(self):
        print("B")

class C(A):
    def show(self):
        print("C")

class D(B, C):
    pass

d = D()
d.show()  # Output: B

print(D.__mro__)


Explanation: Python follows C3 linearization to resolve method order.