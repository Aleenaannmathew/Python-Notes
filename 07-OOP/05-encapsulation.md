🟢 Encapsulation in Python — Detailed Explanation

Encapsulation is one of the core principles of Object-Oriented Programming (OOP). It refers to restricting access to the internal state (data) of an object and controlling how the data is modified or accessed.

It is mainly used to hide the internal details of an object and protect data from unauthorized access or modification.

Encapsulation is often referred to as data hiding.

🔹 1. Why Encapsulation is Important

Data Protection: Prevents accidental changes to the internal state.

Controlled Access: Only allows access through methods (getters/setters).

Maintainability: Internal implementation can be changed without affecting outside code.

Security: Sensitive data can be hidden from direct access.

🔹 2. Access Modifiers in Python

Python supports three types of access for attributes:

Modifier	Description	Example
Public	Accessible from anywhere	self.name
Protected	Accessible within class and subclasses (convention: single _)	_age
Private	Accessible only within the class (name mangling with double __)	__salary
2.1 Public Members
class Employee:
    def __init__(self, name, age):
        self.name = name      # public
        self.age = age        # public

emp = Employee("Alice", 25)
print(emp.name)  # Alice
print(emp.age)   # 25


Public attributes can be accessed and modified directly from outside the class.

2.2 Protected Members
class Employee:
    def __init__(self, name, age):
        self._name = name     # protected
        self._age = age       # protected

class Manager(Employee):
    def show_details(self):
        print(f"Name: {self._name}, Age: {self._age}")

m = Manager("Bob", 30)
m.show_details()   # Name: Bob, Age: 30


Conventionally protected, but still accessible outside class if needed.

_single_underscore signals “use with caution”.

2.3 Private Members
class Employee:
    def __init__(self, name, salary):
        self.__name = name       # private
        self.__salary = salary   # private

    def get_salary(self):
        return self.__salary

    def set_salary(self, value):
        if value >= 0:
            self.__salary = value
        else:
            print("Invalid salary")

emp = Employee("Charlie", 5000)
print(emp.get_salary())  # 5000
emp.set_salary(6000)
print(emp.get_salary())  # 6000


Private members are not accessible directly from outside the class.

Use getter and setter methods to access and modify them.

Python performs name mangling: __salary becomes _Employee__salary internally.

🔹 3. Encapsulation with Properties

Python provides the @property decorator to encapsulate attributes more elegantly:

class Employee:
    def __init__(self, name, salary):
        self.__name = name
        self.__salary = salary

    @property
    def salary(self):
        return self.__salary

    @salary.setter
    def salary(self, value):
        if value >= 0:
            self.__salary = value
        else:
            print("Invalid salary")

emp = Employee("David", 7000)
print(emp.salary)  # 7000
emp.salary = 8000
print(emp.salary)  # 8000
emp.salary = -500  # Invalid salary


@property makes getter and setter methods look like normal attributes.

Improves readability and maintains encapsulation.