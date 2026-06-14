
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
