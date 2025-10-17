🧺 Lists in Python
🧠 What is a List?

A list in Python is an ordered, mutable (changeable), and iterable collection of items.
It can hold elements of different data types, including numbers, strings, objects, or even other lists.

✅ Example
fruits = ["apple", "banana", "cherry"]
numbers = [1, 2, 3, 4, 5]
mixed = [10, "hello", 3.14, True]
nested = [1, [2, 3], [4, 5, 6]]

🔹 1. List Characteristics
Property	Description	Example
Ordered	Elements maintain insertion order	[10, 20, 30] → Order is preserved
Mutable	Elements can be changed	lst[1] = 100
Heterogeneous	Can contain different data types	[1, "A", 3.14]
Indexed	Supports positive and negative indexing	lst[0], lst[-1]
Iterable	Can be looped through using for	for x in lst:
🔹 2. Creating Lists
a) Using Square Brackets
my_list = [1, 2, 3]

b) Using the list() Constructor
my_list = list((1, 2, 3))

c) Empty List
empty = []
# or
empty = list()

🔹 3. Accessing Elements
a) Positive Indexing
fruits = ["apple", "banana", "cherry"]
print(fruits[0])  # apple
print(fruits[2])  # cherry

b) Negative Indexing
print(fruits[-1])  # cherry
print(fruits[-2])  # banana

c) Nested List Access
nested = [1, [2, 3], [4, 5, 6]]
print(nested[1][0])  # 2
print(nested[2][2])  # 6

🔹 4. List Slicing

You can extract a portion of a list using slicing syntax.

Syntax:

list[start:end:step]


Example:

nums = [10, 20, 30, 40, 50, 60]
print(nums[1:4])   # [20, 30, 40]
print(nums[:3])    # [10, 20, 30]
print(nums[3:])    # [40, 50, 60]
print(nums[::2])   # [10, 30, 50]
print(nums[::-1])  # [60, 50, 40, 30, 20, 10]

🔹 5. Modifying Lists
a) Changing Elements
fruits = ["apple", "banana", "cherry"]
fruits[1] = "mango"
print(fruits)  # ['apple', 'mango', 'cherry']

b) Adding Elements
Method	Description	Example
append()	Adds an item at the end	fruits.append("orange")
insert()	Adds at a specific position	fruits.insert(1, "kiwi")
extend()	Adds elements from another list	fruits.extend(["grape", "melon"])

Example:

fruits = ["apple", "banana"]
fruits.append("cherry")
fruits.insert(1, "mango")
fruits.extend(["kiwi", "melon"])
print(fruits)
# ['apple', 'mango', 'banana', 'cherry', 'kiwi', 'melon']

c) Removing Elements
Method	Description	Example
remove()	Removes the first matching value	fruits.remove("banana")
pop()	Removes by index and returns it	fruits.pop(1)
del	Deletes by index or slice	del fruits[0]
clear()	Removes all elements	fruits.clear()

Example:

fruits = ["apple", "banana", "cherry", "banana"]
fruits.remove("banana")
print(fruits)  # ['apple', 'cherry', 'banana']
fruits.pop(1)
print(fruits)  # ['apple', 'banana']
del fruits[0]
print(fruits)  # ['banana']
fruits.clear()
print(fruits)  # []

🔹 6. Looping Through Lists
a) For Loop
fruits = ["apple", "banana", "cherry"]
for fruit in fruits:
    print(fruit)

b) Using Index with range()
for i in range(len(fruits)):
    print(i, fruits[i])

c) Using enumerate()
for index, fruit in enumerate(fruits):
    print(index, fruit)

🔹 7. List Comprehensions

A concise way to create lists.

Example 1 – Simple
squares = [x**2 for x in range(5)]
print(squares)  # [0, 1, 4, 9, 16]

Example 2 – With Condition
even = [x for x in range(10) if x % 2 == 0]
print(even)  # [0, 2, 4, 6, 8]

Example 3 – Nested Loops
pairs = [(x, y) for x in [1, 2] for y in [3, 4]]
print(pairs)  # [(1,3), (1,4), (2,3), (2,4)]

🔹 8. Common List Methods
Method	Description	Example
append(x)	Adds item x to the end	lst.append(10)
extend(iterable)	Adds all elements from iterable	lst.extend([1,2,3])
insert(i, x)	Inserts x at position i	lst.insert(1, 'A')
remove(x)	Removes first occurrence of x	lst.remove('A')
pop([i])	Removes and returns element at index i	lst.pop()
clear()	Removes all elements	lst.clear()
index(x)	Returns index of first occurrence	lst.index('A')
count(x)	Returns count of x	lst.count(2)
sort()	Sorts in ascending order	lst.sort()
reverse()	Reverses list order	lst.reverse()
copy()	Returns a shallow copy	lst2 = lst.copy()
🔹 9. Sorting Lists
a) Ascending Order
nums = [3, 1, 4, 2]
nums.sort()
print(nums)  # [1, 2, 3, 4]

b) Descending Order
nums.sort(reverse=True)
print(nums)  # [4, 3, 2, 1]

c) Custom Sort Using key
words = ["apple", "banana", "kiwi"]
words.sort(key=len)
print(words)  # ['kiwi', 'apple', 'banana']

🔹 10. Copying Lists
a) Shallow Copy (Creates new list with same elements)
a = [1, 2, 3]
b = a.copy()
b.append(4)
print(a)  # [1, 2, 3]
print(b)  # [1, 2, 3, 4]

b) Using list() Constructor
b = list(a)

c) Using Slicing
b = a[:]

🔹 11. Nested Lists

Lists inside lists.

matrix = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
print(matrix[1][2])  # 6


You can iterate through nested lists:

for row in matrix:
    for col in row:
        print(col, end=" ")

🔹 12. Membership Testing
fruits = ["apple", "banana", "cherry"]
print("banana" in fruits)   # True
print("grape" not in fruits)  # True

🔹 13. Built-in Functions for Lists
Function	Description	Example
len(lst)	Returns number of elements	len([1,2,3]) → 3
sum(lst)	Sum of numeric items	sum([1,2,3]) → 6
max(lst)	Maximum value	max([1,5,2]) → 5
min(lst)	Minimum value	min([1,5,2]) → 1
sorted(lst)	Returns a new sorted list	sorted([3,1,2]) → [1,2,3]
🔹 14. Mutable Nature of Lists

When you assign one list to another, both refer to the same object.

a = [1, 2, 3]
b = a
b.append(4)
print(a)  # [1, 2, 3, 4] → a is also changed!


Use .copy() or slicing for independent copies.