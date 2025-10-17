🟢 Iterators in Python — Detailed Explanation

An iterator is an object that allows traversal over a sequence of values without needing to know the underlying structure. Generators are a type of iterator, but not all iterators are generators.

🔹 1. Iterator vs Iterable
Feature	Iterable	Iterator
Definition	Object that can return an iterator	Object with __next__() method
Example	list, tuple, dict, set, string	generator, file object
Methods	__iter__()	__iter__(), __next__()
Can be looped?	Yes, using for	Yes, using for or next()
Exhaustible	No	Yes (once exhausted, raises StopIteration)

Iterable: Can be looped over multiple times.
Iterator: Produces elements one by one, maintains state, and is consumable.

🔹 2. Creating an Iterator

An object becomes an iterator if it implements two methods:

__iter__() – Returns the iterator object itself.

__next__() – Returns the next value; raises StopIteration when done.

my_list = [1, 2, 3]
it = iter(my_list)  # Using iter() function

print(next(it))  # 1
print(next(it))  # 2
print(next(it))  # 3
# next(it) again raises StopIteration


The built-in iter() function converts an iterable into an iterator.

🔹 3. Iterator Protocol

To make a custom object iterable, implement the iterator protocol:

class MyRange:
    def __init__(self, start, end):
        self.current = start
        self.end = end

    def __iter__(self):
        return self

    def __next__(self):
        if self.current >= self.end:
            raise StopIteration
        self.current += 1
        return self.current - 1

numbers = MyRange(1, 5)
for num in numbers:
    print(num)


Output:

1
2
3
4


Explanation:

__iter__() returns the iterator object itself.

__next__() keeps track of state and raises StopIteration when done.

🔹 4. Iterating Through Iterators

Using next()

fruits = ['apple', 'banana', 'cherry']
it = iter(fruits)
print(next(it))  # apple


Using for loop

for fruit in fruits:
    print(fruit)


Using while loop

it = iter(fruits)
while True:
    try:
        print(next(it))
    except StopIteration:
        break

🔹 5. Why Use Iterators?

Memory-efficient: Don’t store entire sequences in memory.

Lazy evaluation: Only generate elements when needed.

Custom traversal logic: Can define your own iteration patterns.

🔹 6. Common Iterator Examples

Built-in Iterators

numbers = [10, 20, 30]
it = iter(numbers)  # list iterator
print(next(it))     # 10


Generators (special iterators)

def gen_numbers(n):
    for i in range(n):
        yield i

it = gen_numbers(3)
print(next(it))  # 0


File objects (line-by-line iteration)

with open("file.txt") as f:
    for line in f:
        print(line.strip())

🔹 7. Infinite Iterators

Using itertools module:

import itertools

counter = itertools.count(1)  # Infinite iterator starting at 1
print(next(counter))  # 1
print(next(counter))  # 2


Infinite iterators are memory-efficient but must be carefully handled.

🔹 8. Summary

Iterators allow sequential access to elements without exposing the underlying data structure.

Implement __iter__() and __next__() to create a custom iterator.

Generators are a convenient way to create iterators.

Iterators support lazy evaluation, memory efficiency, and custom iteration logic.

Iterators can be finite or infinite.