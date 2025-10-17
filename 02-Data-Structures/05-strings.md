🟢 Strings in Python
🧠 What is a String?

A string is a sequence of characters enclosed in single quotes ' ', double quotes " ", or triple quotes ''' ''' / """ """.

Strings are immutable → you cannot change a character directly.

They are ordered → characters have indices.

Strings support various operations like slicing, concatenation, repetition, and formatting.

🔹 1. Creating Strings
str1 = "Hello"
str2 = 'World'
str3 = """This is a
multiline string"""
str4 = '''Another
multiline string'''

🔹 Empty String
empty = ""
empty2 = str()

🔹 2. Accessing Characters

Indexing → Access single character

s = "Python"
print(s[0])   # 'P'
print(s[-1])  # 'n' (last character)


Slicing → Extract substring

s = "Python"
print(s[0:4])   # 'Pyth' (start index inclusive, end index exclusive)
print(s[2:])    # 'thon' (from index 2 to end)
print(s[:4])    # 'Pyth' (start to index 3)
print(s[-4:-1]) # 'tho' (negative indices)
print(s[::2])   # 'Pto' (step of 2)

🔹 3. String Operations
Operation	Example	Result
Concatenation	"Hello" + " World"	'Hello World'
Repetition	"Hi! " * 3	'Hi! Hi! Hi! '
Membership	"H" in "Hello"	True
Iteration	for c in "Hi": print(c)	'H' 'i'
Length	len("Hello")	5
🔹 4. String Methods
Method	Description	Example
lower()	Convert to lowercase	"HELLO".lower() → 'hello'
upper()	Convert to uppercase	"hello".upper() → 'HELLO'
title()	Capitalize each word	"hello world".title() → 'Hello World'
capitalize()	Capitalize first char	"hello".capitalize() → 'Hello'
strip()	Remove whitespaces	" hi ".strip() → 'hi'
lstrip()	Remove left spaces	" hi".lstrip() → 'hi'
rstrip()	Remove right spaces	"hi ".rstrip() → 'hi'
split()	Split into list	"a,b,c".split(',') → ['a', 'b', 'c']
join()	Join list into string	'-'.join(['a','b','c']) → 'a-b-c'
replace()	Replace substring	"Hi there".replace("Hi","Hello") → 'Hello there'
find()	Find substring index	"Python".find('t') → 2
count()	Count substring occurrences	"banana".count('a') → 3
startswith()	Check prefix	"Python".startswith('Py') → True
endswith()	Check suffix	"Python".endswith('on') → True
isalpha()	Only letters?	"Hello".isalpha() → True
isdigit()	Only digits?	"123".isdigit() → True
isalnum()	Letters & numbers?	"abc123".isalnum() → True
format()	String formatting	"Hello, {}".format("Alice") → 'Hello, Alice'
🔹 5. String Formatting
a) Using f-strings (Python 3.6+)
name = "Alice"
age = 25
print(f"My name is {name} and I am {age} years old")

b) Using format() method
print("My name is {} and I am {} years old".format(name, age))
print("My name is {0} and I am {1}".format(name, age))

c) Using %-formatting (old style)
print("My name is %s and I am %d years old" % (name, age))

🔹 6. Escape Sequences
Sequence	Meaning
\\	Backslash
\'	Single quote
\"	Double quote
\n	Newline
\t	Tab
\r	Carriage return
\b	Backspace
print("Hello\nWorld")
print("Hello\tWorld")

🔹 7. String Immutability

Strings cannot be changed after creation.

s = "Hello"
# s[0] = 'h'  → Error
s = "h" + s[1:]  # Correct way to modify

🔹 8. Advanced Concepts
a) Multiline Strings
text = """This is
a multiline
string"""

b) Raw Strings (r"")

Used for regular expressions or paths:

path = r"C:\new_folder\test.txt"
print(path)  # C:\new_folder\test.txt

c) String Slicing Tricks

Reverse string: s[::-1]

Extract every second char: s[::2]

d) Unicode & Encoding
s = "Hello"
b = s.encode("utf-8")  # convert to bytes
s2 = b.decode("utf-8") # convert back to string

🔹 9. Practical Uses

User Input

name = input("Enter your name: ")


Data Cleaning

data = "  hello  "
clean_data = data.strip()


Parsing Text

text = "apple,banana,cherry"
fruits = text.split(",")


Templating & Logging

user = "Alice"
msg = f"Welcome {user}!"

🔹 10. Strings vs Lists
Feature	String	List
Mutable	No	Yes
Indexable	Yes	Yes
Iterable	Yes	Yes
Slicing	Yes	Yes
Concatenation	Yes	Yes
Methods	Many string-specific	List-specific