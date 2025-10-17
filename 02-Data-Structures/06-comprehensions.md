🟢 Comprehensions in Python
🧠 What are Comprehensions?

Comprehensions are a concise way to create sequences or collections in Python using a single line of code.

They make code shorter, readable, and Pythonic.

Can be applied to lists, sets, dictionaries, and generators.

🔹 1. List Comprehension

Syntax:

[expression for item in iterable if condition]

✅ Examples

Basic list comprehension

numbers = [1, 2, 3, 4, 5]
squares = [n**2 for n in numbers]
print(squares)  # [1, 4, 9, 16, 25]


With condition

numbers = [1, 2, 3, 4, 5]
even_squares = [n**2 for n in numbers if n % 2 == 0]
print(even_squares)  # [4, 16]


Nested list comprehension

matrix = [[1, 2], [3, 4], [5, 6]]
flatten = [num for row in matrix for num in row]
print(flatten)  # [1, 2, 3, 4, 5, 6]

🔹 2. Dictionary Comprehension

Syntax:

{key_expression: value_expression for item in iterable if condition}

✅ Examples

Basic dictionary comprehension

numbers = [1, 2, 3, 4]
squares_dict = {n: n**2 for n in numbers}
print(squares_dict)  # {1: 1, 2: 4, 3: 9, 4: 16}


With condition

even_squares_dict = {n: n**2 for n in numbers if n % 2 == 0}
print(even_squares_dict)  # {2: 4, 4: 16}


From two lists

keys = ['a', 'b', 'c']
values = [1, 2, 3]
my_dict = {k: v for k, v in zip(keys, values)}
print(my_dict)  # {'a': 1, 'b': 2, 'c': 3}

🔹 3. Set Comprehension

Syntax:

{expression for item in iterable if condition}

✅ Examples

Basic set comprehension

numbers = [1, 2, 2, 3, 4, 4]
unique_squares = {n**2 for n in numbers}
print(unique_squares)  # {16, 1, 4, 9}


With condition

even_squares = {n**2 for n in numbers if n % 2 == 0}
print(even_squares)  # {16, 4}


🔹 Note: Sets automatically remove duplicates.

🔹 4. Generator Comprehension

Similar to list comprehension but uses parentheses ()

Returns a generator object (lazy evaluation, memory-efficient)

Can be iterated or converted to a list

Syntax:

(expression for item in iterable if condition)

✅ Examples
numbers = [1, 2, 3, 4, 5]
gen = (n**2 for n in numbers)
print(gen)         # <generator object ...>
print(list(gen))   # [1, 4, 9, 16, 25]

🔹 5. Nested Comprehensions
a) Nested List
matrix = [[1, 2], [3, 4], [5, 6]]
flatten = [num for row in matrix for num in row]
print(flatten)  # [1, 2, 3, 4, 5, 6]

b) Nested Dictionary
dict1 = {i: {j: j*i for j in range(1, 4)} for i in range(1, 4)}
print(dict1)
# {1: {1: 1, 2: 2, 3: 3}, 2: {1: 2, 2: 4, 3: 6}, 3: {1: 3, 2: 6, 3: 9}}

🔹 6. Conditional Expressions

Can use if-else inside comprehension:

numbers = [1, 2, 3, 4, 5]
labels = ["Even" if n % 2 == 0 else "Odd" for n in numbers]
print(labels)  # ['Odd', 'Even', 'Odd', 'Even', 'Odd']

🔹 7. Advantages of Comprehensions

Shorter and readable code.

Efficient in memory usage (especially generator comprehensions).

Easy to apply conditions and nested loops.

Widely used in data processing, filtering, and transformations.

🔹 8. When Not to Use Comprehensions

Avoid overly complex nested comprehensions → reduces readability.

Use loops if multiple operations are needed in each iteration.