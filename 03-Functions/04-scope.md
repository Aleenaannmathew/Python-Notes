🟢 Variable Scope in Python — Deep Explanation
🧠 What is Scope?

Scope refers to the region of the program where a variable is recognized and can be accessed.

In Python:

Every variable is defined within a namespace,

and has a scope that determines its visibility and lifetime.

🔹 1. Types of Scopes — The LEGB Rule

Python follows the LEGB rule to resolve variable names:

Scope	Meaning	Example
L	Local — Inside the current function	Variables created inside a function
E	Enclosing — Inside any enclosing function (nested functions)	Outer function variables used by inner function
G	Global — Defined at the top level of a module/script	Variables defined outside all functions
B	Built-in — Python’s reserved names	Functions like len(), max(), etc.
✅ LEGB Resolution Example
x = "global"  # Global Scope

def outer():
    x = "enclosing"  # Enclosing Scope

    def inner():
        x = "local"  # Local Scope
        print(x)
    
    inner()

outer()


🔹 Output:

local

Explanation:

Python first looks for x in Local scope of inner().

If not found, it checks Enclosing, then Global, then Built-in.

It stops when it finds the first match.

🔹 2. Local Scope (Function Scope)

A variable declared inside a function is local to that function.

def greet():
    message = "Hello"  # Local variable
    print(message)

greet()
# print(message)  # ❌ NameError – message not accessible outside the function


📍 Lifetime: Created when function starts, destroyed when function ends.

🔹 3. Global Scope

A variable declared outside any function/class is in the global scope.

name = "Alice"  # Global variable

def show_name():
    print(name)  # Accessible inside function

show_name()     # Alice
print(name)     # Alice


✅ You can read global variables inside functions
❌ But you cannot modify them directly without global keyword.

🧩 Modifying Global Variables — global keyword
count = 0

def increment():
    global count
    count += 1   # modifies global variable

increment()
print(count)     # 1


🔹 Without global, Python would treat count as local and raise an UnboundLocalError.

🔹 4. Enclosing Scope (Nonlocal)

When you have nested functions, variables of the outer function form an enclosing scope for the inner one.

def outer():
    message = "Hi"

    def inner():
        print(message)  # Access enclosing variable

    inner()

outer()


✅ The inner function can read variables from its enclosing function.

🧩 Modifying Enclosing Variables — nonlocal keyword

You can modify a variable in an enclosing scope (not global) using nonlocal.

def outer():
    count = 0

    def inner():
        nonlocal count
        count += 1
        print(count)

    inner()
    inner()

outer()


Output:

1
2


🧠 Without nonlocal, Python would create a new local variable named count inside inner().

🔹 5. Built-in Scope

This is the outermost scope containing all of Python’s built-in names like:

len, range, print, sum, min, max, etc.

You can check them using:

import builtins
print(dir(builtins))

🧩 Overriding Built-ins (Shadowing)

Avoid naming your variables after built-ins!

list = [1, 2, 3]
print(len(list))  # Works fine

list = len        # Oops! You've shadowed 'len'
# print(len([1, 2, 3]))  ❌ TypeError: 'builtin_function_or_method' object is not subscriptable


✅ Best Practice: Never name your variables like built-in functions (list, str, sum, etc.)

🔹 6. Shadowing & Name Resolution

If a variable is redeclared in a smaller scope, it shadows variables of the same name in outer scopes.

x = "global"

def outer():
    x = "enclosing"
    def inner():
        x = "local"
        print(x)
    inner()

outer()


🔹 Output:

local


📍 Inner scope hides the variable from outer scopes.

🔹 7. Variable Lifetime
Scope	Created When	Destroyed When
Local	Function is called	Function exits
Enclosing	Outer function runs	Outer function exits
Global	Module loaded	Program ends
Built-in	Python interpreter starts	Interpreter ends
🔹 8. Example of All Scopes (LEGB Full Example)
x = "global"

def outer():
    x = "enclosing"

    def inner():
        x = "local"
        print("1️⃣ Local:", x)
    
    def inner2():
        print("2️⃣ Enclosing:", x)
    
    inner()
    inner2()

outer()
print("3️⃣ Global:", x)


Output:

1️⃣ Local: local
2️⃣ Enclosing: enclosing
3️⃣ Global: global

🔹 9. Closures and Scope

Closures capture variables from enclosing scopes, keeping them alive even after the outer function has returned.

def make_multiplier(n):
    def multiply(x):
        return x * n
    return multiply

times3 = make_multiplier(3)
print(times3(5))   # 15


Here, multiply() remembers n=3 even after make_multiplier() has finished.

✅ This works because of enclosing (nonlocal) scope preservation.

🔹 10. Global vs Nonlocal Summary
Keyword	Affects	Where used	Purpose
global	Global variable	Inside a function	Modify or assign global variable
nonlocal	Enclosing variable	Inside a nested function	Modify enclosing (outer) variable
✅ Example Comparing global and nonlocal
x = "global"

def outer():
    x = "enclosing"

    def inner():
        nonlocal x
        x = "changed by nonlocal"
        print("Inner:", x)

    inner()
    print("Outer:", x)

outer()
print("Global:", x)


Output:

Inner: changed by nonlocal
Outer: changed by nonlocal
Global: global


🧠 nonlocal changed only the enclosing variable, not the global one.

🔹 11. Advanced Concept: Scope and Mutable Objects

Even if a variable is local, if it refers to a mutable object, you can modify its content without declaring it global.

nums = [1, 2, 3]

def modify_list():
    nums.append(4)  # modifies global list (no reassignment)
    print(nums)

modify_list()
print(nums)


Output:

[1, 2, 3, 4]
[1, 2, 3, 4]


🧩 Important:
Only reassignments require global or nonlocal.
Mutations (like .append(), .remove(), etc.) do not.

🔹 12. Scope in List Comprehensions and Lambdas

Each comprehension creates its own local scope in Python 3+.

x = 10
nums = [x for x in range(3)]
print(nums)  # [0, 1, 2]
print(x)     # 10 (unaffected)


Earlier (Python 2), this would have overridden the outer variable.

🔹 13. Using globals() and locals() Functions
✅ Inspect Current Namespace
x = 5
def demo():
    y = 10
    print("Locals:", locals())   # Local variables inside function

demo()
print("Globals:", globals())     # Global variables in module
