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
## 4.1 Function definition & return values  
## 4.2 `*args` and `**kwargs`  
## 4.3 Lambda functions  
## 4.4 Built-ins: `map`, `filter`, `reduce`  

---

# **5. Error Handling**
## 5.1 Try / Except  
## 5.2 Common exceptions  
## 5.3 Raising errors  

---

# **6. Modules & Imports**
## 6.1 Importing modules  
## 6.2 Creating your own module  
## 6.3 Useful standard libraries  

---

# **7. Classes & Object-Oriented Basics**
## 7.1 Class definition  
## 7.2 Attributes & methods  
## 7.3 Inheritance  
## 7.4 Magic methods (`__str__`, `__len__`, etc.)  

---

# **8. File Handling**
## 8.1 Reading files  
## 8.2 Writing files  
## 8.3 Working with JSON  

---

# **9. Useful Python Features**
## 9.1 List / Dict / Set comprehensions  
## 9.2 Decorators (intro)  
## 9.3 Context managers (`with`)  
## 9.4 Generators & `yield`  

---

# **10. Numpy Essentials**
## 10.1 Creating arrays  
## 10.2 Array operations  
## 10.3 Slicing & indexing  
## 10.4 Broadcasting  
## 10.5 Random utilities  

---

# **11. Handy Snippets for Data Science**
## 11.1 Timing code  
## 11.2 Sorting objects  
## 11.3 Counters & frequencies  
## 11.4 Working with paths (`pathlib`)  

---

# **12. To-Do (Future Sections)**
- Python typing (`typing`)  
- Virtual environments  
- Unit testing  
- Logging  
- Multiprocessing  

---