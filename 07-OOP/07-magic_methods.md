🟢 Magic Methods in Python — Detailed Explanation

Magic methods in Python are special methods with double underscores at the beginning and end of their names, like __init__, __str__, etc. They are also called dunder methods (double underscore).

These methods allow developers to customize the behavior of Python objects for built-in operations like arithmetic, comparison, iteration, and object representation.

🔹 1. Why Magic Methods are Important

Customize Object Behavior: Modify how objects respond to operators (+, -, *, etc.).

Implement Python Protocols: Support built-in Python features like iteration, context management, and representation.

Clean and Pythonic Code: Avoid writing explicit methods for standard behavior.

🔹 2. Common Magic Methods
2.1 Object Initialization

__init__(self, ...) → Constructor, called when an object is created.

__del__(self) → Destructor, called when an object is about to be destroyed.

class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def __del__(self):
        print(f"{self.name} is deleted")

p = Person("Alice", 25)
del p

2.2 Object Representation

__str__(self) → Informal string representation (user-friendly).

__repr__(self) → Official string representation (used by Python shell).

class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def __str__(self):
        return f"{self.name} is {self.age} years old"

    def __repr__(self):
        return f"Person('{self.name}', {self.age})"

p = Person("Bob", 30)
print(p)      # Bob is 30 years old
p             # Person('Bob', 30)

2.3 Arithmetic Operations

Customize operators:

Operation	Magic Method
+	__add__
-	__sub__
*	__mul__
/	__truediv__
//	__floordiv__
%	__mod__
**	__pow__
class Point:
    def __init__(self, x, y):
        self.x = x
        self.y = y

    def __add__(self, other):
        return Point(self.x + other.x, self.y + other.y)

    def __str__(self):
        return f"({self.x}, {self.y})"

p1 = Point(2, 3)
p2 = Point(4, 5)
print(p1 + p2)  # (6, 8)

2.4 Comparison Operators
Operator	Magic Method
==	__eq__
!=	__ne__
<	__lt__
<=	__le__
>	__gt__
>=	__ge__
class Person:
    def __init__(self, age):
        self.age = age

    def __lt__(self, other):
        return self.age < other.age

p1 = Person(25)
p2 = Person(30)
print(p1 < p2)  # True

2.5 Callable Objects

__call__(self, ...) → Makes an object callable like a function.

class Greeter:
    def __call__(self, name):
        print(f"Hello {name}!")

g = Greeter()
g("Alice")  # Hello Alice!

2.6 Container Methods

__len__(self) → Returns length.

__getitem__(self, key) → Access elements using indexing.

__setitem__(self, key, value) → Set item at index/key.

__delitem__(self, key) → Delete item.

class MyList:
    def __init__(self, data):
        self.data = data

    def __len__(self):
        return len(self.data)

    def __getitem__(self, index):
        return self.data[index]

lst = MyList([1, 2, 3])
print(len(lst))     # 3
print(lst[1])       # 2

2.7 Context Management

__enter__(self) → Executed when entering with block.

__exit__(self, exc_type, exc_value, traceback) → Executed when exiting with block.

class FileManager:
    def __init__(self, filename, mode):
        self.filename = filename
        self.mode = mode

    def __enter__(self):
        self.file = open(self.filename, self.mode)
        return self.file

    def __exit__(self, exc_type, exc_value, traceback):
        self.file.close()

with FileManager("test.txt", "w") as f:
    f.write("Hello Python!")

2.8 Other Useful Magic Methods

__iter__ → Make object iterable.

__next__ → Define next element in iteration.

__contains__ → Implements in keyword.

__copy__, __deepcopy__ → Customize copy behavior.