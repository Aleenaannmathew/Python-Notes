🔗 Tuples in Python
🧠 What is a Tuple?

A tuple is an ordered, immutable collection of items.
Like lists, tuples can store multiple elements of different data types, but they cannot be modified once created.

✅ Example
fruits = ("apple", "banana", "cherry")
numbers = (1, 2, 3, 4)
mixed = (1, "Hello", 3.14, True)
nested = ((1, 2), (3, 4))

🔹 1. Tuple Characteristics
Property	Description	Example
Ordered	Elements maintain insertion order	(10, 20, 30)
Immutable	Cannot change items after creation	t[0] = 99 ❌
Heterogeneous	Can store different types	(1, "A", 3.5)
Indexed	Access elements via index	t[0], t[-1]
Allow Duplicates	Duplicates are allowed	(1, 2, 2, 3)
🔹 2. Creating Tuples
a) Using Parentheses
t = (1, 2, 3)

b) Using the tuple() Constructor
t = tuple([1, 2, 3])

c) Without Parentheses (Tuple Packing)
t = 1, 2, 3
print(type(t))  # <class 'tuple'>

d) Empty Tuple
empty = ()

e) Single-Element Tuple ⚠️

To create a one-item tuple, add a comma:

single = (5,)  # ✅ Tuple
not_tuple = (5)  # ❌ int

🔹 3. Accessing Tuple Elements
a) Positive Indexing
colors = ("red", "green", "blue")
print(colors[0])  # red

b) Negative Indexing
print(colors[-1])  # blue
print(colors[-2])  # green

c) Nested Tuples
nested = (1, (2, 3), (4, 5, 6))
print(nested[1][0])  # 2
print(nested[2][2])  # 6

🔹 4. Slicing Tuples

Tuples support slicing like lists.

t = (10, 20, 30, 40, 50)
print(t[1:4])   # (20, 30, 40)
print(t[:3])    # (10, 20, 30)
print(t[::2])   # (10, 30, 50)
print(t[::-1])  # (50, 40, 30, 20, 10)

🔹 5. Tuple Immutability

Tuples cannot be modified after creation.

t = (1, 2, 3)
# t[1] = 100  ❌ TypeError


However, if a tuple contains mutable elements (like lists), those can change.

t = (1, [2, 3], 4)
t[1][0] = 99
print(t)  # (1, [99, 3], 4)


🧩 Immutability applies to the tuple structure, not necessarily to its contents.

🔹 6. Tuple Operations
a) Concatenation
a = (1, 2)
b = (3, 4)
print(a + b)  # (1, 2, 3, 4)

b) Repetition
a = (1, 2)
print(a * 3)  # (1, 2, 1, 2, 1, 2)

c) Membership Testing
colors = ("red", "green", "blue")
print("red" in colors)   # True
print("yellow" not in colors)  # True

🔹 7. Iterating Through Tuples
Using a for Loop
t = ("apple", "banana", "cherry")
for item in t:
    print(item)

Using Index
for i in range(len(t)):
    print(i, t[i])

🔹 8. Tuple Unpacking

Unpacking lets you assign tuple elements to multiple variables.

person = ("John", 25, "Engineer")
name, age, profession = person

print(name)        # John
print(age)         # 25
print(profession)  # Engineer

With * (Asterisk) for Variable-Length Unpacking
numbers = (1, 2, 3, 4, 5)
a, b, *rest = numbers
print(a, b, rest)  # 1 2 [3, 4, 5]


Another example:

a, *middle, b = (10, 20, 30, 40, 50)
print(a)      # 10
print(middle) # [20, 30, 40]
print(b)      # 50

🔹 9. Built-in Tuple Functions
Function	Description	Example
len(t)	Returns length	len((1,2,3)) → 3
max(t)	Maximum element	max((3,1,2)) → 3
min(t)	Minimum element	min((3,1,2)) → 1
sum(t)	Sum of numeric elements	sum((1,2,3)) → 6
any(t)	Returns True if any element is truthy	any((0, '', 5)) → True
all(t)	Returns True if all elements are truthy	all((1, 2, 3)) → True
sorted(t)	Returns a sorted list	sorted((3,1,2)) → [1,2,3]
🔹 10. Tuple Methods

Tuples have only two methods because they’re immutable:

Method	Description	Example
count(x)	Returns count of occurrences of x	(1,2,2,3).count(2) → 2
index(x)	Returns first index of x	(10,20,30).index(20) → 1
🔹 11. Nested Tuples

Tuples can contain other tuples:

nested = ((1, 2), (3, 4), (5, 6))
print(nested[1][0])  # 3


They are often used to represent immutable matrices or coordinate pairs.

🔹 12. Tuple vs List
Feature	Tuple	List
Syntax	( )	[ ]
Mutability	Immutable	Mutable
Performance	Faster	Slower
Memory Usage	Less	More
Methods	Fewer (count, index)	Many (append, extend, etc.)
Suitable For	Fixed data	Dynamic data
Hashable	✅ (if immutable)	❌
🔹 13. Tuples as Dictionary Keys

Since tuples are immutable, they can be used as dictionary keys (lists cannot).

locations = {
    (10.5, 20.7): "City A",
    (15.2, 18.9): "City B"
}
print(locations[(10.5, 20.7)])  # City A

🔹 14. Tuple Packing and Unpacking Together
# Packing
data = ("Alice", 23, "Designer")

# Unpacking
name, age, profession = data
print(f"{name} is a {profession} aged {age}.")

🔹 15. Using Tuples in Functions

Tuples are often used for returning multiple values from a function.

def calculate(a, b):
    add = a + b
    sub = a - b
    return add, sub  # returns a tuple

result = calculate(10, 5)
print(result)  # (15, 5)

add, sub = calculate(10, 5)
print(add, sub)  # 15 5

🔹 16. Tuple Comprehensions?

❌ There are no tuple comprehensions in Python.
✅ But you can use generator expressions and convert them to tuples.

t = tuple(x**2 for x in range(5))
print(t)  # (0, 1, 4, 9, 16)

🔹 17. Performance Advantage of Tuples

Tuples are:

Faster than lists (less overhead).

More memory-efficient.

Hashable → can be used in sets and as dictionary keys.

Useful when you want fixed data that should not be modified.

Example:
import sys, timeit

a_list = [1, 2, 3, 4, 5]
a_tuple = (1, 2, 3, 4, 5)

print(sys.getsizeof(a_list))   # Larger
print(sys.getsizeof(a_tuple))  # Smaller

print(timeit.timeit(stmt="(1,2,3,4,5)", number=1000000))
print(timeit.timeit(stmt="[1,2,3,4,5]", number=1000000))

🔹 18. Converting Between Tuples and Lists
# Tuple → List
t = (1, 2, 3)
lst = list(t)
print(lst)  # [1, 2, 3]

# List → Tuple
lst = [4, 5, 6]
t = tuple(lst)
print(t)  # (4, 5, 6)