🟢 Lambda Functions in Python (Anonymous Functions)
🧠 What is a Lambda Function?

A lambda function is a small, anonymous function defined without using the def keyword.

It can take any number of arguments but can contain only one expression.

It’s often used when a short function is needed temporarily.

🔹 1. Syntax
lambda arguments: expression


Example:

square = lambda x: x ** 2
print(square(5))  # Output: 25


Equivalent to:

def square(x):
    return x ** 2


✅ Both return the same result, but lambda is more concise.

🔹 2. Characteristics of Lambda Functions
Feature	Description
Keyword	Uses lambda instead of def
Expression	Must contain only one expression
Return	Automatically returns the result of the expression
Scope	Behaves like a normal function
Usage	Best for short-term or one-line operations
🔹 3. Multiple Arguments

Lambda functions can take multiple arguments, just like regular functions.

add = lambda a, b: a + b
print(add(10, 20))  # Output: 30

max_of_three = lambda a, b, c: a if (a > b and a > c) else (b if b > c else c)
print(max_of_three(5, 10, 3))  # Output: 10

🔹 4. Using Lambda with Built-in Functions

Lambda functions are often used with higher-order functions like:

map()

filter()

reduce()

sorted()

🟠 a) With map()

Applies a function to every element in an iterable.

numbers = [1, 2, 3, 4]
squares = list(map(lambda x: x ** 2, numbers))
print(squares)  # [1, 4, 9, 16]


Equivalent using normal function:

def square(x):
    return x ** 2
squares = list(map(square, numbers))

🟠 b) With filter()

Filters elements based on a condition.

numbers = [1, 2, 3, 4, 5, 6]
even = list(filter(lambda x: x % 2 == 0, numbers))
print(even)  # [2, 4, 6]

🟠 c) With reduce()

Performs cumulative computation (requires functools module).

from functools import reduce

numbers = [1, 2, 3, 4]
product = reduce(lambda x, y: x * y, numbers)
print(product)  # 24

🟠 d) With sorted()

Use lambda as a key function.

students = [("Alice", 25), ("Bob", 20), ("Charlie", 23)]
sorted_students = sorted(students, key=lambda x: x[1])
print(sorted_students)  # [('Bob', 20), ('Charlie', 23), ('Alice', 25)]

🔹 5. Conditional Expressions in Lambda

You can use ternary conditional statements inside a lambda function.

check_even = lambda x: "Even" if x % 2 == 0 else "Odd"
print(check_even(7))  # Odd

🔹 6. Lambda Inside Other Functions

Lambda can be used within another function to define quick operations.

def make_multiplier(n):
    return lambda x: x * n

double = make_multiplier(2)
triple = make_multiplier(3)

print(double(5))  # 10
print(triple(5))  # 15

🔹 7. Lambda with List Comprehension

Combine lambda and comprehension for compact transformations.

nums = [1, 2, 3, 4]
result = [(lambda x: x ** 2)(x) for x in nums]
print(result)  # [1, 4, 9, 16]

🔹 8. Sorting with Multiple Conditions

You can use multiple keys for sorting tuples or dictionaries.

students = [
    {"name": "Alice", "score": 90},
    {"name": "Bob", "score": 85},
    {"name": "Charlie", "score": 95}
]
sorted_students = sorted(students, key=lambda s: (-s["score"], s["name"]))
print(sorted_students)
# [{'name': 'Charlie', 'score': 95}, {'name': 'Alice', 'score': 90}, {'name': 'Bob', 'score': 85}]

🔹 9. Limitations of Lambda Functions

Single expression only — cannot contain multiple statements.

No name (anonymous) — harder to debug or reuse.

Reduced readability for complex logic.

Cannot include annotations or docstrings.

Example (❌ invalid):

# Can't have multiple statements
lambda x: y = x + 1; print(y)

🔹 10. When to Use Lambda Functions

✅ Good Use Cases:

Short-lived operations

Inside higher-order functions (map, filter, sorted)

Inline logic in one-liners

❌ Avoid When:

Function is complex

You need multiple statements or documentation

🔹 11. Lambda vs def Functions
Feature	Lambda	def
Syntax	Single-line	Multi-line
Return	Implicit	Explicit return
Name	Anonymous	Named
Reusability	Limited	Reusable
Docstring	Not supported	Supported
Debugging	Harder	Easier
🔹 12. Advanced Example – Custom Sort and Map
words = ["apple", "banana", "grape", "kiwi", "pear"]

# Sort by length, then alphabetically
sorted_words = sorted(words, key=lambda x: (len(x), x))
print(sorted_words)  # ['kiwi', 'pear', 'apple', 'grape', 'banana']

# Convert all to uppercase using map
upper_words = list(map(lambda w: w.upper(), words))
print(upper_words)  # ['APPLE', 'BANANA', 'GRAPE', 'KIWI', 'PEAR']
