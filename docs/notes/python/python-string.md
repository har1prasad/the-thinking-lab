
**String** = an ordered sequence of characters, enclosed in quotes.  
Strings are immutable  once created, they cannot be changed [only can be altered or chnaged using slicing].

### Indexing and Slicing

**Indexing** = allows accessing individual characters in a string using [index]  
**Slicing** = allows extracting substrings using [start : end : step]

```python title="string_indexing_slicing.py"
credit_number = "1234-5678-9012-3456"  # Example credit card number with hyphens

print(credit_number[0])          # Get the first character (index 0) → "1"
print(credit_number[0:4])        # Get characters from index 0 to 3 (end is exclusive) → "1234"
print(credit_number[:4])         # Same as [0:4] (start defaults to 0) → "1234"
print(credit_number[4:8])        # Get characters from index 4 to 7 → "-567"
print(credit_number[4:])         # Get all characters from index 4 to the end → "-5678-9012-3456"
print(credit_number[-1])         # Get the last character (negative index) → "6"
print(credit_number[-4:])        # Get the last 4 characters → "3456"
print(credit_number[::2])        # Get every 2nd character (step=2) → "13-68-13-46"
print(credit_number[::3])        # Get every 3rd character (step=3) → "14-8245"
print(credit_number[::-1])       # Reversed → "6543-2109-8765-4321"
```

### String Methods

```python title="string_methods.py"
name = input("Enter your name: ")
phone_number = input("Enter your phone #: ")

length = len(name)               # Calculate the length (number of characters) of the name
index = name.find(" ")           # Find the index of the first space in the name (return -1 if none)
name = name.capitalize()         # Capitalize the first letter of name
name = name.upper()              # Convert all characters in the name to uppercase
name = name.lower()              # Convert all characters in the name to lowercase
result = name.isdigit()          # Check if the name consists only of digits (returns True/False)
result = name.isalpha()          # Check if the name consists only of alphabets (returns True/False)
result = phone_number.count(" ") # Count how many space characters are in the phone number
phone_number = phone_number.replace("-", "") # Remove hyphens from the phone number
```

---