# Basics

!!! warning "Before You Start"

    These notes are designed **only for quick revision**.

    They are **not meant for absolute beginners**. If you are new to programming or Python, you should first learn the basics from beginner tutorials.

    Once you understand the fundamentals, come back here for fast revision.

## Introduction to Python

Python is a popular programming language. It was created by **Guido van Rossum** and **released in 1991**.

Python is widely used for:

- Web development (server-side)
- Software development
- Mathematics and scientific computing
- System scripting

Python runs on an **interpreter system**, meaning that code can be executed as soon as it is written. This allows **very fast prototyping and testing**.

!!! note "Interpreter"
    An **interpreter** is a program that reads and executes code **line by line** instead of converting the entire program into machine code before running it.

    In simple terms:

    **Interpreter → reads one line → executes it immediately → moves to the next line**

Python supports multiple programming styles:

- **Procedural programming**
- **Object-oriented programming (OOP)**
- **Functional programming**

---

## Python Syntax

#### New Lines Instead of Semicolons

Python uses **new lines to complete a command**, unlike many other programming languages that use **semicolons (`;`)** or **parentheses**.

Example:

```python title="example.py"
print("Hello")
print("World")
```

---

#### Indentation-Based Structure

Python uses **indentation (whitespace)** to define blocks of code such as:

- loops
- functions
- classes
- conditional statements

Other programming languages usually use **curly braces `{}`** for this purpose.

Example:

```python title="indentation_example.py"
if True:
    print("This is inside the block")
```

---

#### Dynamically Typed Language

Python is a **dynamically typed language**.

!!! note "Dynamic Typing"
    In a dynamically typed language, you **do not need to declare the data type** of a variable.

    The type of the variable is **decided automatically when the program runs**.

Example:

```python title="dynamic_typing.py"
x = 10        # integer
x = "hello"   # now it becomes a string
```

---

## Variables & Data Types

**variable** = A reusable container for a value (string, integer, float, boolean). The variable behaves as if it was the value that it contains

**data type** = classification that tells the computer what kind of value a variable holds and what operations can be performed on it.

### Simple data types

```python title="simple_variables_datatypes.py"
myname = "Hariprasad AP"     # string data type | str: text
myage = 21                   # integer data type | int: whole number
mycgpa = 7.67                # float data type | float: decimal number
is_student = True            # boolean data type | bool: True/False
complex_num = 3 + 4j         # complex data type | complex: real + imaginary
```

### Collection data types

```python title="Collection_variables_datatypes.py"
fruits_list = ["apple", "banana"]                  # list: ordered collection
colors_tuple = ("red", "green")                    # tuple: ordered, immutable
num_range = range(1, 5)                            # range: sequence of numbers
person_dict = {"name": "Hariprasad", "age": 21}    # dict: key-value pairs
unique_set = {1, 2, 3}                             # set: unique elements
frozen_set = frozenset([4, 5])                     # frozenset: immutable set
```

### Binary data types

```python title="binary_datatypes.py"
byte_data = b"hello"                  # bytes: immutable binary
byte_array = bytearray([65, 66])      # bytearray: mutable binary
mem_view = memoryview(byte_data)      # memoryview: view of binary data
```

---

## Conditional Statement

**if statement** = If the condition is True, the code inside the if block runs.  
allows your program to make decisions by checking if a condition is True or False.  
[if, elif, else]

```python title="conditional_statements.py"
age = int(input("Enter you age: "))

if age >= 18:   # if
    print("hurray! you are an adult.")
elif age == 17: # elif
    print("one more year to go pal.")
elif age >= 65:
    print("you are a seniour citizen.")
else:           # else
    print("you are basically a kid.")
```

---

## Looping Statements

Loops are used to repeat a block of code multiple times. Instead of writing the same code over and over, you use a loop.

### For Loop

**for loop** = used to iterate over a sequence [string, list, set, tuple].
repeat a block of code an exact amount of time

```python title="for_loop.py"
fruitlist = ["banana", "apple", "orange", "watermelon"]

for i in range(10):       # in case of range - range(start, end, step)
    print(i)              # print from 0-9

for x in fruitlist:
    # iterates over each item in this list (same for string, set and tuple)
    print(x)
```

### While Loop

**while loop** = repeats a block of code as long as a condition is True.  
we should re-check the condition at the end of the loop

```python title="while_loop.py"
name = input("Enter your name: ")

while(name == ""):
    name = input("Enter your name: ")

print(f"your name is {name}")
```

This while loop keeps asking "Enter your name:" until you type something.
If you press Enter without typing, it asks again. (That is the condition will be true so it loops again)
If you enter a name, the loop stops. (Here, the condition will turn false so it does not repeat)

---

## String

**String** = an ordered sequence of characters, enclosed in quotes.  
Strings are immutable  once created, they cannot be changed [only can be altered or chnaged using slicing].

### Indexing and Slicing

**Indexing** = allows accessing individual characters in a string using [index]  
**Slicing** = allows extracting substrings using [start : end : step]

```python title="string_indexing_slicing.py"
credit_number = "1234-5678-9012-3456"  # Example credit card number with hyphens

print(credit_number[0])          # Get the first character (index 0) → "1"
print(credit_number[0:4])        # Get characters from index 0 to 3 (end is exclusive) → "1234"
print(credit_number[:4])         # Same as [0:4] (start defaults to 0) → "1234"
print(credit_number[4:8])        # Get characters from index 4 to 7 → "-567"
print(credit_number[4:])         # Get all characters from index 4 to the end → "-5678-9012-3456"
print(credit_number[-1])         # Get the last character (negative index) → "6"
print(credit_number[-4:])        # Get the last 4 characters → "3456"
print(credit_number[::2])        # Get every 2nd character (step=2) → "13-68-13-46"
print(credit_number[::3])        # Get every 3rd character (step=3) → "14-8245"
print(credit_number[::-1])       # Reversed → "6543-2109-8765-4321"
```

### String Methods

```python title="string_methods.py"
name = input("Enter your name: ")
phone_number = input("Enter your phone #: ")

length = len(name)               # Calculate the length (number of characters) of the name
index = name.find(" ")           # Find the index of the first space in the name (return -1 if none)
name = name.capitalize()         # Capitalize the first letter of name
name = name.upper()              # Convert all characters in the name to uppercase
name = name.lower()              # Convert all characters in the name to lowercase
result = name.isdigit()          # Check if the name consists only of digits (returns True/False)
result = name.isalpha()          # Check if the name consists only of alphabets (returns True/False)
result = phone_number.count(" ") # Count how many space characters are in the phone number
phone_number = phone_number.replace("-", "") # Remove hyphens from the phone number
```

---

## List

**Collection** = single "variable" used to store multiple values  
**List** = [] ordered and changeable. Duplicates OK  
we can iterate over this using for loop and can access using indexes

### Modifying the list

```python title="lists.py"
fruits = ["banana", "apple", "orange", "watermelon"]

fruits.append("grape")                   # Adds "grape" at the end
fruits.insert(1, "kiwi")                 # Inserts "kiwi" at index 1
fruits.extend(["pear", "mango"])         # Adds multiple items at the end
```

### Removing elements

```python title="lists.py"
fruits = ["banana", "apple", "orange", "watermelon"]

fruits.remove("apple")       # Removes first "apple"
popped = fruits.pop(2)       # Removes the item at position 2 and stores it in popped
fruits.clear()               # Empties the list → []
```

### Information methods

```python title="lists.py"
fruits = ["banana", "apple", "orange", "watermelon"]

print(fruits.count("apple"))  # Returns count of "apple" → 1
print(fruits.index("orange")) # Returns index of first "orange" → 2
```

### Reorganizing

```python title="lists.py"
fruits = ["banana", "apple", "orange", "watermelon"]

fruits.reverse()             # Reverses the list → ["watermelon", "orange", "apple", "banana"]
fruits.sort()                # Sorts alphabetically → ["apple", "banana", "orange", "watermelon"]
```

### Copying

```python title="lists.py"
fruits_copy = fruits.copy()  # Creates a shallow copy → ["apple", "banana", "orange", "watermelon"]
```

### Basic list operations

```python title="lists.py"
fruits = ["banana", "apple", "orange", "watermelon"]

print(len(fruits))      # Returns number of items → 4
print(min(fruits))      # Returns lexicographically smallest item → "apple"
print(max(fruits))      # Returns lexicographically largest item → "watermelon"

# in case of numbers min returns smallest and max returns largest

# sum() requires numeric values
numbers = [10, 20, 30, 40]
print(sum(numbers))     # Returns sum of all numbers → 100
print(sum(numbers[:2])) # Sum of first two numbers → 30 (10+20)
```

## List Comprehensions

**List Comprehensions** = a concise way to create lists in Python. It allows you to generate a new list by applying an expression to each item in an existing iterable.

**Syntax**: [expression *for* value *in* iterable *if* condition]  
- Compact alternative to for-loops  
- More readable for simple transformations/filtering

### Basic numeric examples

```python title="list_comprehensions.py"
# Generate doubled values from 1 to 10
doubles = [x * 2 for x in range(1, 11)]
# Result: [2, 4, 6, 8, 10, 12, 14, 16, 18, 20]
```

### String operations

```python title="list_comprehensions.py"
fruits = ["apple", "orange", "banana", "coconut"]

# Convert all fruits to uppercase
uppercase_words = [fruit.upper() for fruit in fruits]
# Result: ['APPLE', 'ORANGE', 'BANANA', 'COCONUT']
```

### Conditional filtering

```python title="list_comprehensions.py"
numbers = [1, -2, 3, -4, 5, -6, 8, -7]

# Filter positive numbers
positive_numbers = [x for x in numbers if x >= 0]
# Result: [1, 3, 5, 8]
```

---

## Sets

**collection** = single "variable" used to store multiple values  
**Set** = {} unordered, unindexed, and **no duplicates allowed**  
Mutable: we can add or remove items, but we can't access them by index  
Useful when uniqueness is important or for fast membership tests

### Creating a set

```python title="sets.py"
fruits = {"banana", "apple", "orange", "watermelon", "apple"}  # duplicate "apple" will be removed

print(fruits)  # Output: {'banana', 'apple', 'orange', 'watermelon'} → unordered, no duplicates
```

### Adding elements

```python title="sets.py"
fruits = {"banana", "apple", "orange", "watermelon"}

fruits.add("grape")              # Adds "grape" to the set
fruits.update(["kiwi", "mango"]) # Adds multiple items
```

### Removing elements

```python title="sets.py"
fruits = {"banana", "apple", "orange", "watermelon"}

fruits.remove("banana")         # Removes "banana" → Error if not present
fruits.discard("pear")          # Safely removes "pear" if it exists (no error)
popped = fruits.pop()           # Removes and returns a random item
fruits.clear()                  # Empties the set → set()
```

### Copying a set

```python title="sets.py"
fruits_copy = fruits.copy()     # Shallow copy of the set
```

### Checking membership

```python title="sets.py"
fruits = {"banana", "apple", "orange", "watermelon"}

print("apple" in fruits)        # True
print("kiwi" in fruits)         # False
```

### Set operations

```python title="sets.py"
a = {1, 2, 3, 4}
b = {3, 4, 5, 6}

print(a.union(b))                    # All unique values → {1, 2, 3, 4, 5, 6}
print(a.intersection(b))             # Common values → {3, 4}
print(a.difference(b))               # In a but not in b → {1, 2}
print(a.symmetric_difference(b))     # In either a or b but not both → {1, 2, 5, 6}
```

### Removing duplicates

**Set is great for removing duplicates from lists**

```python title="sets.py"
items = ["apple", "banana", "apple", "orange"]
unique_items = set(items)  # → {'apple', 'banana', 'orange'}
```

---

## Tuples

**collection** = single "variable" used to store multiple values  
**Tuple** = () ordered and unchangeable (immutable). Duplicates allowed.  
Faster and memory-efficient than lists. Good for fixed data.  
Tuples are useful for:

- Returning multiple values from functions
- Storing related but unchangeable data (e.g., coordinates, RGB values)

### Creating a tuple

```python title="tuples.py"
fruits = ("banana", "apple", "orange", "watermelon", "apple")
```

### Accessing items

```python title="tuples.py"
fruits = ("banana", "apple", "orange", "watermelon", "apple")

print(fruits[1])           # Access by index → "apple"
print(fruits[-1])          # Last item → "apple"
```

### Iterating

```python title="tuples.py"
fruits = ("banana", "apple", "orange", "watermelon", "apple")

for fruit in fruits:
    print(fruit)
```

### Count and index

```python title="tuples.py"
fruits = ("banana", "apple", "orange", "watermelon", "apple")

print(fruits.count("apple"))   # → 2 (counts how many times "apple" appears)
print(fruits.index("orange"))  # → 2 (position of first "orange")
```

### Length

```python title="tuples.py"
fruits = ("banana", "apple", "orange", "watermelon", "apple")

print(len(fruits))             # → 5
```

### Min/Max for strings

It does this lexicographically

```python title="tuples.py"
fruits = ("banana", "apple", "orange", "watermelon", "apple")

print(min(fruits))             # → "apple"
print(max(fruits))             # → "watermelon"
```

### Slicing

```python title="tuples.py"
fruits = ("banana", "apple", "orange", "watermelon", "apple")

print(fruits[1:3])  # → ("apple", "orange")
```

### Copying a tuple

Just assign since it's immutable

```python title="tuples.py"
fruits = ("banana", "apple", "orange", "watermelon", "apple")

fruits_copy = fruits  # Both point to same tuple (safe because it can't be changed)
```

---

## Dictionaries

**collection** = single "variable" used to store multiple values  
**Dictionary** = {key: value} → unordered, changeable, no duplicate keys  
Keys must be unique and immutable (e.g., strings, numbers)  
Dictionary is great for:

- Storing key-value pairs like user data, config settings
- Fast lookup by key
- Organizing structured info

### Creating a dictionary

```python title="dictionaries.py"
person = {
    "name": "Hari",
    "age": 22,
    "location": "India"
}
```

### Accessing values

```python title="dictionaries.py"
person = {
    "name": "Hari",
    "age": 22,
    "location": "India"
}

print(person["name"])        # → "Hari"
print(person.get("age"))     # → 22
print(person.get("email"))   # → None (safe way to access non-existing key)
```

### Adding or updating values

```python title="dictionaries.py"
person = {
    "name": "Hari",
    "age": 22,
    "location": "India"
}

person["email"] = "hari@example.com"     # Adds new key-value
person["age"] = 23                       # Updates existing key
```

### Removing items

```python title="dictionaries.py"
person = {
    "name": "Hari",
    "age": 22,
    "location": "India"
}

del person["location"]                  # Deletes "location"
removed = person.pop("email")           # Removes and returns "email"
print("Removed:", removed)

# popitem() removes the last inserted pair (Python 3.7+)
last_item = person.popitem()
print("Last item removed:", last_item)
```

### Clearing the dictionary

```python title="dictionaries.py"
person = {
    "name": "Hari",
    "age": 22,
    "location": "India"
}

person.clear()      # → {}
```

### Dictionary methods

```python title="dictionaries.py"
person = {
    "name": "Hari",
    "age": 22,
    "location": "India"
}

print(person.keys())       # → dict_keys(['name', 'age', 'location'])
print(person.values())     # → dict_values(['Hari', 22, 'India'])
print(person.items())      # → dict_items([('name', 'Hari'), ('age', 22), ('location', 'India')])
```

### Looping through dictionary

```python title="dictionaries.py"
person = {
    "name": "Hari",
    "age": 22,
    "location": "India"
}

for key in person:
    print(key, "→", person[key])
```

### Copying a dictionary

```python title="dictionaries.py"
person = {
    "name": "Hari",
    "age": 22,
    "location": "India"
}

person_copy = person.copy()
```

### Nested dictionary

```python title="dictionaries.py"
student = {
    "name": "Hari",
    "grades": {
        "math": 85,
        "science": 90
    }
}
print(student["grades"]["math"])  # → 85
```

---

## Functions

**Function** = **reusable blocks of code** that perform specific tasks. They help organize code, avoid repetition, and make programs easier to understand.

In Python functions, the terms **parameter** and **argument** are often used interchangeably, but they have distinct meanings:

- **Parameter** is the variable name listed in the function **definition** (the placeholder).
- **Argument** is the actual value you pass to the function when you **call** it.

### Parameters & Arguments

```python title="functions.py"
def greet(name):          # 'name' is a parameter
    print(f"Hello, {name}!")

greet("Alice")            # "Alice" is an argument
```

Here:

- `name` is the **parameter**.
- `"Alice"` is the **argument**.

In short: **parameters are the blueprint; arguments are the materials you give to follow that blueprint.**

### Defining a simple function

```python title="functions.py"
def greet(name):
    """This function greets the person passed as parameter"""
    print(f"Hello, {name}!")

# Calling the function
greet("Alice")  # Output: Hello, Alice!
```

### Function with return value

```python title="functions.py"
def square(number):
    """Returns the square of a number"""
    return number * number

result = square(5)
print(result)  # Output: 25
```

### Function with multiple parameters

```python title="functions.py"
def add_numbers(a, b):
    """Adds two numbers and returns the result"""
    return a + b

sum_result = add_numbers(3, 7)
print(sum_result)  # Output: 10
```

### Function with default arguments

```python title="functions.py"
def power(base, exponent=2):
    """Raises base to the power of exponent (default is 2)"""
    return base ** exponent

print(power(3))     # Output: 9 (uses default exponent)
print(power(3, 3))  # Output: 27
```

### Variable-length arguments (*args)

**Variable-length arguments (`*args`)** = `*args` allows a function to accept any number of positional arguments. The arguments are **packed into a tuple** inside the function.

```python title="functions.py"
def average(*numbers):
    """Calculates average of any number of values"""
    return sum(numbers) / len(numbers)

print(average(1, 2, 3))        # Output: 2.0
print(average(10, 20, 30, 40)) # Output: 25.0

def add(*numbers):
    total = 0
    for number in numbers:
        total += number
    return total

print(add(10, 10, 10, 10, 10, 10, 10, 10, 10, 10))
```

### Keyword arguments (**kwargs)

**Keyword arguments (`**kwargs`)** = `**kwargs` allows a function to accept any number of keyword arguments. The arguments are **packed into a dictionary** inside the function.

```python title="functions.py"
def person_info(**details):
    """Prints person information from keyword arguments"""
    for key, value in details.items():
        print(f"{key}: {value}")

person_info(name="John", age=30, city="New York")
# Output:
# name: John
# age: 30
# city: New York
```

### Lambda functions

**Lambda functions** are small, **anonymous functions** defined using the `lambda` keyword. They can have any number of arguments but only one expression. The expression is evaluated and returned.

#### Syntax

```python
lambda arguments: expression
```

- `lambda` – keyword
- `arguments` – comma-separated list of parameters
- `expression` – a single Python expression (cannot contain statements like `return`, `if-else` can be used as a conditional expression though)

```python title="lambda.py"
multiply = lambda x, y: x * y
print(multiply(4, 5))  # Output: 20

numbers = [1, 2, 3, 4, 5]
squared = list(map(lambda x: x**2, numbers))
print(squared)  # Output: [1, 4, 9, 16, 25]
```

Often used with **map()**, **filter()**, **reduce()** & **sorted**

#### Common use cases

##### 1. With `map()` – apply function to every item

```python title="lambda.py"
numbers = [1, 2, 3, 4, 5]

squared = list(map(lambda x: x**2, numbers))
print(squared)            # Output: [1, 4, 9, 16, 25]

names = ["alice", "bob", "charlie"]
upper_names = list(map(lambda name: name.upper(), names))
print(upper_names)        # Output: ['ALICE', 'BOB', 'CHARLIE']
```

##### 2. With `filter()` – keep items that satisfy a condition

```python title="lambda.py"
numbers = [1, 2, 3, 4, 5, 6, 7, 8]

evens = list(filter(lambda x: x % 2 == 0, numbers))
print(evens)              # Output: [2, 4, 6, 8]

words = ["hi", "hello", "hey", "greetings"]
long_words = list(filter(lambda w: len(w) > 3, words))
print(long_words)         # Output: ['hello', 'greetings']
```

##### 3. With `sorted()` – custom sorting key

```python title="lambda.py"
students = [
    {"name": "Alice", "grade": 85},
    {"name": "Bob", "grade": 92},
    {"name": "Charlie", "grade": 78}
]

sorted_by_grade = sorted(students, key=lambda student: student["grade"])
print(sorted_by_grade)
# Output:
# [{'name': 'Charlie', 'grade': 78}, {'name': 'Alice', 'grade': 85}, {'name': 'Bob', 'grade': 92}]

names = ["Alice", "Bob", "Christopher"]
sorted_names = sorted(names, key=lambda name: len(name))
print(sorted_names)       # Output: ['Bob', 'Alice', 'Christopher']
```

##### 4. With `reduce()` – cumulative operation (from `functools`)

```python title="lambda.py"
from functools import reduce

numbers = [1, 2, 3, 4]
product = reduce(lambda x, y: x * y, numbers)
print(product)            # Output: 24 (1*2*3*4)
```

### Recursive function

A **recursive function** is a function that **calls itself** in order to solve a problem. Recursion is a technique where the solution to a problem depends on solving smaller instances of the same problem.

```python title="functions.py"
def factorial(n):
    """Calculates factorial recursively"""
    if n == 1:
        return 1
    else:
        return n * factorial(n-1)

print(factorial(5))  # Output: 120
```

### Function annotations (type hints)

```python title="functions.py"
def circle_area(radius: float) -> float:
    """Calculates area of circle with type hints"""
    return 3.14159 * radius ** 2

print(circle_area(2.5))  # Output: 19.6349375
```

### Scope of variables

```python title="functions.py"
global_var = "I'm global"

def scope_demo():
    local_var = "I'm local"
    print(local_var)   # Can access local variable
    print(global_var)  # Can access global variable

scope_demo()
# print(local_var)  # Would cause error - local_var not defined outside function
```

### Function docstrings

```python title="functions.py"
def documented_function():
    """This is a docstring.
    
    It can span multiple lines and explain:
    - What the function does
    - What parameters it takes
    - What it returns
    """
    return "This function is well-documented"

# Accessing the docstring
print(documented_function.__doc__)
```

---
