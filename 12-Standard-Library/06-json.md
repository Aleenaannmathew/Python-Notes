🟢 Python json Module — Detailed Explanation

The json module in Python provides functions to encode Python objects into JSON format and decode JSON data back into Python objects. JSON (JavaScript Object Notation) is a lightweight, text-based data interchange format widely used in APIs, configuration files, and web data exchange.

⚠️ Note: JSON only supports a subset of Python data types.

🔹 1. Importing the json Module
import json

🔹 2. Python Data Types vs JSON Data Types
Python Type	JSON Type
dict	object
list, tuple	array
str	string
int, float	number
True	true
False	false
None	null

⚠️ JSON does not support Python-specific types like set, bytes, or custom objects directly.

🔹 3. Encoding (Python → JSON)
a) json.dumps()

Converts a Python object to a JSON string.

data = {"name": "Alice", "age": 25, "is_student": True}
json_str = json.dumps(data)
print(json_str)  
# Output: {"name": "Alice", "age": 25, "is_student": true}


Optional Parameters:

indent: Pretty-print with indentation.

sort_keys: Sort keys alphabetically.

separators: Customize separators.

json_str = json.dumps(data, indent=4, sort_keys=True)
print(json_str)

b) json.dump()

Writes JSON data directly to a file.

data = {"name": "Bob", "age": 30}
with open("data.json", "w") as f:
    json.dump(data, f, indent=4)


json.dumps() returns a string, json.dump() writes to a file.

🔹 4. Decoding (JSON → Python)
a) json.loads()

Converts a JSON string to a Python object.

json_str = '{"name": "Alice", "age": 25, "is_student": true}'
data = json.loads(json_str)
print(data)
print(type(data))  # <class 'dict'>

b) json.load()

Reads JSON data from a file and converts it to a Python object.

with open("data.json", "r") as f:
    data = json.load(f)
print(data)


json.loads() works with strings, json.load() works with files.

🔹 5. Handling Complex Python Objects

JSON cannot serialize objects like sets, custom classes, or bytes by default. Use default parameter to handle them.

import json

class Student:
    def __init__(self, name, age):
        self.name = name
        self.age = age

s = Student("Alice", 20)

# Serialize using default function
json_str = json.dumps(s, default=lambda o: o.__dict__, indent=4)
print(json_str)

Decoding Custom JSON
def dict_to_student(d):
    return Student(d['name'], d['age'])

json_data = '{"name": "Alice", "age": 20}'
student_obj = json.loads(json_data, object_hook=dict_to_student)
print(student_obj.name, student_obj.age)

🔹 6. Common JSON Errors
Error	Cause
JSONDecodeError	Invalid JSON syntax during decoding
TypeError: Object of type X is not JSON serializable	Python object not supported by default JSON encoding
🔹 7. Useful Tips

Pretty Printing JSON:

json.dumps(data, indent=4)


Compact JSON (remove spaces):

json.dumps(data, separators=(',', ':'))


Ensure ASCII (for Unicode):

json.dumps(data, ensure_ascii=False)


Sort keys alphabetically:

json.dumps(data, sort_keys=True)

🔹 8. Summary of Important Functions
Function	Purpose
json.dumps()	Python object → JSON string
json.dump()	Python object → JSON file
json.loads()	JSON string → Python object
json.load()	JSON file → Python object

✅ Conclusion:
The json module is essential for data exchange and storage in Python. Mastering JSON serialization and deserialization allows you to work efficiently with APIs, configuration files, and web data.