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