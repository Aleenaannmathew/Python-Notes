🟢 Shallow Copy vs Deep Copy in Python — Detailed Explanation
🔹 1. What is Copying in Python?

In Python, copying an object means creating a new object with the same content as the original.

There are two types of copies:

Shallow Copy – copies only the top-level object.

Deep Copy – copies the object and all objects nested inside it recursively.

🔹 2. Shallow Copy

A shallow copy creates a new object, but the nested objects are shared between the original and the copy.

Changes to nested objects in the copy affect the original.

Changes to top-level object do not affect the original.

How to create a shallow copy

Using slice (for lists)

Using copy.copy() from the copy module

Using constructors (e.g., list(), dict())

Example:
import copy

original = [[1, 2], [3, 4]]

shallow = copy.copy(original)

print("Original:", original)
print("Shallow Copy:", shallow)

# Modify top-level object
shallow.append([5, 6])
print("After modifying top-level in shallow copy:")
print("Original:", original)
print("Shallow:", shallow)

# Modify nested object
shallow[0][0] = 99
print("After modifying nested object:")
print("Original:", original)
print("Shallow:", shallow)


Output:

Original: [[1, 2], [3, 4]]
Shallow Copy: [[1, 2], [3, 4]]
After modifying top-level in shallow copy:
Original: [[1, 2], [3, 4]]
Shallow: [[1, 2], [3, 4], [5, 6]]
After modifying nested object:
Original: [[99, 2], [3, 4]]
Shallow: [[99, 2], [3, 4], [5, 6]]


✅ Key Point: Nested objects are shared; top-level objects are separate.

🔹 3. Deep Copy

A deep copy creates a new object and recursively copies all nested objects.

Changes to the copy do not affect the original, at any level.

Useful when you need a completely independent copy of complex objects.

How to create a deep copy

Use copy.deepcopy() from the copy module.

Example:
import copy

original = [[1, 2], [3, 4]]

deep = copy.deepcopy(original)

# Modify nested object in deep copy
deep[0][0] = 99

print("Original:", original)
print("Deep Copy:", deep)


Output:

Original: [[1, 2], [3, 4]]
Deep Copy: [[99, 2], [3, 4]]


✅ Key Point: Nested objects are fully independent.

🔹 4. Shallow vs Deep Copy Table
Feature	Shallow Copy	Deep Copy
Copies top-level object	✅ Yes	✅ Yes
Copies nested objects	❌ No	✅ Yes
Memory overhead	Low	Higher
Independent nested objects	❌ No	✅ Yes
Module function	copy.copy()	copy.deepcopy()
🔹 5. When to Use Which?

Shallow Copy:
When your object is simple or you don’t need full independence for nested objects.

Deep Copy:
When working with nested/mutable objects and you need full independence from the original.

🔹 6. Built-in Alternatives for Copying

List copy – new_list = old_list[:]

Dict copy – new_dict = old_dict.copy()

Set copy – new_set = old_set.copy()

These methods are equivalent to shallow copy.

🔹 7. Summary

Shallow Copy: Top-level object copied, nested objects shared.

Deep Copy: Top-level and nested objects copied recursively, fully independent.

Python provides copy module for both types of copies.

Choose shallow or deep copy based on independence needs and object complexity.