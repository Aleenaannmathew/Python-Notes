🟢 Sets in Python
🧠 What is a Set?

A set is an unordered, mutable collection of unique elements.

Unordered: Items do not maintain any order.

Mutable: Elements can be added or removed.

Unique Elements: Duplicates are automatically removed.

Hashable Elements: Only hashable (immutable) items like numbers, strings, and tuples can be elements of a set.

✅ Example
fruits = {"apple", "banana", "cherry"}
numbers = {1, 2, 3, 4}
mixed = {1, "apple", (2, 3)}

🔹 1. Creating Sets
a) Using Curly Braces { }
my_set = {1, 2, 3, 4}

b) Using set() Constructor
my_set = set([1, 2, 3, 4])
empty_set = set()  # {} creates an empty dictionary, not a set

🔹 2. Characteristics of Sets
Property	Description
Unordered	Elements have no specific index
Mutable	Can add/remove elements
Unique Elements	No duplicates allowed
No Indexing or Slicing	You cannot access elements by index
Iterable	Can loop through using for-loops
🔹 3. Adding Elements
Method	Description	Example
add()	Adds a single element	my_set.add(5)
update()	Adds multiple elements from iterable	my_set.update([6, 7, 8])
numbers = {1, 2, 3}
numbers.add(4)
numbers.update([5, 6, 7])
print(numbers)  # {1, 2, 3, 4, 5, 6, 7}

🔹 4. Removing Elements
Method	Description	Example
remove()	Removes element, raises KeyError if not found	my_set.remove(2)
discard()	Removes element, does NOT raise error if not found	my_set.discard(10)
pop()	Removes and returns a random element	my_set.pop()
clear()	Removes all elements	my_set.clear()
🔹 5. Set Operations

Sets support mathematical operations like union, intersection, difference, etc.

a) Union (| or union())
a = {1, 2, 3}
b = {3, 4, 5}
print(a | b)        # {1, 2, 3, 4, 5}
print(a.union(b))   # {1, 2, 3, 4, 5}

b) Intersection (& or intersection())
print(a & b)            # {3}
print(a.intersection(b)) # {3}

c) Difference (- or difference())
print(a - b)          # {1, 2}
print(a.difference(b)) # {1, 2}

d) Symmetric Difference (^ or symmetric_difference())
print(a ^ b)              # {1, 2, 4, 5}
print(a.symmetric_difference(b)) # {1, 2, 4, 5}

🔹 6. Subset, Superset, Disjoint
a = {1, 2, 3}
b = {1, 2, 3, 4, 5}

print(a.issubset(b))   # True
print(b.issuperset(a)) # True

c = {6, 7}
print(a.isdisjoint(c)) # True

🔹 7. Iterating Through Sets
fruits = {"apple", "banana", "cherry"}
for fruit in fruits:
    print(fruit)


⚠️ Remember: Order is not guaranteed.

🔹 8. Frozenset (Immutable Set)

frozenset is immutable; cannot add or remove elements.

Useful as dictionary keys or set elements.

f_set = frozenset([1, 2, 3])
print(f_set)  # frozenset({1, 2, 3})
# f_set.add(4) → Error

🔹 9. Set Comprehensions

Similar to list comprehensions:

squares = {x**2 for x in range(5)}
print(squares)  # {0, 1, 4, 9, 16}

even_squares = {x**2 for x in range(10) if x % 2 == 0}
print(even_squares)  # {0, 4, 16, 36, 64}

🔹 10. Practical Uses of Sets

Remove duplicates from a list

numbers = [1, 2, 2, 3, 3, 3]
unique_numbers = set(numbers)
print(unique_numbers)  # {1, 2, 3}


Membership testing (fast)

fruits = {"apple", "banana", "cherry"}
print("apple" in fruits)  # True


Mathematical operations

a = {1, 2, 3}
b = {2, 3, 4}
common = a & b
all_elements = a | b

🔹 11. Set vs List vs Dictionary
Feature	Set	List	Dictionary
Ordered	No	Yes	No (3.7+ preserves order)
Mutable	Yes	Yes	Yes
Unique Elements	Yes	No	Keys are unique
Indexed	No	Yes	Keys are used for indexing
Lookup Time	O(1) average	O(n)	O(1) average