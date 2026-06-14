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

### Modern Dictionary Merging

Prior to Python 3.9, merging dictionaries required using `.update()` or unpacking (`{**d1, **d2}`). Python 3.9 introduced:

- Merge operator (`|`): returns a new dictionary.
- Update operator (`|=`): merges in-place.


### Dictionary Merging and Defaults

```python
dict_a = {"x": 1, "y": 2}
dict_b = {"y": 99, "z": 4}  # Overlapping key 'y'

# Merge returns a new dict (values from right dict override left)
merged = dict_a | dict_b
print(merged)  # Output: {'x': 1, 'y': 99, 'z': 4}

# Using setdefault
# If key exists, returns value. If not, inserts key with default and returns default.
counts = {}
counts.setdefault("apple", 0)
counts["apple"] += 1
print(counts)  # Output: {'apple': 1}
```

---