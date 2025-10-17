🗂️ Dictionaries in Python
🧠 What is a Dictionary?

A dictionary is an unordered, mutable collection of key-value pairs.

Each key must be unique and hashable (e.g., strings, numbers, tuples).

Each value can be any Python object.

Dictionaries are mutable, meaning you can change, add, or remove items.

✅ Example
person = {
    "name": "Alice",
    "age": 25,
    "city": "New York"
}

numbers = {1: "one", 2: "two", 3: "three"}

mixed = {"name": "Bob", 1: [1, 2, 3], "is_student": True}

🔹 1. Characteristics of Dictionaries
Property	Description	Example
Unordered	Elements do not maintain insertion order (Python 3.7+ preserves insertion order)	{"a":1, "b":2}
Mutable	Can add, remove, or modify key-value pairs	d["x"] = 100
Key-Value Pair	Each item has a unique key and a value	"name": "Alice"
Keys Unique	Duplicate keys are not allowed	{"a":1, "a":2} → {"a":2}
Values Can Repeat	Values can be duplicated	{"x":10, "y":10}
🔹 2. Creating Dictionaries
a) Using Curly Braces { }
d = {"a": 1, "b": 2, "c": 3}

b) Using dict() Constructor
d = dict(a=1, b=2, c=3)

c) Using a List of Tuples
d = dict([("a", 1), ("b", 2)])

d) Empty Dictionary
empty = {}
empty = dict()

🔹 3. Accessing Dictionary Items
a) Using Key
person = {"name": "Alice", "age": 25}
print(person["name"])  # Alice


⚠️ Accessing a non-existent key raises a KeyError.

b) Using get() Method
print(person.get("name"))      # Alice
print(person.get("gender"))    # None
print(person.get("gender", "N/A"))  # N/A (default)

🔹 4. Adding or Updating Items
person = {"name": "Alice", "age": 25}

# Add
person["city"] = "New York"
print(person)  # {'name': 'Alice', 'age': 25, 'city': 'New York'}

# Update
person["age"] = 26
print(person)  # {'name': 'Alice', 'age': 26, 'city': 'New York'}

# Using update()
person.update({"age": 27, "country": "USA"})
print(person)  # {'name': 'Alice', 'age': 27, 'city': 'New York', 'country': 'USA'}

🔹 5. Removing Items
Method	Description	Example
del	Delete by key	del person["city"]
pop()	Remove by key and return value	age = person.pop("age")
popitem()	Remove and return last inserted key-value pair	k, v = person.popitem()
clear()	Remove all items	person.clear()
🔹 6. Dictionary Keys, Values, and Items
person = {"name": "Alice", "age": 25, "city": "NY"}

# Keys
print(person.keys())    # dict_keys(['name', 'age', 'city'])

# Values
print(person.values())  # dict_values(['Alice', 25, 'NY'])

# Items (key-value pairs)
print(person.items())   # dict_items([('name', 'Alice'), ('age', 25), ('city', 'NY')])

🔹 7. Iterating Over Dictionaries
a) Iterating through Keys
for key in person:
    print(key)

b) Iterating through Values
for value in person.values():
    print(value)

c) Iterating through Key-Value Pairs
for key, value in person.items():
    print(f"{key} → {value}")

🔹 8. Nested Dictionaries

Dictionaries can contain other dictionaries:

people = {
    "Alice": {"age": 25, "city": "NY"},
    "Bob": {"age": 30, "city": "LA"}
}

print(people["Alice"]["city"])  # NY

🔹 9. Dictionary Comprehensions

Like list comprehensions, dictionaries can be created dynamically:

# Squares of numbers
squares = {x: x**2 for x in range(5)}
print(squares)  # {0:0, 1:1, 2:4, 3:9, 4:16}

# Conditional comprehension
even_squares = {x: x**2 for x in range(10) if x % 2 == 0}
print(even_squares)  # {0:0, 2:4, 4:16, 6:36, 8:64}

🔹 10. Dictionary Methods Overview
Method	Description
copy()	Returns a shallow copy of dictionary
fromkeys(seq, value)	Creates a new dictionary with keys from seq and all values set to value
get(key, default)	Returns value for key, or default if key not found
items()	Returns view object of key-value pairs
keys()	Returns view object of keys
values()	Returns view object of values
pop(key[,default])	Removes specified key and returns value
popitem()	Removes last inserted key-value pair and returns it
setdefault(key, default)	Returns value if key exists, else sets key to default
update(other_dict)	Updates dictionary with key-value pairs from other_dict
clear()	Removes all items
🔹 11. Dictionary vs List
Feature	Dictionary	List
Access	By key (fast)	By index (slower for large data)
Order	Unordered (Python 3.7+ insertion order preserved)	Ordered
Mutability	Mutable	Mutable
Lookup Time	O(1) average	O(n)
Suitable For	Key-value storage	Sequence of items
🔹 12. Practical Uses of Dictionaries

Storing configuration settings

config = {"theme": "dark", "font_size": 12}


Counting occurrences

text = "hello world"
count = {}
for char in text:
    count[char] = count.get(char, 0) + 1
print(count)


Mapping IDs to objects

users = {101: "Alice", 102: "Bob"}


Fast lookups

data = {i: i*2 for i in range(1000)}
print(data[500])  # 1000

🔹 13. Dictionary Performance Tips

Dictionaries are optimized for fast lookups (hash tables).

Use get() to avoid KeyError.

Use setdefault() to initialize values safely.