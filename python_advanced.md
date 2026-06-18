# Python — Advanced Concepts

## 1. *args and **kwargs

These let a function accept a variable number of arguments.

```python
# *args - for multiple positional arguments (collected as a tuple)
def add_numbers(*args):
    return sum(args)

print(add_numbers(1, 2, 3))        # 6
print(add_numbers(1, 2, 3, 4, 5))  # 15

# **kwargs - for multiple keyword arguments (collected as a dictionary)
def display_info(**kwargs):
    for key, value in kwargs.items():
        print(f"{key}: {value}")

display_info(name="Akhila", age=25, city="Bangalore")
# Output:
# name: Akhila
# age: 25
# city: Bangalore
```

**Why use them?** When you don't know in advance how many arguments will be passed.

---

## 2. Decorators

A decorator is a function that adds extra functionality to another function, without changing its actual code.

```python
def my_decorator(func):
    def wrapper():
        print("Something happening BEFORE the function runs")
        func()
        print("Something happening AFTER the function runs")
    return wrapper

@my_decorator
def say_hello():
    print("Hello!")

say_hello()
# Output:
# Something happening BEFORE the function runs
# Hello!
# Something happening AFTER the function runs
```

**Real-world use:** Logging, measuring execution time, checking permissions — all without touching the original function's code.

```python
import time

def timer(func):
    def wrapper(*args, **kwargs):
        start = time.time()
        result = func(*args, **kwargs)
        end = time.time()
        print(f"Time taken: {end - start} seconds")
        return result
    return wrapper

@timer
def slow_function():
    time.sleep(2)
    print("Function finished")

slow_function()
```

---

## 3. Generators (Memory-Efficient Loops)

A generator produces values **one at a time**, instead of creating the entire list in memory at once.

```python
# Normal function - creates full list in memory
def get_numbers(n):
    return [i for i in range(n)]

# Generator - creates values one at a time (more memory efficient)
def get_numbers_gen(n):
    for i in range(n):
        yield i

gen = get_numbers_gen(5)
for num in gen:
    print(num)   # 0, 1, 2, 3, 4
```

**Key difference:** `return` gives back everything at once. `yield` gives back one value at a time, pausing the function in between.

**Why it matters:** If you had a generator for 1 million numbers, it wouldn't load all 1 million into memory at once — much more efficient.

---

## 4. Iterators

An iterator is an object that can be looped over, one item at a time, using `__iter__()` and `__next__()`.

```python
class CountUpTo:
    def __init__(self, limit):
        self.limit = limit
        self.counter = 0

    def __iter__(self):
        return self

    def __next__(self):
        if self.counter < self.limit:
            self.counter += 1
            return self.counter
        else:
            raise StopIteration

nums = CountUpTo(5)
for num in nums:
    print(num)   # 1, 2, 3, 4, 5
```

Lists, strings, and dictionaries are all iterators behind the scenes — this is how `for` loops work internally.

---

## 5. Exception Handling — Custom Exceptions

```python
class InsufficientBalanceError(Exception):
    def __init__(self, message="Insufficient balance for this transaction"):
        self.message = message
        super().__init__(self.message)

class BankAccount:
    def __init__(self, balance):
        self.balance = balance

    def withdraw(self, amount):
        if amount > self.balance:
            raise InsufficientBalanceError()
        self.balance -= amount
        return self.balance

acc = BankAccount(1000)
try:
    acc.withdraw(5000)
except InsufficientBalanceError as e:
    print(e)   # Insufficient balance for this transaction
```

---

## 6. Multiple Inheritance & MRO (Method Resolution Order)

```python
class A:
    def show(self):
        print("A's show method")

class B:
    def show(self):
        print("B's show method")

class C(A, B):    # inherits from both A and B
    pass

obj = C()
obj.show()    # A's show method (A comes first, so A's method is used)

print(C.__mro__)   # Shows the order Python checks classes in
```

**MRO** = the order Python searches through parent classes to find a method. Goes left to right as listed in the class definition.

---

## 7. Magic / Dunder Methods

Special methods surrounded by double underscores that let your objects work with built-in Python operations.

```python
class Point:
    def __init__(self, x, y):
        self.x = x
        self.y = y

    def __str__(self):
        return f"Point({self.x}, {self.y})"

    def __add__(self, other):
        return Point(self.x + other.x, self.y + other.y)

p1 = Point(1, 2)
p2 = Point(3, 4)

print(p1)            # Point(1, 2)  -- uses __str__
p3 = p1 + p2          # uses __add__ (operator overloading)
print(p3)            # Point(4, 6)
```

| Dunder Method | Triggered By |
|---|---|
| `__init__` | Creating an object |
| `__str__` | `print(object)` |
| `__add__` | `object1 + object2` |
| `__len__` | `len(object)` |
| `__eq__` | `object1 == object2` |

---

## 8. Property Decorator (Getters & Setters)

```python
class Employee:
    def __init__(self, salary):
        self._salary = salary

    @property
    def salary(self):
        return self._salary

    @salary.setter
    def salary(self, value):
        if value < 0:
            raise ValueError("Salary cannot be negative")
        self._salary = value

emp = Employee(50000)
print(emp.salary)      # 50000 (calls the getter)
emp.salary = 60000      # calls the setter
print(emp.salary)      # 60000
```

This lets you control how a value is read/changed, while still using simple `object.attribute` syntax instead of calling methods like `get_salary()`.

---

## 9. Singleton Pattern (Only One Object Allowed)

```python
class Singleton:
    _instance = None

    def __new__(cls):
        if cls._instance is None:
            cls._instance = super().__new__(cls)
        return cls._instance

obj1 = Singleton()
obj2 = Singleton()
print(obj1 is obj2)   # True - both are the SAME object
```

**Real use case:** Database connections — you want only ONE connection shared across the entire application, not a new one every time.

---

## Quick Reference — When to Use What

| Concept | Use When |
|---|---|
| `*args`/`**kwargs` | Function needs flexible number of inputs |
| Decorators | Need to add behavior (logging, timing) without changing original code |
| Generators | Working with large datasets, need memory efficiency |
| Custom Exceptions | Need specific, meaningful error messages for your application |
| Property decorator | Need validation when setting a value |
| Singleton | Need only ONE instance of a class (e.g., DB connections) |
