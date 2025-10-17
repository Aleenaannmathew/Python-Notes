🌀 Type Conversions in Python

Type conversion means changing the data type of a variable from one type to another.
Python supports two kinds of conversions:

Implicit Type Conversion (Type Casting done by Python)

Explicit Type Conversion (Manually done by the programmer)

🔹 1. Implicit Type Conversion

Also known as type coercion, this happens automatically when Python converts one data type to another during an operation.

Python automatically promotes smaller data types to larger data types to prevent data loss.

✅ Example:
a = 5          # int
b = 2.5        # float

result = a + b # int + float = float
print(result)  # 7.5
print(type(result))  # <class 'float'>


➡️ Here, Python automatically converted a (int) to a float before performing addition.

🧩 Example: Mixing bool, int, and float
x = True   # bool (1)
y = 10     # int

print(x + y)       # 11
print(type(x + y)) # <class 'int'>


➡️ True behaves like 1, and the result is automatically converted to int.

⚠️ Note:

Python only allows safe conversions (no data loss).
For example, it will not automatically convert a string to an integer:

a = "10"
b = 5
# print(a + b)   # ❌ TypeError: can only concatenate str (not "int") to str

🔹 2. Explicit Type Conversion (Type Casting)

Here, we manually convert the type of an object using built-in functions.

Common Built-in Type Conversion Functions
Function	Description	Example
int(x)	Converts x to an integer	int(5.6) → 5, int("10") → 10
float(x)	Converts x to a floating-point number	float(3) → 3.0, float("2.5") → 2.5
str(x)	Converts x to a string	str(25) → "25"
bool(x)	Converts x to a boolean	bool(0) → False, bool("Hello") → True
list(x)	Converts x to a list	list((1,2,3)) → [1,2,3]
tuple(x)	Converts x to a tuple	tuple([1,2,3]) → (1,2,3)
set(x)	Converts x to a set	set([1,2,2,3]) → {1,2,3}
dict(x)	Converts a sequence of key-value pairs into a dictionary	dict([(1, 'a'), (2, 'b')]) → {1:'a', 2:'b'}
complex(x, y)	Creates a complex number	complex(2, 3) → (2+3j)
✅ Example 1: Integer to String
x = 100
y = str(x)
print(y, type(y))  # "100" <class 'str'>

✅ Example 2: String to Float
x = "12.5"
y = float(x)
print(y, type(y))  # 12.5 <class 'float'>

✅ Example 3: Tuple to List
x = (1, 2, 3)
y = list(x)
print(y, type(y))  # [1, 2, 3] <class 'list'>

✅ Example 4: Boolean Conversion
print(bool(0))       # False
print(bool(1))       # True
print(bool(""))      # False
print(bool("Hi"))    # True
print(bool([]))      # False
print(bool([1,2,3])) # True

⚠️ Invalid Conversions

Some conversions are not possible and will raise ValueError or TypeError:

int("hello")   # ❌ ValueError: invalid literal for int()
tuple(5)       # ❌ TypeError: 'int' object is not iterable
