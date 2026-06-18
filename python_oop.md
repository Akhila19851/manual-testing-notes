# Python — OOP & Intermediate Concepts

## 1. Classes and Objects

A **class** is a blueprint. An **object** is an actual instance created from that blueprint.

```python
class Student:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def display(self):
        print(f"Name: {self.name}, Age: {self.age}")

# Creating an object
s1 = Student("Akhila", 25)
s1.display()   # Output: Name: Akhila, Age: 25
```

- `__init__` is the **constructor** — it runs automatically when an object is created.
- `self` refers to the current object being created.

---

## 2. The 4 Pillars of OOP

| Pillar | Meaning | Simple Example |
|---|---|---|
| **Encapsulation** | Wrapping data and methods together, hiding internal details | Using `self.name` inside a class |
| **Inheritance** | One class reusing another class's properties | `Dog` class inherits from `Animal` class |
| **Polymorphism** | Same method name, different behavior | `speak()` behaves differently for Dog vs Cat |
| **Abstraction** | Hiding complex implementation, showing only essentials | Using a method without knowing its internal code |

---

## 3. Inheritance

```python
class Animal:
    def __init__(self, name):
        self.name = name

    def speak(self):
        print(f"{self.name} makes a sound")

class Dog(Animal):              # Dog inherits from Animal
    def speak(self):              # method overriding
        print(f"{self.name} says Woof!")

class Cat(Animal):
    def speak(self):
        print(f"{self.name} says Meow!")

d = Dog("Rex")
c = Cat("Whiskers")
d.speak()   # Rex says Woof!
c.speak()   # Whiskers says Meow!
```

This is also an example of **Polymorphism** — the same method `speak()` behaves differently for each class.

---

## 4. Using `super()`

`super()` lets a child class call the parent class's constructor or methods.

```python
class Animal:
    def __init__(self, name):
        self.name = name

class Dog(Animal):
    def __init__(self, name, breed):
        super().__init__(name)     # calls Animal's constructor
        self.breed = breed

    def display(self):
        print(f"{self.name} is a {self.breed}")

d = Dog("Rex", "Labrador")
d.display()    # Rex is a Labrador
```

---

## 5. Encapsulation — Private & Protected Variables

```python
class BankAccount:
    def __init__(self, balance):
        self.__balance = balance     # double underscore = private

    def deposit(self, amount):
        self.__balance += amount

    def get_balance(self):
        return self.__balance

acc = BankAccount(1000)
acc.deposit(500)
print(acc.get_balance())   # 1500
# print(acc.__balance)      # This would cause an error - private!
```

- `_variable` (single underscore) → protected (convention, can still be accessed)
- `__variable` (double underscore) → private (cannot be accessed directly from outside)

---

## 6. Class Method vs Static Method

```python
class Counter:
    count = 0     # class variable, shared by all objects

    def __init__(self):
        Counter.count += 1

    @classmethod
    def get_count(cls):
        return cls.count

    @staticmethod
    def greet():
        print("Hello from Counter class!")

c1 = Counter()
c2 = Counter()
print(Counter.get_count())   # 2
Counter.greet()                # Hello from Counter class!
```

| Type | Uses `self`? | Uses `cls`? | Can access class variables? |
|---|---|---|---|
| Regular method | Yes | No | Yes (via self) |
| `@classmethod` | No | Yes | Yes (via cls) |
| `@staticmethod` | No | No | No |

---

## 7. File Handling

```python
# Writing to a file
with open("data.txt", "w") as f:
    f.write("Hello, this is a test file.")

# Reading from a file
with open("data.txt", "r") as f:
    content = f.read()
    print(content)

# Appending to a file
with open("data.txt", "a") as f:
    f.write("\nAdding a new line.")

# Reading line by line
with open("data.txt", "r") as f:
    for line in f:
        print(line.strip())
```

**Why use `with open()`?** It automatically closes the file after use — no need to manually call `f.close()`.

| Mode | Meaning |
|---|---|
| `"r"` | Read (default) |
| `"w"` | Write (overwrites existing content) |
| `"a"` | Append (adds to end of file) |
| `"r+"` | Read and write |

---

## 8. Modules and Imports

```python
# math_utils.py
def add(a, b):
    return a + b

def subtract(a, b):
    return a - b
```

```python
# main.py
import math_utils

print(math_utils.add(5, 3))        # 8
print(math_utils.subtract(5, 3))   # 2

# OR import specific functions
from math_utils import add
print(add(10, 20))   # 30
```

Useful built-in modules:
```python
import math
print(math.sqrt(16))     # 4.0
print(math.pow(2, 3))    # 8.0

import random
print(random.randint(1, 10))   # random number between 1-10

import datetime
print(datetime.datetime.now())   # current date and time
```

---

## 9. Lambda Functions (Short, One-line Functions)

```python
# Normal function
def square(x):
    return x * x

# Same thing as lambda
square = lambda x: x * x
print(square(5))   # 25

# Commonly used with map/filter
numbers = [1, 2, 3, 4, 5]
squared = list(map(lambda x: x * x, numbers))
print(squared)   # [1, 4, 9, 16, 25]

even_numbers = list(filter(lambda x: x % 2 == 0, numbers))
print(even_numbers)   # [2, 4]
```

---

## 10. List Comprehension (Shortcut for Loops)

```python
# Normal way
squares = []
for x in range(5):
    squares.append(x * x)

# List comprehension way (shorter)
squares = [x * x for x in range(5)]
print(squares)   # [0, 1, 4, 9, 16]

# With condition
even_squares = [x * x for x in range(10) if x % 2 == 0]
print(even_squares)   # [0, 4, 16, 36, 64]
```

---

## Quick Reference — OOP Keywords

| Keyword | Meaning |
|---|---|
| `class` | Defines a blueprint |
| `self` | Refers to the current object |
| `__init__` | Constructor, runs on object creation |
| `super()` | Calls the parent class |
| `@classmethod` | Method that works on the class, not instance |
| `@staticmethod` | Method with no access to self/cls |
| `__variable` | Private variable (encapsulation) |
