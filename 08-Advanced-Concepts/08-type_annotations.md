🟢 Type Annotations in Python — Detailed Explanation
🔹 1. What are Type Annotations?

Type annotations allow you to explicitly declare the expected data types of variables, function parameters, and return values.

They do not enforce types at runtime (Python is dynamically typed) but help with readability, documentation, and static type checking using tools like mypy, pyright, or IDE hints.

🔹 2. Basic Syntax for Variables
name: str = "Alice"
age: int = 25
height: float = 5.6
is_student: bool = True


Here, name, age, height, and is_student are annotated with their expected types.

Python does not restrict you from assigning a different type (e.g., age = "25"), but static type checkers will warn you.

🔹 3. Type Annotations in Functions
a) Parameters
def greet(name: str, age: int):
    print(f"Hello {name}, you are {age} years old.")

greet("Alice", 25)

b) Return Type
def add(a: int, b: int) -> int:
    return a + b

result = add(10, 20)


-> int specifies the return type.

Helps IDEs and tools catch errors early.

🔹 4. Optional and Default Types
from typing import Optional

def greet(name: str, age: Optional[int] = None) -> str:
    if age:
        return f"Hello {name}, you are {age}"
    return f"Hello {name}"


Optional[int] means the parameter can be int or None.

🔹 5. Complex Types Using typing Module

Python provides the typing module for advanced type hints.

a) Lists, Tuples, Sets, Dicts
from typing import List, Tuple, Set, Dict

names: List[str] = ["Alice", "Bob"]
coords: Tuple[int, int] = (10, 20)
unique_ids: Set[int] = {1, 2, 3}
user_ages: Dict[str, int] = {"Alice": 25, "Bob": 30}

b) Union

To specify multiple possible types:

from typing import Union

def process(value: Union[int, str]):
    print(value)

process(10)
process("Hello")

c) Any

When any type is allowed:

from typing import Any

data: Any = 42
data = "Hello"

d) Callable

To annotate functions that take other functions:

from typing import Callable

def operate(a: int, b: int, func: Callable[[int, int], int]) -> int:
    return func(a, b)

def add(x, y):
    return x + y

print(operate(5, 3, add))  # 8

🔹 6. Type Aliases

You can create reusable type names.

from typing import List, Dict

UserType = Dict[str, List[int]]

users: UserType = {
    "Alice": [1, 2, 3],
    "Bob": [4, 5]
}

🔹 7. Benefits of Type Annotations

Readability — Makes code easier to understand.

Error detection — Detect type mismatches before runtime using mypy.

IDE support — Autocomplete, documentation, and type hints.

Documentation — Self-explanatory function signatures.

🔹 8. Static Type Checking Example
$ mypy example.py
example.py:10: error: Argument 1 to "add" has incompatible type "str"; expected "int"


mypy will catch type errors without running the code.