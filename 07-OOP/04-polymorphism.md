🟢 Polymorphism in Python — Detailed Explanation

Polymorphism is a core concept of Object-Oriented Programming (OOP). The term “Polymorphism” comes from Greek, meaning “many forms”.

In Python, polymorphism allows objects of different classes to be treated as objects of a common superclass, and it allows methods to have the same name but behave differently depending on the object calling them.

🔹 1. Types of Polymorphism
1. Compile-Time (Static) Polymorphism

Achieved through method overloading or operator overloading.

Note: Python does not support traditional method overloading, but you can achieve similar behavior using default arguments or variable arguments.

Example: Using Default Arguments
class MathOperations:
    def add(self, a, b=0, c=0):
        return a + b + c

m = MathOperations()
print(m.add(5))        # 5
print(m.add(5, 10))    # 15
print(m.add(5, 10, 15))# 30

Example: Operator Overloading
class Point:
    def __init__(self, x, y):
        self.x = x
        self.y = y

    def __add__(self, other):  # Overloading +
        return Point(self.x + other.x, self.y + other.y)

p1 = Point(2, 3)
p2 = Point(4, 5)
p3 = p1 + p2
print(p3.x, p3.y)  # 6 8

2. Run-Time (Dynamic) Polymorphism

Achieved through method overriding in inheritance.

The method called is determined at runtime based on the object type.

class Bird:
    def speak(self):
        print("Some sound")

class Parrot(Bird):
    def speak(self):
        print("Parrot says: Squawk!")

class Crow(Bird):
    def speak(self):
        print("Crow says: Caw!")

def make_speak(bird):
    bird.speak()  # The correct method is called at runtime

p = Parrot()
c = Crow()

make_speak(p)  # Parrot says: Squawk!
make_speak(c)  # Crow says: Caw!

🔹 2. Polymorphism with Functions

Polymorphism allows different objects to respond differently to the same function call.

class Dog:
    def speak(self):
        print("Woof!")

class Cat:
    def speak(self):
        print("Meow!")

animals = [Dog(), Cat()]

for animal in animals:
    animal.speak()  # Polymorphic behavior


Output:

Woof!
Meow!

🔹 3. Polymorphism with Inbuilt Functions

Polymorphism is not limited to user-defined classes.

Built-in functions like len() work on different types: strings, lists, tuples, dictionaries, etc.

print(len("Hello"))    # 5
print(len([1, 2, 3])) # 3
print(len((1, 2, 3))) # 3
print(len({"a":1, "b":2})) # 2


Same function len() behaves differently depending on the object type.

🔹 4. Duck Typing in Python

Python uses duck typing, a type of dynamic polymorphism.

It allows any object with the required method or attribute to be used, regardless of its class.

class Bird:
    def fly(self):
        print("Bird can fly")

class Airplane:
    def fly(self):
        print("Airplane can fly")

def lets_fly(entity):
    entity.fly()  # Works for any object with fly() method

b = Bird()
a = Airplane()
lets_fly(b)  # Bird can fly
lets_fly(a)  # Airplane can fly