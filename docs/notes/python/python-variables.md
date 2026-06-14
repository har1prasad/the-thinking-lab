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
