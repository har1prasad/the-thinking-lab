# Object-Oriented Programming

!!! warning "Work in Progress"

    This page covers the *why* of OOP and the contrast with procedural programming.
    The concepts section — classes, objects, inheritance, and the rest — will be added soon.

---

I learned C first. Because of that, the procedural way of thinking was the only way I knew Functions, global data, top-down flow — that was just "how programming worked" in my head.

OOP didn't make sense to me until I stopped asking *"what is it?"* and started asking *"why does it exist?"*
This page is my answer to that question.

---

## Procedural Programming

Procedure-oriented programming is a paradigm centered on functions and routines. You break a program into a linear, top-down sequence of steps. The focus is on *how* to do things — the process, the algorithm, the steps.

C is a good example of this. And since C was my first language, this was my default way of thinking.

<figure markdown="span">
    ![Procedural Programming](./figures/POP.png){width="400"}
</figure>

**How it works:**

- The program starts with a main routine and breaks down into smaller functions
- Data is often global — shared and accessible across the entire program
- Functions can be reused, but there's no concept of things *owning* their own data

### Characteristics of Procedural Programming

- Follows a **top-down approach**, where the program is broken into smaller functions step by step (e.g., `main() → input() → process() → output()`)  
- Focuses on **procedures (functions)** — how the task is performed  
- Uses **shared/global data**, which can be accessed and modified by multiple functions  
- Supports **basic code reuse** through functions, but lacks advanced reuse like inheritance  

**Where it works well:** simple programs, scripts, small utilities.

### Advantages of Procedural Programming

- Simple and easy to understand for beginners  
- Efficient in terms of memory and performance for small programs  
- Clear step-by-step flow makes logic straightforward  

**Where it breaks down:** once the program grows, global data becomes dangerous, functions start depending on each other in unpredictable ways, and every change risks breaking something elsewhere.

### Disadvantages of Procedural Programming

- Becomes difficult to manage as the program grows  
- Global data can lead to **security and data integrity issues**  
- Harder to reuse and extend code for larger systems  
- Changes in one part can affect other parts unexpectedly  

---

## Why OOP exists 

Imagine a guy named Arun who learned programming using C.

One day he gets a job managing a small restaurant system. At first he writes everything the way he learned separate functions for taking orders, updating stock, calculating bills. It works fine... until things grow.

Now there are multiple waiters, hundreds of items, discounts, different customer types. His code becomes a mess. Every change breaks something else. He's spending more time fixing old code than building new features.

Then someone shows him a different way.

*"Think of your program like your restaurant."*

Instead of scattered functions, you create objects:

- A **Customer** — with a name, an order, a bill
- An **Item** — with a price and stock
- An **Order** — with items and a total

Now each thing manages itself. If you want to change how billing works
you go to the `Order` — not hunt through 50 functions. 
If you need a new type of customer (VIP), you don't rewrite everything — you just extend it.

That's Object-Oriented Programming.

You don't use it because it's fancy.
You use it because once your program stops being small,
the "functions everywhere" approach collapses.
OOP gives structure. It turns chaos into systems.
It lets you think like an engineer instead of just someone writing instructions.

## Object-Oriented Programming

Object-Oriented Programming is a paradigm centered on **objects and data models**. You organize a program around real-world entities, where each object combines data (attributes) and behavior (methods). Instead of writing a linear sequence of steps, you structure your code as interacting components. The focus is on **what things are and what they can do**, rather than just the procedure to follow.

<figure markdown="span">
    ![Object-Oriented Programming](./figures/OOP.png){width="400"}
</figure>

### Advantages of OOP

- Provides a clear structure to programs
- Makes code easier to maintain, reuse, and debug
- Helps keep your code **DRY (Don't Repeat Yourself)**
- Allows you to build reusable applications with less code

!!! note "DRY principle"
    The **DRY principle** means you should avoid writing the same code more than once. Move repeated code into functions or classes and reuse it.

---

## Coffee Machine

This is the clearest way I found to understand the difference. The same coffee machine program, written in both styles. Same functionality. Very different structure.

---

### Procedural way

Everything lives in one file. Global data. Functions that reach into shared state.

<figure markdown="span">
    ![Procedural Programming Menu program](./figures/pop_menu.jpeg)
</figure>

It works. But notice — `profit` and `resources` are global. Any function can touch them.
`check_price` modifies `profit` directly. If something goes wrong, you have to trace
through every function to find where the data changed.

Now imagine this program with ten more features. That's Arun's problem.

---

### Object oriented way

Same program. Split across four files. Each class owns its own data and behavior.

<figure markdown="span">
    ![OOP Cofee maker](./figures/coffee_maker.png)
</figure>

<figure markdown="span">
    ![OOP menu](./figures/menu.png)
</figure>

<figure markdown="span">
    ![OOP money machine](./figures/money_maker.png)
</figure>

<figure markdown="span">
    ![OOP main](./figures/main.png)
</figure>

---

### What actually changed

The functionality is identical. But look at `main.py` in the OOP version —
it reads almost like plain English. You can understand what the program does
without reading a single other file.

More importantly: `profit` is no longer a global variable floating around.
It belongs to `MoneyMachine`. `resources` belongs to `CoffeeMaker`.
If something breaks, you know exactly where to look.

That's the shift. Not just cleaner code — **clearer ownership.**

When something breaks, you don't search. You go to the class that owns that thing.

In Object-Oriented Programming, I can modify internal implementation as long as the interface (input/output) stays the same, without needing to understand the entire system.

---

## Core concepts in OOP

### Class

**Class:** A structural blueprint that defines the data attributes and behaviors (methods) for a specific type of entity. It dictates the architecture of what an entity will be, but it allocates no memory on its own.

- Class is non primitive (user defined) data type, it is combination of characteristics and behaviors.

For example, take a class of sixty students. If you want to store one student in the database, we will write their name and register number. But what if another student comes? We would again write variables for name and reg no. This way, multiple memory locations are allocated to different variables, but they are all doing the same work.

Here, we know that name and reg no. are common for every student—whether there are 50 or 100. So in this case, we can store name and reg no. as a blueprint called a **class**. Whenever a new student is added or removed, we simply update the value of that variable (i.e., create a new object or modify an existing one).

So a **class** is a structure that defines what an object can do, and the **object** does the actual work.

### Object

**Object:** A concrete, usable instance created from a class blueprint that occupies memory and holds its own specific data values. If a class is the architectural schematic for a building, the object is the physical building itself.

- An attribute is just a fancy word for a variable that's associated with a modeled object.
- A method goes along the same vein. As you can clearly see, these are just functions, but we call it a method because it's a function that a particular modeled object can do.
- In OOP, we're trying to model real-life objects, and those objects have things, and they also can do things. The things that they have are their attributes(variables), and these are usually modeled with variables. The things that they can do are called methods(functions), and they are modeled by functions.
- In OOP, we refer to the blueprint or template as a class. And we call the individual objects that are generated from the blueprint an object.

#### Example of Class and object

<figure markdown="span">
    ![Class and object example](./figures/Class-Object.png)
</figure>

- **Inheritance:** A mechanism where a new class automatically adopts the properties and behaviors of an existing parent class. This establishes a logical hierarchy and promotes clean code reuse as your systems scale over time.

- **Abstraction:** The practice of exposing only the necessary, high-level interactions of a system while hiding the complex, underlying execution logic. It allows developers to interact with powerful systems efficiently without getting bogged down in the internal wiring.

- **Polymorphism:** The ability to treat different objects interchangeably through a shared interface, even if their underlying executions differ. It keeps your architecture flexible, allowing a single command to trigger different, appropriate behaviors depending on the specific object receiving it.

- **Encapsulation:** The strict bundling of data and the methods that operate on it into a single, secure container, restricting unauthorized external access. It acts as a protective boundary, ensuring an object's internal state cannot be arbitrarily altered or corrupted by outside interference.

