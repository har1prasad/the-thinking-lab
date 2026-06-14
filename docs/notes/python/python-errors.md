
Most programs are written assuming everything goes right. Exception handling is how you write code that survives when it doesn't.

---

### Syntax Error vs Exception

These are two different *kinds* of wrong — and Python catches them at different times.

**Syntax Error** = Python can't even read your code. Caught *before* the program runs.

**Exception (Runtime Error)** = The code is readable, but something breaks *while* it's running.

```python title="errors.py"
# SYNTAX ERROR — Python won't even start
print("hello"          # → SyntaxError: '(' was never closed

# EXCEPTION — Valid code, breaks at runtime
result = 10 / 0        # → ZeroDivisionError: division by zero
name_list = ["Hari"]
print(name_list[5])    # → IndexError: list index out of range
```

So. Syntax errors are grammar mistakes. Exceptions are things that *could* go wrong depending on data, user input, or the environment.

---

### The `try-except-else-finally` Block

Here's the thing about exceptions — you can *anticipate* them. The `try` block lets you say: "run this, but if it breaks, here's what to do instead."

**`try`** = code that might fail  
**`except ExceptionType`** = what to do *if* that specific error happens  
**`else`** = what to do *only if* no error happened  
**`finally`** = what to do *no matter what* — runs always

```python title="errors.py"
def safe_divide(a, b):
    try:
        result = a / b                          # This might throw ZeroDivisionError or TypeError
    except ZeroDivisionError as e:
        print(f"Can't divide by zero: {e}")     # → Runs only on ZeroDivisionError
        result = None
    except TypeError as e:
        print(f"Wrong types: {e}")              # → Runs only on TypeError
        result = None
    else:
        print("Division worked!")               # → Runs only if NO exception was raised
    finally:
        print("Cleaning up...")                 # → ALWAYS runs, no matter what

    return result

safe_divide(10, 2)   # → Division worked! → Cleaning up... → 5.0
safe_divide(10, 0)   # → Can't divide by zero... → Cleaning up... → None
```

Notice what's happening: `else` and `except` are opposites. Only one of them runs per execution. But `finally` is loyal — it runs regardless.

`finally` is where you close files, release database connections, or clean up any resource you opened in `try`. Think of it as "always do this on your way out."

---

### Catching Specific Exceptions

The mistake beginners make: catching everything with a bare `except:`.

It feels safe, but it's dangerous. A bare `except:` catches *everything* — including `KeyboardInterrupt` (Ctrl+C) and `SystemExit`. Your program becomes impossible to stop.

```python title="errors.py"
# ❌ BAD — catches everything, hides real bugs
try:
    data = fetch_data()
except:
    print("Something went wrong.")   # What went wrong? No idea.

# ✅ GOOD — target the specific error you know how to handle
try:
    data = fetch_data()
except ConnectionError:
    print("Network issue. Retrying...")
```

You can handle multiple specific exceptions in one block:

```python title="errors.py"
try:
    value = int(input("Enter a number: "))
    result = 100 / value
except ValueError:
    print("That's not a number.")        # → Input was something like "abc"
except ZeroDivisionError:
    print("Can't divide by zero.")       # → Input was 0
```

---

### Raising Exceptions

You're not limited to catching exceptions Python raises. You can raise them yourself using `raise`.

**`raise`** = manually trigger an exception — useful for validating inputs before something breaks further down

```python title="errors.py"
def set_age(age):
    if age < 0:
        raise ValueError("Age cannot be negative.")   # Raise with a message
    return age

try:
    set_age(-5)
except ValueError as e:
    print(f"Invalid input: {e}")   # → Invalid input: Age cannot be negative.
```

You can also *re-raise* a caught exception to let the caller know it happened, after logging it:

```python title="errors.py"
try:
    open("missing_file.txt", "r")
except FileNotFoundError as e:
    print("Logged: file not found")
    raise    # → Re-raises the same FileNotFoundError, original traceback preserved
```

---

### Custom Exceptions

When you're building something real — an app, a library, an API — generic exceptions like `ValueError` don't tell you *what went wrong in your domain*.

**Custom exception** = a class that inherits from `Exception`, giving you a named, meaningful error specific to your logic.

```python title="errors.py"
# Define a custom exception
class NegativeValueError(Exception):
    """Raised when a negative number is passed where only positive values are allowed."""
    def __init__(self, value, message="Value cannot be negative"):
        self.value = value
        self.message = message
        super().__init__(self.message)   # Pass message to the base Exception class


def square_root(x):
    if x < 0:
        raise NegativeValueError(x, f"Got {x}, expected a positive number")
    return x ** 0.5


try:
    print(square_root(-9))
except NegativeValueError as e:
    print(f"Custom error caught: {e.message}")   # → Custom error caught: Got -9...
    print(f"Bad value was: {e.value}")           # → Bad value was: -9
```

Good names for custom exceptions:

- `InsufficientBalanceError` — banking app
- `UserNotPermittedError` — auth system
- `InvalidConfigError` — config loader

The name alone tells the next developer exactly what broke, without reading the message.

---

### Common Built-in Exceptions

| Exception | When it happens |
| :--- | :--- |
| `ValueError` | Right type, wrong value — `int("abc")` |
| `TypeError` | Wrong type entirely — `len(5)` |
| `IndexError` | List index out of range — `lst[10]` on a 3-item list |
| `KeyError` | Dict key doesn't exist — `d["missing"]` |
| `ZeroDivisionError` | Dividing or modulo by zero |
| `FileNotFoundError` | File or path doesn't exist |
| `AttributeError` | Object doesn't have that attribute — `"hello".push()` |
| `NameError` | Variable used before it was defined |

---

!!! tip "The one-line takeaway"
    Wrap only the risky line in `try`, catch the specific exception you expect, use `finally` to clean up, and never use a bare `except:` — it turns your program into a black box that swallows its own bugs.