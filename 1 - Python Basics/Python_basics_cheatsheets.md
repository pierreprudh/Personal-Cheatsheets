# **1. Python Fundamentals**
## 1.1 Variables & Data Types  

Python is dynamically typed, meaning you don’t need to declare variable types explicitly.  
A variable is created when you assign a value to a name.

### Common Data Types
| Type        | Example                   | Description |
|-------------|----------------------------|-------------|
| `int`       | `x = 10`                   | Integer numbers |
| `float`     | `pi = 3.14`                | Decimal numbers |
| `str`       | `name = "John"`            | Text (immutable) |
| `bool`      | `flag = True`              | Boolean values |
| `list`      | `nums = [1, 2, 3]`         | Ordered, mutable |
| `tuple`     | `coords = (1, 2)`          | Ordered, immutable |
| `dict`      | `person = {"name": "A"}`   | Key-value pairs |
| `set`       | `s = {1, 2, 3}`            | Unique elements |

### Variables Assignement

```python
x=10 
y=3.14
name="John"
is_true=True
```

you can also do that
```python
a, b, c = 1, 2, 3
```

### Checking Types

```python
type(42)   #<class 'int'>
```

> See **examples.ipynb**

You can also use the **isinstance** function to check type 

```python
isinstance(10, int)           # True
isinstance("abc", (int, str)) # True, because it matches one of them
```


### String Manipulation

Strings are immutable sequences of characters.

```python
name = "John"
greeting = f"Hello, {name}!"   # f-string
length = len(name)
```

Operations 
```python
"hello".upper()   # "HELLO"
"Hello".lower()   # "hello"
"data".capitalize()   # "Data"
```

## 1.2 Basic Operations  

Python supports all standard arithmetic operators.
These operations work on integers, floats, and even some built-in container types.


### Arithmetic Operators

| Operator | Example | Meaning |
|----------|---------|---------|
| `+` | `3 + 2` | Addition |
| `-` | `5 - 1` | Subtraction |
| `*` | `4 * 2` | Multiplication |
| `/` | `10 / 3` | Division (returns float) |
| `//` | `10 // 3` | Floor division |
| `%` | `10 % 3` | Modulo (remainder) |
| `**` | `2 ** 3` | Exponentiation |


### Assignement Operators 

| Operator | Example |
|----------|---------|
| `x+=1`| `x = x + 1`|
| `x-=1`| `x = x - 1`|
| `x*=2`| `x = x * 2`|
| `x/=2`| `x = x / 2`|

### Comparison Operators 

| Operator | Example  | Meaning          |
| -------- | -------- | ---------------- |
| `==`     | `a == b` | Equal            |
| `!=`     | `a != b` | Not equal        |
| `>`      | `a > b`  | Greater than     |
| `<`      | `a < b`  | Less than        |
| `>=`     | `a >= b` | Greater or equal |
| `<=`     | `a <= b` | Less or equal    |

### Logical Operators

| Operator | Meaning                   |
| -------- | ------------------------- |
| `and`    | Both must be True         |
| `or`     | At least one must be True |
| `not`    | Negates a boolean         |


### Identity and equality

- `==` checks value equity 
- `is` checks object memory location


```python 
a = [1, 2, 3]
b = [1, 2, 3]

a == b   # True (same content)
a is b   # False (different objects)
```


## 1.3 Type Casting  

Type casting (or *type conversion*) means converting a value from one data type to another.  
Python provides several built-in functions to convert between common types.


### Basic Type Conversion Functions

| Function | Converts To | Example |
|----------|-------------|---------|
| `int()` | Integer | `int("42")` → `42` |
| `float()` | Float | `float("3.14")` → `3.14` |
| `str()` | String | `str(100)` → `"100"` |
| `bool()` | Boolean | `bool(0)` → `False` |
| `list()` | List | `list((1,2))` → `[1,2]` |
| `tuple()` | Tuple | `tuple([1,2])` → `(1,2)` |
| `set()` | Set | `set([1,2,2])` → `{1,2}` |


### Examples

#### **String → Integer / Float**

```python
age_str = "25"
age = int(age_str)

price_str = "19.99"
price = float(price_str)
```

#### **Integer / Float → String**

```python 
x = 10
text = "Value: " + str(x)
```

#### **Numeric -> Boolean** 

- `0`, `0.0`, and empty containers -> `False`
- Everything else -> `True`

```python 
bool(0)      # False
bool(5)      # True
bool([])     # False
bool([1])    # True
```

#### Between Containers
```python 
# List → Tuple
tuple([1, 2, 3])     # (1, 2, 3)

# Tuple → List
list((4, 5, 6))      # [4, 5, 6]

# List → Set (duplicates removed)
set([1, 1, 2, 3])    # {1, 2, 3}
```

---

# **2. Data Structures**
Python provides several built-in data structures that are heavily used in Data Science and Machine Learning.

---


## 2.1 Lists  
Lists are **ordered, mutable collections** that can store elements of any type.

### Creating Lists
```python
numbers = [1, 2, 3, 4]
mixed = [1, "data", 3.14, True]
empty_list = []
```

### Accessing List Elements
```python
numbers[0]      # First element
numbers[-1]     # Last element
numbers[1:3]    # Slicing (from index 1 to 2)
```

### Modifying List Elements
```python
numbers[0] = 10        # Modify element
numbers.append(5)      # Add one element at the end 
numbers.extend([6, 7]) # Add multiple elements
numbers.insert(1, 99)  # Insert at position 99
```

### Removing List Elements
```python
numbers.remove(99)   # Remove by value
numbers.pop()        # Remove last element
numbers.pop(0)       # Remove by index
del numbers[1]       # Delete by index
```

### List Length
```python
len(numbers)
```

### Sorting List 
```python
nums = [3, 1, 4, 2]

sorted_nums = sorted(nums)   # Returns new list
nums.sort()                  # Sorts in place

nums.sort(reverse=True)
```

### List creation with operations
```python
squares = [x**2 for x in range(10)]

evens = [x for x in range(20) if x % 2 == 0]
```

### Useful operators
```python
sum(nums)
min(nums)
max(nums)

in
```



## 2.2 Tuples  

Tuples are **ordered, immutable collections**.  
They are commonly used for **fixed data**, **coordinates**, or **function returns**.

### Creating Tuples

```python
t = (1, 2, 3)
single = (5,)        # comma required
empty = ()

t = 1, 2, 3
```

### Accessing elements in Tuples
```python
t[0]      # First element
t[-1]     # Last element
t[1:3]    # Slicing

t[0] = 10   # TypeError 

x, y, z = (1, 2, 3)  # Unpacking
```
> Tuples can't be modified and are used for image dimension for example




## 2.3 Dictionaries  

Dictionaries store data as **key–value pairs**.  
They are **unordered (insertion-ordered since Python 3.7)** and optimized for fast lookups.

### Creating Dictionaries

```python
person = {
    "name": "Pierre",
    "age": 25,
    "is_student": False
}

empty_dict = {}
```

### Accessing values in Dictionaries

```python
person["name"]        # 'Pierre'
person.get("age")     # 25

person.get("salary", 0) #No error if missing
```

### Modifying values in Dictionaries

```python
person["age"] = 26          # Update value
person["city"] = "Paris"    # Add new key

del person["is_student"]
age = person.pop("age")
```

### Dictionary Methods
```python
person.keys()
person.values()
person.items()
```

### Nested Dictionnaries
```python
user = {
    "id": 1,
    "profile": {
        "name": "Alice",
        "email": "alice@email.com"
    }
}

user["profile"]["email"]
```

## 2.4 Sets  

Sets are **unordered collections of unique elements**.  
They are useful for **removing duplicates**, **membership tests**, and **set operations**.


### Creating Sets

```python
s = {1, 2, 3}
empty_set = set()  # NOT {}
``` 
From a list (duplicates removed):

```python
values = [1, 2, 2, 3, 3, 3]
unique_values = set(values)
```

### Modifying Sets

```python
s.add(4)

s.remove(2)     # Error if missing
s.discard(10)   # Safe removal
```

### Sets Operation

```python
a = {1, 2, 3}
b = {3, 4, 5}

a | b           #{1, 2, 3, 4, 5}
# Intersection :
a & b

# Difference :
a - b

# Symmetric difference :
a ^ b
```

---

# **3. Control Flow**

Control flow statements define how code is executed based on conditions and loops.
They are fundamental for decision-making and iteration in Python programs.



## 3.1 Conditional Statements (`if / elif / else`)  
Used to execute code based on boolean conditions.

### Basic syntax

```python
x = 10

if x > 0:
    print("Positive")
elif x == 0:
    print("Zero")
else:
    print("Negative")
```

### Multiple Conditions
```python
age = 25
income = 45000

if age > 18 and income > 30000:
    eligible = True
```

## 3.2 Loops (`for`, `while`)  

### `for` Loop

Used to iterate over sequences 

```python
for i in range(5):
    print(i)
```

Iterating over a list :
```python
values = [10, 20, 30]

for v in values:
    print(v)
```

### `while` Loop

Used when the number of iterations is unknown
```python
count = 0

while count < 3:
    print(count)
    count += 1
```

### Loop Control Keywords

```python
for i in range(10):
    if i == 5:
        break      # stop loop
    if i % 2 == 0:
        continue   # skip iteration
```

## 3.3 Loop utilities (`enumerate`, `zip`, `range`)  


### ``enumerate``

```python
names = ["Alice", "Bob", "Charlie"]

for idx, name in enumerate(names):
    print(idx, name)
```

### ``zip``

Iterate over multiple sequences in parallel.

```python
x = [1, 2, 3]
y = [4, 5, 6]

for a, b in zip(x, y):
    print(a, b)
```


### ``range``
```python
range(5)        # 0 → 4
range(1, 5)     # 1 → 4
range(0, 10, 2) # step = 2, 5 steps
```

---

# **4. Functions**

Functions allow you to **reuse code**, **structure logic**, and **make programs readable**.

## 4.1 Function definition & return values  

### Basic Function

```python
def add(a, b):
    return a + b

result = add(3, 5)
```  

**Default argument**
```python 
def power(x, exp=2): return x ** exp

power(3)      # 9
power(3, 3)   # 27
```

### Returning Multiple Values
```python
def stats(values):
    return min(values), max(values), sum(values) / len(values)

low, high, mean = stats([1, 2, 3, 4])
```  

## 4.2 `*args` and `**kwargs`  

Used to handle variable numbers of arguments.

### `args` (positional arguments)

```python
def add_all(*args):
    return sum(args)

add_all(1, 2, 3, 4)  # 10
```  

### `kwargs` (keyword arguments)

```python
def print_info(**kwargs):
    for key, value in kwargs.items():
        print(key, value)

print_info(name="Alice", age=30)
``` 

## 4.3 Lambda functions  

One-line function with no declaration

```python
square = lambda x: x ** 2
square(5)
``` 

Can be used in **list**

```python
list(map(lambda x: x * 2, [1, 2, 3]))
```

## 4.4 Built-ins: `map`, `filter`, `reduce`  

### ``map``
```python
nums = [1, 2, 3]
mapped = list(map(lambda x: x + 1, nums))
```


### ``filter``
```python
filtered = list(filter(lambda x: x % 2 == 0, nums))
```

### ``reduce``
```python
total = reduce(lambda x, y: x + y, nums)
```


#### Pratical example -> Feature Transformation

> Normalize values in one column

```python
values = [10, 20, 30]

normalized = list(map(lambda x: x / max(values), values))
```

---

# **5. Error Handling**

Error handling allows your program to **fail** while avoid crashes, and handle unexpected cases.
This is especially important when working with **real-world data**.

## 5.1 Try / Except  

### Basic structure:

```python
try:
    x = int("10")
except ValueError:
    print("Conversion failed")
```
>If no error, ``except`` is skipped.

### Catching Multiple Exceptions

```python
try:
    value = 10 / x
except (ZeroDivisionError, TypeError):
    print("Invalid operation")
```

### Else & Finally
#### ``else`` (runs if no exception)
```python
try:
    x = int("5")
except ValueError:
    print("Error")
else:
    print("Success")
```

#### ``finally`` (always runs)
```python
try:
    f = open("file.txt")
except FileNotFoundError:
    print("File missing")
finally:
    f.close()
```

## 5.2 Common exceptions  

| Exception           | When it occurs     |
| ------------------- | ------------------ |
| `ValueError`        | Invalid value      |
| `TypeError`         | Wrong type         |
| `KeyError`          | Missing dict key   |
| `IndexError`        | Index out of range |
| `ZeroDivisionError` | Division by zero   |
| `FileNotFoundError` | Missing file       |

## 5.3 Raising errors  

Use ``raise`` to trigger your own exceptions and avoid crashes.

```python
def withdraw(balance, amount):
    if amount > balance:
        raise ValueError("Insufficient balance")
    return balance - amount
```

## 5.4 Creating Custom Exceptions

```python
class DataValidationError(Exception):
    pass

def validate_age(age):
    if age < 0:
        raise DataValidationError("Age must be positive")
```

---

# **6. Modules & Imports**


A module is a Python file (`.py`), and a package is a collection of modules.

## 6.1 Importing modules  

### Import the whole module

```python
import math

math.sqrt(16)
math.pi
```

### Import specific objects

```python
from math import sqrt, pi

sqrt(16)
```

### Import with alias 

```python
import numpy as np

np.array([1, 2, 3])
```

## 6.2 Creating your own module  

**Create** a file ``utils.py`` :

```python
# utils.py
def mean(values):
    return sum(values) / len(values)
```

Use it in another file:

```python
# main.py
from utils import mean

mean([1, 2, 3])
```

---

# **7. Classes & Object-Oriented Basics**

Classes let you **bundle data and behavior** into a single reusable blueprint.  
You use them to define your own types, which is very common in ML models, pipelines, and APIs.

## 7.1 Class definition

A class defines a new type, and `__init__` is the constructor called when you create an instance.

```python
class Model:
    def __init__(self, name):
        self.name = name  # attribute stored on the instance

# create an object (instance)
model = Model("MyModel")
print(model.name)  # -> MyModel
```


## 7.2 Attributes & methods
**Attributes** : variables that belong to an object (``self.name``).

**Methods** : functions defined inside a class that operate on that object (``train``).

```python
class Model:
    def __init__(self, name):
        self.name = name          # attribute

    def train(self, X):           # method
        print(f"Training {self.name} on {len(X)} samples")

model = Model("MyModel")
model.train()[1]
```

## 7.3 Inheritance  

Inheritance lets a class reuse and extend the behavior of another class.

```python
class Model:
    def __init__(self, name):
        self.name = name

    def train(self, X):
        print(f"Training {self.name} on {len(X)} samples")


# LinearModel "is a" Model and inherits its attributes and methods
class LinearModel(Model):
    pass


lm = LinearModel("LinearReg")
lm.train()  # uses Model.train[1]
```

You can also override methods in the child class :
```python
class LinearModel(Model):
    def train(self, X):
        print(f"Fitting linear weights for {self.name} on {len(X)} samples")
```

## 7.4 Magic methods (`__str__`, `__len__`, etc.)  

```python
class Dataset:
    def __init__(self, data):
        self.data = data

    def __len__(self):
        return len(self.data)

    def __str__(self):
        return f"Dataset(size={len(self)})"
```

#### Example 
```python
model = Model("Linear Regression")
model.train(X=None)
```

---

# **8. File Handling**

Python provides simple and safe tools to work with files.

## 8.1 Reading files  

### Reading a text file

```python
with open("data.txt", "r") as f:
    content = f.read()
``` 

> Read line by line 

```python
with open("data.txt") as f:
    for line in f:
        print(line.strip())
``` 

## 8.2 Writing files  

### ``Write`` (overwrite) :

```python
with open("output.txt", "w") as f:
    f.write("Hello world")
``` 

### ``Append`` :

```python
with open("output.txt", "a") as f:
    f.write("\nNew line")
``` 

## 8.3 Working with JSON  

You can use the ``json`` library 

### Reading JSON

```python
import json

with open("data.json") as f:
    data = json.load(f)
``` 

### Writing JSON

```python
with open("data.json", "w") as f:
    json.dump(data, f, indent=2)
``` 

## 8.4 Using ``pathlib`` library

Using ``pathlib`` library can prevent from errors when you move documents if they are hard-coded and not in cloud storage. 

```python
from pathlib import Path

path = Path("data") / "file.txt"

if path.exists():
    text = path.read_text()
``` 

Write : 

```python

path.write_text("content")
``` 

---

# **9. Useful Python Features**

This section covers Python features that greatly improve **code readability, efficiency, and safety**.

## 9.1 List / Dict / Set comprehensions  

### List Comprehension

```python
squares = [x**2 for x in range(5)]
```

With condition:

```python
positives = [x for x in values if x > 0]
```

### Dictionary Comprehension

```python
counts = {x: values.count(x) for x in set(values)}
```

### Set Comprehension

```python
unique_lengths = {len(x) for x in words}
```


## 9.2 Decorators (intro)  

Decorators modify function behavior (see ``example.ipynb``)

```python
def log_call(func):
    def wrapper(*args, **kwargs):
        print("Function called")
        return func(*args, **kwargs)
    return wrapper

@log_call
def add(a, b):
    return a + b
```

## 9.3 Context managers (`with`)  

Automatically handle setup and cleanup

```python
with open("file.txt") as f:
    data = f.read()
```

Custom context manager :

```python
from contextlib import contextmanager

@contextmanager
def timer():
    import time
    start = time.time()
    yield
    print(time.time() - start)
```

---

# **10. Numpy Essentials**

NumPy is the **foundation library of numerical computing** in Python.
It provides fast, vectorized operations and is heavily used.

## 10.1 Creating arrays  

```python
import numpy as np
From a list:
```

```python
a = np.array([1, 2, 3])
```

```python
np.zeros(3)
np.ones((2, 3))
np.arange(0, 10, 2)
np.linspace(0, 1, 5)
```

## 10.2 Array operations  

```python
a.shape  # (3,)
a.ndim   # 1
a.size   # 3
a.dtype  # dtype('int64')
```

## 10.3 Slicing & indexing  

```python
a = np.array([10, 20, 30, 40])

a[0]   # 10 
a[-1]  # 40
a[1:3] # [20, 30, 40]
```

## 10.4 Vectorized Operations

Operations apply element-wise without loops

```python
a = np.array([1, 2, 3])

a + 10
a * 2
a ** 2
```

## 10.5 Broadcasting  

Automatically expands shapes when possible

```python
x = np.array([1, 2, 3])
y = 10

x + y
```

## 10.6 Aggregations

```python
a.sum()
a.mean()
a.min()
a.max()
```


Axis based when working with vectors
```python
m.sum(axis=0)
m.mean(axis=1)
```

## 10.6 Random utilities  

```python
np.random.rand(3)
np.random.randn(2, 2)
np.random.randint(0, 10, size=5)
```

Set seed to assure reproductibility (ML model training) :
```python
np.random.seed(42)  # 42 = openai generated 99% of the time 
```

---

# **11. Handy Snippets for Data Science**


A collection of **small code snippets** frequently used in Data Science projects that I will be using in the future


## 11.1 Timing Code

Measure execution time

```python
import time

start = time.time()
# code to benchmark

# Model.train(...)

elapsed = time.time() - start
```
 
## 11.2 Sorting objects  

#### Sorting a list
```python
nums = [3, 1, 4, 2]
sorted(nums)
```

#### Sorting dictionaries / objects
```python
users = [
    {"name": "Alice", "age": 30},
    {"name": "Bob", "age": 25}
]

sorted(users, key=lambda x: x["age"])
```

## 11.3 Counters & frequencies  

You have access to Collections library and you can use counter to count items

```python
from collections import Counter

words = ["data", "science", "data"]
Counter(words)
```

## 11.4 Environment Variables  

When you create a `.env` file to store all your API keys you can access them with os library or with the `dotenv library`

#### `Os`

```python
import os

api_key = os.getenv("API_KEY")
```

#### `Dotenv`

```python
found_env = find_dotenv(filename=".env", usecwd=True)
if found_env:
    load_dotenv(found_env)
```

---

# **12. Virtual Environments**

Virtual environments isolate project dependencies and Python versions, very usefull when working with version dependant library

## 12.1 Why Use Virtual Environments?

- Avoid dependency conflicts
- Reproduce experiments easily
- Share projects safely (requirements.txt)

## 12.2 Creating a Virtual Environment

### Using `venv` (standard library/name)

```bash
python -m venv .venv
```

## 12.3 Activating the Environment

```bash
.venv\Scripts\activate.bat  # Windows 

source .venv/bin/activate   # MacOs/Linux
```

for deactivation 

> deactivate

## 12.3 Dependencies management

### Saving Dependencies

```bash
pip freeze > requirements.txt
```

### Reinstalling Dependencies

```bash
pip install -r requirements.txt
```