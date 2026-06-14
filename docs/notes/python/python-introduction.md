# Introduction

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
