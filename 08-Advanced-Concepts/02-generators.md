🟢 Generators in Python — Detailed Explanation

A generator is a special type of iterator in Python that yields items one at a time and does not store all values in memory. Generators are memory-efficient, especially when working with large datasets.

🔹 1. Why Use Generators?

Memory efficiency: Only one item is in memory at a time.

Lazy evaluation: Values are generated on-the-fly when needed.

Useful for large sequences: Files, streams, or infinite sequences.

🔹 2. Generator Functions

Defined using a normal function with the yield keyword instead of return.

Each call to yield pauses the function, and the state is saved.

def my_generator():
    yield 1
    yield 2
    yield 3

gen = my_generator()

print(next(gen))  # Output: 1
print(next(gen))  # Output: 2
print(next(gen))  # Output: 3
# next(gen) again raises StopIteration


Explanation:

yield produces a value and pauses the function.

next() resumes execution until the next yield.

Once exhausted, StopIteration is raised.

🔹 3. Generator Expressions

Similar to list comprehensions, but use parentheses () instead of brackets [].

squares = (x**2 for x in range(5))

print(next(squares))  # Output: 0
print(next(squares))  # Output: 1


Memory-efficient alternative to [x**2 for x in range(5)].

🔹 4. Advantages Over Lists
Feature	List	Generator
Memory	Stores all items	Generates on demand
Speed (initialization)	Slower for large lists	Faster, lazy evaluation
Iteration	Iterate multiple times	Can only iterate once (unless recreated)
🔹 5. Iterating Through Generators

You can use for loops:

def fibonacci(n):
    a, b = 0, 1
    for _ in range(n):
        yield a
        a, b = b, a + b

for num in fibonacci(5):
    print(num)


Output:

0
1
1
2
3

🔹 6. Infinite Generators

Generators can produce infinite sequences since they generate values lazily.

def infinite_numbers():
    num = 0
    while True:
        yield num
        num += 1

gen = infinite_numbers()
print(next(gen))  # 0
print(next(gen))  # 1


Caution: Infinite generators must be iterated with conditions or break statements.

🔹 7. Sending Values to Generators

Python generators can receive values using the send() method.

def accumulator():
    total = 0
    while True:
        value = yield total
        if value is None:
            break
        total += value

gen = accumulator()
print(next(gen))       # Initialize generator, Output: 0
print(gen.send(5))     # Output: 5
print(gen.send(10))    # Output: 15

🔹 8. Generator Methods

next(generator) – Returns next value.

generator.send(value) – Sends value into the generator.

generator.throw(exception) – Raises exception at the yield.

generator.close() – Stops the generator.

🔹 9. When to Use Generators

Large datasets (e.g., reading files line by line).

Infinite sequences.

Pipelines (processing one item at a time).

Memory-sensitive applications.

🔹 10. Summary

Generators are memory-efficient iterators.

Use yield in a function to create a generator.

Can be iterated once; use generator expressions for simple cases.

Advanced usage: sending values, throwing exceptions, infinite generators.

Perfect for lazy evaluation and streaming data.