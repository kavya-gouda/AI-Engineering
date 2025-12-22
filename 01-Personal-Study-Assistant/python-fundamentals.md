# Python Fundamentals - Complete Reference Guide

## 1. Basic Syntax & Variables

### Variables and Data Types
```python
# Variables (no declaration needed)
name = "Alice"
age = 25
height = 5.6
is_student = True

# Multiple assignment
x, y, z = 1, 2, 3
a = b = c = 0

# Type checking
print(type(name))  # <class 'str'>
print(type(age))   # <class 'int'>
```

### Basic Data Types
```python
# Numbers
integer = 42
floating = 3.14
complex_num = 3 + 4j

# Strings
single = 'Hello'
double = "World"
multiline = """This is
a multiline
string"""

# String operations
text = "Python"
print(text[0])        # P (indexing)
print(text[1:4])      # yth (slicing)
print(text.upper())   # PYTHON
print(len(text))      # 6
print(f"I love {text}")  # f-strings

# Boolean
is_valid = True
is_empty = False
```

## 2. Data Structures

### Lists (Mutable, Ordered)
```python
# Creation
fruits = ["apple", "banana", "cherry"]
numbers = [1, 2, 3, 4, 5]
mixed = [1, "hello", True, 3.14]

# Common operations
fruits.append("orange")      # Add to end
fruits.insert(1, "mango")    # Insert at index
fruits.remove("banana")      # Remove by value
popped = fruits.pop()        # Remove and return last
fruits.sort()                # Sort in place
fruits.reverse()             # Reverse in place

# List comprehension
squares = [x**2 for x in range(10)]
evens = [x for x in range(20) if x % 2 == 0]
```

### Tuples (Immutable, Ordered)
```python
# Creation
coordinates = (10, 20)
single_item = (42,)  # Note the comma

# Unpacking
x, y = coordinates
print(x, y)  # 10 20

# Tuples are immutable
# coordinates[0] = 15  # This would raise an error
```

### Dictionaries (Key-Value Pairs)
```python
# Creation
person = {
    "name": "John",
    "age": 30,
    "city": "New York"
}

# Access and modify
print(person["name"])
person["email"] = "john@example.com"
person.update({"age": 31, "phone": "123-456"})

# Methods
keys = person.keys()
values = person.values()
items = person.items()

# Get with default
email = person.get("email", "no-email@example.com")

# Dictionary comprehension
squared = {x: x**2 for x in range(5)}
```

### Sets (Unique, Unordered)
```python
# Creation
numbers = {1, 2, 3, 4, 5}
letters = set("hello")  # {'h', 'e', 'l', 'o'}

# Operations
numbers.add(6)
numbers.remove(3)
numbers.discard(10)  # Won't error if not present

# Set operations
set1 = {1, 2, 3}
set2 = {3, 4, 5}
print(set1 | set2)  # Union: {1, 2, 3, 4, 5}
print(set1 & set2)  # Intersection: {3}
print(set1 - set2)  # Difference: {1, 2}
```

## 3. Control Flow

### If-Elif-Else
```python
age = 18

if age < 13:
    print("Child")
elif age < 20:
    print("Teenager")
else:
    print("Adult")

# Ternary operator
status = "Adult" if age >= 18 else "Minor"

# Multiple conditions
if age >= 18 and age < 65:
    print("Working age")
```

### Loops

#### For Loop
```python
# Iterate over list
fruits = ["apple", "banana", "cherry"]
for fruit in fruits:
    print(fruit)

# Range
for i in range(5):        # 0 to 4
    print(i)

for i in range(2, 10, 2): # Start, stop, step
    print(i)              # 2, 4, 6, 8

# Enumerate (index + value)
for index, fruit in enumerate(fruits):
    print(f"{index}: {fruit}")

# Dictionary iteration
person = {"name": "Alice", "age": 25}
for key, value in person.items():
    print(f"{key}: {value}")
```

#### While Loop
```python
count = 0
while count < 5:
    print(count)
    count += 1

# Break and continue
for i in range(10):
    if i == 3:
        continue  # Skip this iteration
    if i == 7:
        break     # Exit loop
    print(i)
```

## 4. Functions

### Basic Functions
```python
# Simple function
def greet(name):
    return f"Hello, {name}!"

# Multiple parameters
def add(a, b):
    return a + b

# Default parameters
def power(base, exponent=2):
    return base ** exponent

print(power(5))      # 25
print(power(5, 3))   # 125

# Multiple return values
def get_stats(numbers):
    return min(numbers), max(numbers), sum(numbers)

minimum, maximum, total = get_stats([1, 2, 3, 4, 5])
```

### Advanced Function Features
```python
# *args (variable positional arguments)
def sum_all(*args):
    return sum(args)

print(sum_all(1, 2, 3, 4))  # 10

# **kwargs (variable keyword arguments)
def print_info(**kwargs):
    for key, value in kwargs.items():
        print(f"{key}: {value}")

print_info(name="Alice", age=25, city="NYC")

# Lambda functions
square = lambda x: x**2
print(square(5))  # 25

# Map, filter, reduce
numbers = [1, 2, 3, 4, 5]
squared = list(map(lambda x: x**2, numbers))
evens = list(filter(lambda x: x % 2 == 0, numbers))
```

## 5. File Handling

### Reading Files
```python
# Method 1: Manual close
file = open("data.txt", "r")
content = file.read()
file.close()

# Method 2: Context manager (recommended)
with open("data.txt", "r") as file:
    content = file.read()

# Read line by line
with open("data.txt", "r") as file:
    for line in file:
        print(line.strip())

# Read all lines into list
with open("data.txt", "r") as file:
    lines = file.readlines()
```

### Writing Files
```python
# Write (overwrites existing)
with open("output.txt", "w") as file:
    file.write("Hello, World!\n")
    file.write("Second line\n")

# Append
with open("output.txt", "a") as file:
    file.write("Appended line\n")

# Write multiple lines
lines = ["Line 1\n", "Line 2\n", "Line 3\n"]
with open("output.txt", "w") as file:
    file.writelines(lines)
```

### Working with JSON
```python
import json

# Write JSON
data = {
    "name": "Alice",
    "age": 25,
    "hobbies": ["reading", "coding"]
}

with open("data.json", "w") as file:
    json.dump(data, file, indent=2)

# Read JSON
with open("data.json", "r") as file:
    loaded_data = json.load(file)
    print(loaded_data["name"])

# String to JSON and back
json_string = json.dumps(data)
parsed_data = json.loads(json_string)
```

### Working with CSV
```python
import csv

# Write CSV
data = [
    ["Name", "Age", "City"],
    ["Alice", 25, "NYC"],
    ["Bob", 30, "LA"]
]

with open("data.csv", "w", newline="") as file:
    writer = csv.writer(file)
    writer.writerows(data)

# Read CSV
with open("data.csv", "r") as file:
    reader = csv.reader(file)
    for row in reader:
        print(row)

# Using DictReader/DictWriter
with open("data.csv", "r") as file:
    reader = csv.DictReader(file)
    for row in reader:
        print(row["Name"], row["Age"])
```

## 6. Error Handling

### Try-Except-Finally
```python
# Basic exception handling
try:
    result = 10 / 0
except ZeroDivisionError:
    print("Cannot divide by zero!")

# Multiple exceptions
try:
    value = int("abc")
except ValueError:
    print("Invalid integer")
except TypeError:
    print("Type error occurred")

# Catch all exceptions
try:
    risky_operation()
except Exception as e:
    print(f"Error occurred: {e}")

# Finally (always executes)
try:
    file = open("data.txt", "r")
    content = file.read()
except FileNotFoundError:
    print("File not found")
finally:
    if 'file' in locals():
        file.close()

# Raise exceptions
def validate_age(age):
    if age < 0:
        raise ValueError("Age cannot be negative")
    return age
```

## 7. Object-Oriented Programming

### Classes and Objects
```python
class Person:
    # Class variable
    species = "Homo sapiens"
    
    # Constructor
    def __init__(self, name, age):
        self.name = name  # Instance variable
        self.age = age
    
    # Instance method
    def greet(self):
        return f"Hello, I'm {self.name}"
    
    # String representation
    def __str__(self):
        return f"Person({self.name}, {self.age})"

# Create objects
person1 = Person("Alice", 25)
person2 = Person("Bob", 30)

print(person1.greet())
print(person1.species)
```

### Inheritance
```python
class Animal:
    def __init__(self, name):
        self.name = name
    
    def speak(self):
        pass

class Dog(Animal):
    def speak(self):
        return f"{self.name} says Woof!"

class Cat(Animal):
    def speak(self):
        return f"{self.name} says Meow!"

dog = Dog("Buddy")
cat = Cat("Whiskers")
print(dog.speak())
print(cat.speak())
```

## 8. Important Libraries & Imports

### Standard Library
```python
# Math operations
import math
print(math.sqrt(16))
print(math.pi)

# Random numbers
import random
print(random.randint(1, 10))
print(random.choice(["apple", "banana", "cherry"]))

# Date and time
from datetime import datetime, timedelta
now = datetime.now()
tomorrow = now + timedelta(days=1)
print(now.strftime("%Y-%m-%d %H:%M:%S"))

# OS operations
import os
print(os.getcwd())  # Current directory
os.makedirs("new_folder", exist_ok=True)

# Path operations
from pathlib import Path
path = Path("folder/file.txt")
print(path.exists())
print(path.parent)
```

### Package Management
```python
# Install packages (in terminal)
# pip install requests
# pip install python-dotenv

# Requirements file
# pip freeze > requirements.txt
# pip install -r requirements.txt

# Import installed packages
import requests
from dotenv import load_dotenv
```

## 9. List/Dict Comprehensions (Advanced)

```python
# List comprehensions
squares = [x**2 for x in range(10)]
evens = [x for x in range(20) if x % 2 == 0]
matrix = [[i*j for j in range(3)] for i in range(3)]

# Dictionary comp
