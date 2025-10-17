🧭 Control Flow in Python

Control flow refers to the order in which statements are executed in a program.
Python executes code sequentially by default, but control flow statements allow you to:

Make decisions (via conditionals),

Repeat tasks (via loops),

And alter the normal sequence of execution (via control keywords).

🔹 1. Conditional Statements

Conditional statements let you execute specific code blocks only if certain conditions are true.

Syntax
if condition:
    # code block
elif another_condition:
    # code block
else:
    # code block

✅ Example
age = 20

if age < 18:
    print("You are a minor.")
elif age == 18:
    print("You just became an adult.")
else:
    print("You are an adult.")


Output:

You are an adult.

🧩 Nested if Statements

You can place one if statement inside another.

num = 10

if num > 0:
    if num % 2 == 0:
        print("Positive even number")
    else:
        print("Positive odd number")
else:
    print("Non-positive number")

🧠 Short-Hand if Statement

When you have a single statement inside an if, you can write it in one line:

x = 10
if x > 5: print("x is greater than 5")


Short-Hand if-else:

x = 20
print("Even") if x % 2 == 0 else print("Odd")

⚡ pass Statement

When you need a placeholder (no action), use pass:

if True:
    pass  # Placeholder for future code

🔹 2. Looping Statements

Loops allow repetitive execution of a block of code.

Python has two main types:

for loop → Iterates over a sequence

while loop → Repeats while a condition is true

🌀 For Loop

Used to iterate over sequences (list, tuple, string, etc.)

Syntax:

for variable in sequence:
    # code block


Example:

fruits = ["apple", "banana", "cherry"]
for fruit in fruits:
    print(fruit)


Output:

apple
banana
cherry

🔁 Using range()

range() generates a sequence of numbers.

for i in range(5):
    print(i)


Output:

0
1
2
3
4


Custom range:

for i in range(2, 10, 2):  # start, stop, step
    print(i)


Output:

2
4
6
8

🧩 Looping Through Strings
for ch in "Python":
    print(ch)

🔄 While Loop

Repeats as long as a condition is True.

Syntax:

while condition:
    # code block


Example:

count = 1
while count <= 5:
    print("Count:", count)
    count += 1


Output:

Count: 1
Count: 2
Count: 3
Count: 4
Count: 5

⚠️ Infinite Loop Example
while True:
    print("This will run forever!")  # Press Ctrl+C to stop


Always make sure the condition eventually becomes False.

🔹 3. Loop Control Statements

Control how loops behave during execution.

Keyword	Description
break	Terminates the loop completely
continue	Skips the rest of the code in the current iteration
pass	Does nothing (placeholder)
🧱 Break Example
for i in range(10):
    if i == 5:
        break
    print(i)


Output:

0
1
2
3
4

🔂 Continue Example
for i in range(5):
    if i == 2:
        continue
    print(i)


Output:

0
1
3
4

⚙️ Pass Example
for i in range(5):
    if i == 3:
        pass  # Placeholder for future logic
    print(i)

🔹 4. Loop with else Block

You can use an else with loops.
The else block executes only if the loop completes normally (no break).

Example 1:

for i in range(5):
    print(i)
else:
    print("Loop finished successfully!")


Output:

0
1
2
3
4
Loop finished successfully!


Example 2 (with break):

for i in range(5):
    if i == 3:
        break
    print(i)
else:
    print("Loop finished successfully!")  # Will NOT execute


Output:

0
1
2

🔹 5. Nested Loops

Loops inside other loops.

Example:

for i in range(3):
    for j in range(2):
        print(f"i={i}, j={j}")


Output:

i=0, j=0
i=0, j=1
i=1, j=0
i=1, j=1
i=2, j=0
i=2, j=1