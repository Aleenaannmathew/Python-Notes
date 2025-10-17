🟢 MRO (Method Resolution Order) in Python — Detailed Explanation

In Python, MRO (Method Resolution Order) determines the order in which methods and attributes are searched in a class hierarchy, especially when multiple inheritance is involved.

🔹 1. What is MRO?

Python uses C3 Linearization Algorithm to compute MRO.

It decides which method is called first when multiple classes have methods with the same name.

MRO is crucial in multiple inheritance to avoid ambiguity.

🔹 2. Checking MRO

You can check the MRO of a class using:

ClassName.__mro__    # Tuple of classes in MRO order
# or
ClassName.mro()      # List of classes in MRO order

🔹 3. Single Inheritance Example
class A:
    def show(self):
        print("A's show method")

class B(A):
    def show(self):
        print("B's show method")

b = B()
b.show()  # Output: B's show method

print(B.mro())
# Output: [<class '__main__.B'>, <class '__main__.A'>, <class 'object'>]


Observation:

Python first searches in B → then in A → finally in object.

🔹 4. Multiple Inheritance Example
class A:
    def show(self):
        print("A's show method")

class B(A):
    def show(self):
        print("B's show method")

class C(A):
    def show(self):
        print("C's show method")

class D(B, C):
    pass

d = D()
d.show()  # Output: B's show method

print(D.mro())
# Output: [<class '__main__.D'>, <class '__main__.B'>, <class '__main__.C'>, <class '__main__.A'>, <class 'object'>]


Observation:

Python follows C3 linearization: left-to-right, depth-first.

D → B → C → A → object.

🔹 5. MRO Rules (C3 Linearization)

Child class methods first: Always start search from the child class.

Left-to-right in inheritance list: If multiple parents, Python checks left parent first.

No duplicate search: Each class is considered only once.

Follow base class hierarchy consistently to avoid conflicts.

🔹 6. Example with Diamond Problem
class A:
    def show(self):
        print("A")

class B(A):
    def show(self):
        print("B")

class C(A):
    def show(self):
        print("C")

class D(B, C):
    pass

d = D()
d.show()  # Output: B

print(D.mro())
# Output: [D, B, C, A, object]


Observation:

Diamond problem: D inherits from both B and C which inherit from A.

MRO ensures A is called only once, preventing multiple calls.

🔹 7. MRO in Python 2 vs Python 3

Python 2: Old-style classes → Depth-first search (DFS)

Python 3: New-style classes → C3 Linearization, consistent and predictable.

🔹 8. Summary

MRO defines search order for attributes and methods.

Use ClassName.mro() or ClassName.__mro__ to inspect.

C3 Linearization ensures:

Left-to-right search for multiple parents

Single search for each class

Consistent and predictable method resolution

Critical in multiple inheritance to avoid ambiguity and diamond problem.