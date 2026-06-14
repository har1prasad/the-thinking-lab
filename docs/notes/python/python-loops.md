## Looping Statements

Loops are used to repeat a block of code multiple times. Instead of writing the same code over and over, you use a loop.

### For Loop

**for loop** = used to iterate over a sequence [string, list, set, tuple].
repeat a block of code an exact amount of time

```python title="for_loop.py"
fruitlist = ["banana", "apple", "orange", "watermelon"]

for i in range(10):       # in case of range - range(start, end, step)
    print(i)              # print from 0-9

for x in fruitlist:
    # iterates over each item in this list (same for string, set and tuple)
    print(x)
```

### While Loop

**while loop** = repeats a block of code as long as a condition is True.  
we should re-check the condition at the end of the loop

```python title="while_loop.py"
name = input("Enter your name: ")

while(name == ""):
    name = input("Enter your name: ")

print(f"your name is {name}")
```

This while loop keeps asking "Enter your name:" until you type something.
If you press Enter without typing, it asks again. (That is the condition will be true so it loops again)
If you enter a name, the loop stops. (Here, the condition will turn false so it does not repeat)

---
