🟢 Python re Module — Detailed Explanation

The re module in Python provides support for regular expressions, which allow you to search, match, and manipulate strings using patterns. Regular expressions are powerful tools for text processing, validation, and parsing.

⚠️ Note: Regular expressions can be complex, so always test your patterns carefully.

🔹 1. Importing the re Module
import re

🔹 2. Basic Functions in re
a) re.match()

Checks for a match only at the beginning of a string.

text = "Hello World"
result = re.match(r'Hello', text)
if result:
    print("Match found:", result.group())  # Match found: Hello


Returns a Match object if found, otherwise None.

b) re.search()

Searches for a pattern anywhere in the string.

text = "Hello World"
result = re.search(r'World', text)
if result:
    print("Found:", result.group())  # Found: World

c) re.findall()

Returns a list of all non-overlapping matches.

text = "My numbers are 12, 45, and 78"
numbers = re.findall(r'\d+', text)
print(numbers)  # ['12', '45', '78']

d) re.finditer()

Returns an iterator yielding Match objects.

text = "My numbers are 12, 45, and 78"
for match in re.finditer(r'\d+', text):
    print(match.group(), match.start(), match.end())
# Output:
# 12 14 16
# 45 18 20
# 78 26 28

e) re.sub()

Substitute/replace patterns in a string.

text = "I love cats"
new_text = re.sub(r'cats', 'dogs', text)
print(new_text)  # I love dogs

f) re.split()

Split a string by a pattern.

text = "apple,banana;cherry orange"
fruits = re.split(r'[;, ]', text)
print(fruits)  # ['apple', 'banana', 'cherry', 'orange']

🔹 3. Match Object Methods

If a match is found, a Match object is returned with methods:

Method	Description
group()	Returns the matched string
start()	Returns starting index of match
end()	Returns ending index of match
span()	Returns tuple (start, end)
m = re.search(r'World', "Hello World")
print(m.group(), m.start(), m.end(), m.span())  # World 6 11 (6, 11)

🔹 4. Regular Expression Syntax
a) Meta Characters
Character	Meaning
.	Any character except newline
^	Start of string
$	End of string
*	0 or more repetitions
+	1 or more repetitions
?	0 or 1 repetition
\d	Digit [0-9]
\D	Non-digit
\s	Whitespace
\S	Non-whitespace
\w	Word character [a-zA-Z0-9_]
\W	Non-word character
[abc]	Any character a, b, or c
[^abc]	Any character except a, b, or c
b) Quantifiers
Symbol	Meaning
{n}	Exactly n repetitions
{n,}	n or more repetitions
{n,m}	Between n and m repetitions
c) Groups and Capturing
text = "John: 25, Alice: 30"
pattern = r'(\w+): (\d+)'
matches = re.findall(pattern, text)
print(matches)  # [('John', '25'), ('Alice', '30')]

d) Special Sequences

\b → Word boundary

\B → Non-word boundary

\A → Start of string

\Z → End of string

e) Flags

Flags modify the behavior of regex functions.

Flag	Description
re.IGNORECASE / re.I	Case-insensitive match
re.MULTILINE / re.M	^ and $ match start/end of each line
re.DOTALL / re.S	. matches newline as well
text = "Hello\nworld"
print(re.findall(r'^world', text, re.MULTILINE))  # ['world']

🔹 5. Compiling Regular Expressions

You can compile a regex for repeated use, which improves performance:

pattern = re.compile(r'\d+')
matches = pattern.findall("I have 2 apples and 3 oranges")
print(matches)  # ['2', '3']

🔹 6. Summary of Most Used Functions
Function	Purpose
match()	Match at beginning of string
search()	Search anywhere in string
findall()	List all matches
finditer()	Iterator for matches
sub()	Replace pattern
split()	Split string by pattern
compile()	Compile regex for reuse

✅ Conclusion:
The re module is extremely powerful for text searching, validation, extraction, and manipulation. Learning regex syntax is essential for data parsing, input validation, and advanced string handling in Python.