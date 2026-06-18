# Python Core Basics — Notes

## 1. Variables

A variable is a name that stores a value in memory.

```python
name = "Akhila"        # string
age = 25                # integer
height = 5.6             # float
is_student = True        # boolean
```

Python automatically detects the data type — you don't need to declare it like in Java/C.

---

## 2. Data Types

| Type | Example | Description |
|---|---|---|
| `int` | `10` | Whole numbers |
| `float` | `10.5` | Decimal numbers |
| `str` | `"hello"` | Text |
| `bool` | `True`/`False` | Logical values |
| `list` | `[1, 2, 3]` | Ordered, changeable collection |
| `tuple` | `(1, 2, 3)` | Ordered, unchangeable collection |
| `dict` | `{"key": "value"}` | Key-value pairs |
| `set` | `{1, 2, 3}` | Unordered, unique values |

---

## 3. Operators

```python
# Arithmetic
a = 10 + 5    # addition
b = 10 - 5    # subtraction
c = 10 * 5    # multiplication
d = 10 / 5    # division (returns float)
e = 10 // 3   # floor division (returns int)
f = 10 % 3    # modulus (remainder)
g = 10 ** 2   # exponent (power)

# Comparison
10 == 5   # equal to → False
10 != 5   # not equal to → True
10 > 5    # greater than → True
10 < 5    # less than → False

# Logical
True and False   # False
True or False    # True
not True          # False
```

---

## 4. Conditional Statements (if-else)

```python
age = 20

if age >= 18:
    print("You are an adult")
elif age >= 13:
    print("You are a teenager")
else:
    print("You are a child")
```

---

## 5. Loops

### For Loop
```python
# Loop through a range
for i in range(5):
    print(i)   # prints 0,1,2,3,4

# Loop through a list
fruits = ["apple", "banana", "cherry"]
for fruit in fruits:
    print(fruit)
```

### While Loop
```python
count = 0
while count < 5:
    print(count)
    count += 1   # same as count = count + 1
```

### Loop Control
```python
for i in range(10):
    if i == 5:
        break       # stops the loop completely
    if i == 3:
        continue    # skips this iteration, moves to next
    print(i)
```

---

## 6. Functions

```python
def greet(name):
    return f"Hello, {name}!"

result = greet("Akhila")
print(result)   # Output: Hello, Akhila!
```

### Function with default parameter
```python
def greet(name="Guest"):
    return f"Hello, {name}!"

print(greet())          # Hello, Guest!
print(greet("Akhila"))  # Hello, Akhila!
```

### Function with multiple parameters
```python
def add(a, b):
    return a + b

print(add(10, 20))   # Output: 30
```

---

## 7. Lists — Most Used Data Structure

```python
fruits = ["apple", "banana", "cherry"]

fruits.append("mango")        # add to end
fruits.remove("banana")       # remove specific item
fruits[0]                     # access first item → "apple"
fruits[-1]                    # access last item → "cherry"
len(fruits)                   # get length
fruits.sort()                 # sort the list
```

---

## 8. Dictionaries — Key-Value Pairs

```python
student = {
    "name": "Akhila",
    "age": 25,
    "course": "Python"
}

print(student["name"])     # Output: Akhila
student["age"] = 26          # update value
student["grade"] = "A"       # add new key-value
del student["grade"]         # delete a key

for key, value in student.items():
    print(key, ":", value)
```

---

## 9. String Operations

```python
text = "Hello World"

text.lower()         # "hello world"
text.upper()         # "HELLO WORLD"
text.split()          # ["Hello", "World"]
text.replace("World", "Python")  # "Hello Python"
len(text)              # 11
text[0]                 # "H"
text[0:5]               # "Hello" (slicing)
```

---

## 10. Exception Handling (Error Handling)

```python
try:
    num = int(input("Enter a number: "))
    result = 10 / num
    print(result)
except ZeroDivisionError:
    print("Cannot divide by zero!")
except ValueError:
    print("Please enter a valid number!")
finally:
    print("Execution completed.")
```

---

## Quick Reference — Common Built-in Functions

| Function | What it does |
|---|---|
| `print()` | Display output |
| `len()` | Get length of list/string |
| `type()` | Get data type of a variable |
| `int()`, `str()`, `float()` | Convert between data types |
| `range()` | Generate a sequence of numbers |
| `input()` | Take input from user |
| `sorted()` | Return a sorted list |
| `max()`, `min()` | Get maximum/minimum value |
