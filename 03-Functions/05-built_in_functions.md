🟢 Python Built-in Functions — Detailed Explanation

Python provides over 70 built-in functions that are always available without importing any library. They are ready-to-use, optimized, and essential for everyday programming.

🔹 1. Numeric Functions
Function	Description	Example
abs(x)	Returns the absolute value of a number	abs(-5) → 5
round(x, n)	Rounds a number x to n decimal places	round(3.14159, 2) → 3.14
pow(x, y[, z])	Returns x**y. If z is given, returns x**y % z	pow(2, 3) → 8
divmod(a, b)	Returns a tuple (quotient, remainder)	divmod(9, 2) → (4, 1)
max(iterable) / min(iterable)	Returns maximum / minimum value	max([1, 5, 3]) → 5
🔹 Type Conversion Functions
Function	Description	Example
int(x)	Converts x to integer	int("10") → 10
float(x)	Converts x to float	float("3.5") → 3.5
str(x)	Converts x to string	str(100) → '100'
bool(x)	Converts x to boolean	bool(0) → False
list(iterable)	Converts iterable to list	list((1,2,3)) → [1,2,3]
tuple(iterable)	Converts iterable to tuple	tuple([1,2]) → (1,2)
set(iterable)	Converts iterable to set	set([1,2,2]) → {1,2}
dict()	Creates a dictionary	dict(a=1, b=2) → {'a':1,'b':2}
🔹 Sequence & Iterable Functions
Function	Description	Example
len(obj)	Returns length of object	len([1,2,3]) → 3
sum(iterable)	Returns sum of elements	sum([1,2,3]) → 6
sorted(iterable, key=None, reverse=False)	Returns a sorted list	sorted([3,1,2]) → [1,2,3]
reversed(iterable)	Returns an iterator in reverse order	list(reversed([1,2,3])) → [3,2,1]
enumerate(iterable, start=0)	Returns index-value pairs	list(enumerate(['a','b'])) → [(0,'a'),(1,'b')]
zip(*iterables)	Combines iterables element-wise	list(zip([1,2],[3,4])) → [(1,3),(2,4)]
all(iterable)	Returns True if all elements are True	all([True, True]) → True
any(iterable)	Returns True if any element is True	any([False, True]) → True
🔹 String Functions
Function	Description	Example
chr(i)	Returns character for Unicode i	chr(97) → 'a'
ord(c)	Returns Unicode code of character	ord('a') → 97
format(value, format_spec)	Formats a value	format(3.14159, ".2f") → '3.14'
repr(obj)	Returns string representation	repr("Hello") → "'Hello'"
🔹 Object & Attribute Functions
Function	Description	Example
type(obj)	Returns the type of an object	type(5) → <class 'int'>
id(obj)	Returns unique ID of object	id(5) → 1407234672
isinstance(obj, classinfo)	Checks if object is instance of class	isinstance(5, int) → True
hasattr(obj, attr)	Checks if object has attribute	hasattr([], 'append') → True
getattr(obj, attr[, default])	Returns attribute value	getattr([], 'append') → <built-in method append of list object>
setattr(obj, attr, value)	Sets attribute value	setattr(obj, 'x', 5)
delattr(obj, attr)	Deletes attribute	delattr(obj, 'x')
🔹 Functional Programming Helpers
Function	Description	Example
map(func, iterable)	Applies function to each item	list(map(lambda x:x*2, [1,2])) → [2,4]
filter(func, iterable)	Filters items based on function	list(filter(lambda x:x>1, [1,2,3])) → [2,3]
reduce(func, iterable) (from functools)	Reduces iterable to single value	from functools import reduce; reduce(lambda x,y:x+y,[1,2,3]) → 6
sorted(iterable, key=func)	Sort with key function	sorted(['apple','bat'], key=len) → ['bat','apple']
🔹 Other Useful Functions
Function	Description	Example
help(obj)	Shows documentation	help(len)
dir(obj)	Lists all attributes/methods	dir([])
id(obj)	Unique identifier of object	id(5)
eval(expr)	Evaluates string expression	eval('2+3') → 5
exec(code)	Executes code dynamically	exec('a=5')
input(prompt)	Accepts user input	input("Enter name: ")
open(file, mode)	Opens file	open("file.txt", "r")
abs(x)	Returns absolute value	abs(-5)
🔹 Key Notes

Always available — no import needed.

Highly optimized — faster than user-defined alternatives.

Many functions have optional parameters (sorted, round, pow).

Can be combined with lambda, map, filter, reduce for functional programming.

Knowledge of built-ins improves coding efficiency drastically.

🔹 Example — Using Multiple Built-ins
numbers = [3, 7, 2, 9]

# Max, Min, Sum
print(max(numbers))  # 9
print(min(numbers))  # 2
print(sum(numbers))  # 21

# Sorting in reverse
print(sorted(numbers, reverse=True))  # [9,7,3,2]

# Using map & lambda
squared = list(map(lambda x: x**2, numbers))
print(squared)  # [9,49,4,81]

# Enumerate
for idx, num in enumerate(numbers):
    print(idx, num)