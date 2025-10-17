# Python Data Types

In Python, **data types** represent the kind of value a variable holds.  
They determine what operations can be performed on that value.

Python is **dynamically typed**, meaning you don’t have to declare a variable’s type explicitly — it’s inferred automatically at runtime.

```python
x = 10       # int
y = 3.14     # float
z = "Hello"  # str
🧩 1. Built-in Data Types in Python
Python has several built-in data types grouped into categories:

Category	Data Type	Example
Text Type	str	"Hello"
Numeric Types	int, float, complex	10, 3.14, 3+4j
Sequence Types	list, tuple, range	[1,2,3], (1,2,3), range(5)
Mapping Type	dict	{"name": "Alice", "age": 25}
Set Types	set, frozenset	{1,2,3}, frozenset({1,2,3})
Boolean Type	bool	True, False
Binary Types	bytes, bytearray, memoryview	b"Hello", bytearray(5)
None Type	NoneType	None

🔢 2. Numeric Types
Integer (int)
Whole numbers, positive or negative, without a decimal.


a = 10
b = -5
print(type(a))  # <class 'int'>
Float (float)
Numbers with decimal points.


x = 3.14
y = -0.5
Complex (complex)
Used for complex numbers with real and imaginary parts.


z = 3 + 4j
print(z.real)  # 3.0
print(z.imag)  # 4.0
🧵 3. Text Type — str
Strings are sequences of characters enclosed in single ('), double ("), or triple quotes (''' or """).


text = "Python"
multiline = """This is
a multi-line string."""
Strings are immutable, meaning they cannot be changed after creation.


name = "Alice"
# name[0] = "M"  # ❌ Error: Strings are immutable
📜 4. Sequence Types
List
An ordered, mutable collection that allows duplicates.


fruits = ["apple", "banana", "cherry"]
fruits[1] = "mango"
print(fruits)  # ['apple', 'mango', 'cherry']
Tuple
An ordered, immutable collection.


colors = ("red", "green", "blue")
# colors[0] = "yellow" ❌ Error
Range
Represents a sequence of numbers, often used in loops.


r = range(5)
print(list(r))  # [0, 1, 2, 3, 4]
🗺️ 5. Mapping Type — dict
Stores key-value pairs, unordered, and mutable.


person = {"name": "Alice", "age": 25}
print(person["name"])  # Alice
person["age"] = 26     # Update value
⚙️ 6. Set Types
Set
Unordered, mutable collection with unique elements.


nums = {1, 2, 3, 3}
print(nums)  # {1, 2, 3}
Frozen Set
Immutable version of a set.


frozen = frozenset({1, 2, 3})
✅ 7. Boolean Type — bool
Represents logical values: True or False.


a = True
b = False
print(a and b)  # False
Booleans are subclasses of integers (True = 1, False = 0).


print(True + True + False)  # 2
💾 8. Binary Types
Used for binary data (e.g., images, files).


b = b"Python"           # bytes
arr = bytearray(b)      # mutable version
mem = memoryview(b)     # view without copying data
🚫 9. None Type
Represents the absence of a value.


x = None
print(type(x))  # <class 'NoneType'>
Commonly used for default function arguments or placeholders.

🧠 10. Type Conversion (Type Casting)
Convert between data types using built-in functions.


x = int(3.14)       # float → int (3)
y = float(5)        # int → float (5.0)
z = str(10)         # int → string ("10")
⚖️ 11. Mutable vs Immutable Types
Mutable (Can Change)	Immutable (Cannot Change)
list	int
dict	float
set	str
bytearray	tuple
frozenset
bytes

Example:


# Mutable
nums = [1, 2, 3]
nums.append(4)
print(nums)  # [1, 2, 3, 4]

# Immutable
name = "Alice"
name = name + " Smith"
print(name)  # "Alice Smith" (new string created)