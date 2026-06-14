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
