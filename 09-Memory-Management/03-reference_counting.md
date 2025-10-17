🟢 Reference Counting in Python — Detailed Explanation
🔹 1. What is Reference Counting?

Reference counting is Python’s primary memory management technique.

Every object in Python has an associated reference count, which tracks how many references point to the object.

When the reference count drops to zero, Python automatically deallocates (frees) the memory occupied by the object.

🔹 2. How Reference Counting Works

Python stores an internal counter with each object.

Incremented when a new reference to the object is created.

Decremented when a reference is deleted or goes out of scope.

If the counter reaches 0, the object is destroyed.

Example:
import sys

a = [1, 2, 3]       # reference count of list object increases
b = a                # reference count increases again

print(sys.getrefcount(a))  # Shows 3 (a, b, and argument to getrefcount)

del b                # reference count decreases
print(sys.getrefcount(a))  # Shows 2


Note: sys.getrefcount() shows one extra count because the argument itself adds a temporary reference.

🔹 3. Reference Count Changes

Reference count changes in various situations:

Action	Effect on Reference Count
Assigning object to a variable	+1
Passing object to a function	+1 (temporary)
Returning object from a function	+1 (temporary)
Deleting variable using del	-1
Going out of scope	-1
🔹 4. Reference Counting Example
import sys

x = [10, 20]     # new list object
print(sys.getrefcount(x))  # e.g., 2

y = x            # new reference
print(sys.getrefcount(x))  # 3

del y            # delete one reference
print(sys.getrefcount(x))  # 2

x = None         # delete last reference
# Object is automatically destroyed

🔹 5. Reference Counting Limitations

Cannot handle circular references:
Objects that reference each other may never have their reference count reach zero.

class Node:
    def __init__(self, value):
        self.value = value
        self.next = None

a = Node(1)
b = Node(2)

a.next = b
b.next = a   # circular reference

del a
del b
# Memory is not freed because reference count != 0


Solution: Python uses Garbage Collection to clean up such cycles.

Overhead:
Every assignment or deletion operation updates the reference count, which is a minor runtime overhead.

🔹 6. Reference Counting vs Garbage Collection
Feature	Reference Counting	Garbage Collection
Primary mechanism	✅ Yes	❌ No
Detects circular references	❌ No	✅ Yes
Immediate deallocation	✅ Yes	❌ Usually later
Performance overhead	Low	Slightly higher

Reference counting handles most objects efficiently, while GC handles complex cycles.

🔹 7. Tools for Reference Counting

sys.getrefcount(obj) → Check reference count

gc.get_referrers(obj) → Objects referring to obj

gc.get_referents(obj) → Objects referred by obj

import gc

a = [1, 2, 3]
print(gc.get_referrers(a))
print(gc.get_referents(a))

🔹 8. Summary

Reference counting is automatic memory management in Python.

Every object has a counter tracking references.

When count = 0 → object is deleted.

Limitation: Cannot handle circular references, which GC solves.

Reference counting is fast and works for most scenarios.