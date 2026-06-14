**operator** = a symbol that tells Python to perform a specific computation  
**expression** = any combination of values, variables, and operators that produces a result  

Operators are the building blocks of logic in Python — arithmetic, comparison, assignment, bitwise, and beyond.

For detailed explanation of operators : [w3schools - python operators](https://www.w3schools.com/python/python_operators.asp)

---

### Division 

```python title="operators.py"
print(7 / 2)    # → 3.5  (true division — always a float)
print(7 // 2)   # → 3    (floor division — rounds DOWN to nearest integer)
print(7 % 2)    # → 1    (modulo — gives the remainder)
```

**`/`** always returns a float, even if the result is whole (`4 / 2` → `2.0`).  
**`//`** rounds toward **negative infinity**, not zero — this matters with negatives:

```python title="operators.py"
print(-7 // 2)  # → -4  (NOT -3 — floor goes down, not toward zero)
```

**`%`** is more useful than it looks:

- `n % 2 == 0` → even number check
- `index % length` → wrap around a circular list
- `seconds % 60` → extract remaining seconds

---

### Exponentiation

```python title="operators.py"
print(2 ** 3)      # → 8   (2 to the power of 3)
print(2 ** 0.5)    # → 1.4142... (square root)
```

!!! warning "Exponentiation is right-to-left"
    Unlike every other operator, `**` evaluates right to left:
    ```python title="operators.py"
    print(2 ** 3 ** 2)   # → 512  (reads as 2 ** (3**2) = 2 ** 9)
    print(-2 ** 2)        # → -4   (reads as -(2**2), NOT (-2)**2)
    print((-2) ** 2)      # → 4    (use parentheses to be explicit)
    ```

---

### The Walrus Operator (`:=`)

**Walrus operator** = assigns a value to a variable *inside* an expression (Python 3.8+)

Without walrus — you call `len()` twice and write an extra line:

```python title="operators.py"
user_input = input("Type something: ")
if len(user_input) > 0:
    print(f"Length is {len(user_input)}")  # len() called again
```

With walrus — assign and check in one shot:

```python title="operators.py"
if (n := len(input("Type something: "))) > 0:
    print(f"Length is {n}")               # n is already stored
```

Best used in:

- `while` loops checking file lines or network chunks
- Regex match + use: `if m := re.search(pattern, text)`
- Any place where you'd compute something just to immediately check it

---

### Bitwise Operators

**Bitwise operators** = work on the actual binary (0s and 1s) of an integer

```python title="operators.py"
a = 5   # binary: 0101
b = 3   # binary: 0011

print(a & b)   # → 1   AND  (0101 & 0011 = 0001)
print(a | b)   # → 7   OR   (0101 | 0011 = 0111)
print(a ^ b)   # → 6   XOR  (0101 ^ 0011 = 0110)
print(~a)      # → -6  NOT  (flips all bits)
print(a << 1)  # → 10  Left shift  (= multiply by 2)
print(a >> 1)  # → 2   Right shift (= divide by 2, drop remainder)
```

| Operator | Name | What it keeps |
| :--- | :--- | :--- |
| `&` | AND | bit only if **both** have it |
| `\|` | OR | bit if **either** has it |
| `^` | XOR | bit if **exactly one** has it |
| `<<` | Left shift | shifts bits left, pads with 0s |
| `>>` | Right shift | shifts bits right, drops remainder |

Bitwise operators appear in permission flags, system programming, and certain interview problems.  
In everyday Python, `<<` and `>>` are occasionally useful as fast multiply/divide by powers of 2.

---

### Operator Precedence

Python evaluates in this order (highest → lowest):

| Priority | Operators |
| :--- | :--- |
| 1 | `()` parentheses |
| 2 | `**` exponentiation |
| 3 | `+x`, `-x`, `~x` unary |
| 4 | `*`, `/`, `//`, `%` |
| 5 | `+`, `-` |
| 6 | `<<`, `>>` bitwise shifts |
| 7 | `&` bitwise AND |
| 8 | `^`, `\|` bitwise XOR / OR |
| 9 | `<`, `>`, `==`, `is`, `in` comparisons |
| 10 | `not`, `and`, `or` logical |

**Rule of thumb:** if you're unsure, just use parentheses. They cost nothing and make intent obvious.

---

### Floating Point Gotcha

```python title="operators.py"
print(0.1 + 0.2 == 0.3)    # → False  ← this surprises everyone
print(0.1 + 0.2)            # → 0.30000000000000004
```

Not a Python bug — computers store decimals in binary, which can't represent `0.1` exactly.  
The tiny errors compound when you add them.

Never use `==` to compare floats. Use `math.isclose()` instead:

```python title="operators.py"
import math

print(math.isclose(0.1 + 0.2, 0.3))  # → True
```

---

!!! tip "The one-line takeaway"
    Python has three kinds of division, right-associative exponentiation, and floats that lie at the decimal — use `//` for integer math, parentheses for clarity, and `math.isclose()` for float comparisons.