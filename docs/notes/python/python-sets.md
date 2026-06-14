
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

### Mathematical Set Operations

Python sets support standard mathematical operations using both methods and operators:

- **Union (`a | b`):** All unique elements from both sets.
- **Intersection (`a & b`):** Elements present in both sets.
- **Difference (`a - b`):** Elements in `a` but not in `b`.
- **Symmetric Difference (`a ^ b`):** Elements in `a` or `b` but *not* both.
- **Subset (`a <= b`):** Checks if all elements of `a` are inside `b`.
- **Superset (`a >= b`):** Checks if `a` contains all elements of `b`.

### Removing duplicates

**Set is great for removing duplicates from lists**

```python title="sets.py"
items = ["apple", "banana", "apple", "orange"]
unique_items = set(items)  # → {'apple', 'banana', 'orange'}
```

---