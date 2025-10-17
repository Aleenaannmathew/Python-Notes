⚙️ Python Operators

Operators are symbols that perform operations on variables and values.
In Python, everything from arithmetic to logical comparison is handled using these operators.

🧮 1. Arithmetic Operators

Used to perform basic mathematical operations.

Operator	Description	Example	Output
+	Addition	10 + 5	15
-	Subtraction	10 - 5	5
*	Multiplication	10 * 5	50
/	Division (float)	10 / 4	2.5
//	Floor Division	10 // 4	2
%	Modulus (remainder)	10 % 4	2
**	Exponentiation	2 ** 3	8
a = 10
b = 3
print(a + b)   # 13
print(a / b)   # 3.333...
print(a // b)  # 3
print(a ** b)  # 1000

⚖️ 2. Comparison (Relational) Operators

Used to compare two values and return a Boolean (True or False).

Operator	Description	Example	Output
==	Equal to	10 == 5	False
!=	Not equal to	10 != 5	True
>	Greater than	10 > 5	True
<	Less than	10 < 5	False
>=	Greater than or equal to	10 >= 10	True
<=	Less than or equal to	10 <= 5	False
x = 7
y = 10
print(x < y)   # True
print(x == 7)  # True
print(x != y)  # True

🧠 3. Logical Operators

Used to combine multiple conditions.

Operator	Description	Example	Output
and	True if both conditions are True	(x > 5 and y < 15)	True
or	True if at least one condition is True	(x > 10 or y < 15)	True
not	Reverses the result	not(x > 5)	False
x = 8
print(x > 5 and x < 10)   # True
print(x > 10 or x == 8)   # True
print(not(x == 8))        # False

💾 4. Assignment Operators

Used to assign values to variables, often with operations combined.

Operator	Example	Equivalent To
=	x = 5	Assign value
+=	x += 3	x = x + 3
-=	x -= 3	x = x - 3
*=	x *= 3	x = x * 3
/=	x /= 3	x = x / 3
//=	x //= 3	x = x // 3
%=	x %= 3	x = x % 3
**=	x **= 3	x = x ** 3
x = 5
x += 2   # 7
x *= 3   # 21

🔢 5. Bitwise Operators

Used to perform operations at the bit level.
(Useful in performance-critical code or low-level programming.)

Operator	Name	Description	Example	Output
&	AND	Sets each bit to 1 if both bits are 1	5 & 3	1
`	`	OR	Sets each bit to 1 if one of two bits is 1	`5
^	XOR	Sets each bit to 1 if only one bit is 1	5 ^ 3	6
~	NOT	Inverts all the bits	~5	-6
<<	Left shift	Shifts bits left by n positions	5 << 1	10
>>	Right shift	Shifts bits right by n positions	5 >> 1	2

Explanation for 5 & 3:

5 = 0101
3 = 0011
------------
& = 0001  => 1

📦 6. Membership Operators

Used to test whether a value or variable exists in a sequence (like a list, tuple, or string).

Operator	Description	Example	Output
in	True if value is present	'a' in 'apple'	True
not in	True if value is not present	'z' not in 'apple'	True
fruits = ["apple", "banana", "cherry"]
print("apple" in fruits)      # True
print("mango" not in fruits)  # True

🪞 7. Identity Operators

Used to compare the memory locations of two objects.

Operator	Description	Example	Output
is	True if both refer to the same object	x is y	True
is not	True if they refer to different objects	x is not y	True
x = [1, 2, 3]
y = x
z = [1, 2, 3]

print(x is y)      # True  (same memory)
print(x is z)      # False (different memory)
print(x == z)      # True  (same values)

🧮 8. Operator Precedence

When multiple operators are used, Python follows a specific order of execution.

Precedence (High → Low)	Operators
1	() Parentheses
2	** Exponentiation
3	~, +, - (Unary)
4	*, /, //, %
5	+, -
6	<<, >>
7	&
8	^
9	`
10	Comparison (<, >, ==, etc.)
11	not
12	and
13	or

Example:

result = 10 + 2 * 3 ** 2
# Step 1: 3 ** 2 = 9
# Step 2: 2 * 9 = 18
# Step 3: 10 + 18 = 28
print(result)  # 28
