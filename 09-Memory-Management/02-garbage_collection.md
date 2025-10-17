🟢 Garbage Collection in Python — Detailed Explanation
🔹 1. What is Garbage Collection?

Garbage collection (GC) is the process by which Python automatically identifies and frees memory occupied by objects that are no longer in use.

This helps in preventing memory leaks.

Python’s GC complements reference counting, handling cyclic references that reference counting alone cannot resolve.

🔹 2. Reference Counting Limitation

Python primarily uses reference counting to manage memory.

Every object has a reference count — number of references pointing to it.

When ref count == 0, the object is deleted.

Problem:

Reference counting cannot handle circular references:

class Node:
    def __init__(self, value):
        self.value = value
        self.next = None

a = Node(10)
b = Node(20)

a.next = b
b.next = a   # Circular reference

del a
del b
# Objects still exist in memory because reference count != 0


GC solves this issue by detecting unreachable objects even if their reference count is not zero.

🔹 3. How Python Garbage Collector Works

Python uses the gc module to manage garbage collection. It uses generational GC:

Generations:

Generation 0 (youngest)

Newly created objects are placed here.

Frequent collection occurs here.

Generation 1

Objects that survived Generation 0 collection move here.

Collected less frequently.

Generation 2 (oldest)

Long-lived objects reside here.

Collected least frequently.

Rationale: Most objects die young; generational GC reduces overhead.

🔹 4. Using the gc Module
a) Importing and enabling GC
import gc

gc.enable()   # Enable automatic garbage collection
gc.disable()  # Disable GC (not recommended)

b) Manually triggering GC
gc.collect()  # Forces collection of all generations

c) Checking objects
print(gc.get_count())  # Returns number of objects in each generation

🔹 5. Identifying Unreachable Objects

GC can detect objects that are not accessible from any program variables.

These objects are called garbage and are automatically deleted.

🔹 6. Circular References

GC handles cycles:

import gc

class A:
    def __init__(self):
        self.ref = None

x = A()
y = A()

x.ref = y
y.ref = x

del x
del y

gc.collect()  # Removes cyclic garbage


Without GC, memory would not be freed because reference count != 0.

🔹 7. Performance Considerations

GC is automatic but may introduce slight performance overhead.

Avoid creating unnecessary cyclic references in large-scale applications.

For high-performance scenarios, you can:

Temporarily disable GC using gc.disable().

Manually trigger GC when needed.

🔹 8. Memory Efficiency Tips

Avoid long-lived circular references.

Use weak references (weakref module) when objects can reference each other but don’t need to prevent collection.

Explicitly delete unused objects with del.

Monitor GC stats with gc.get_stats() for optimization.