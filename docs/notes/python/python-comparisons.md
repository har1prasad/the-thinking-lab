## Conditional Statement

**if statement** = If the condition is True, the code inside the if block runs.  
allows your program to make decisions by checking if a condition is True or False.  
[if, elif, else]

```python title="conditional_statements.py"
age = int(input("Enter you age: "))

if age >= 18:   # if
    print("hurray! you are an adult.")
elif age == 17: # elif
    print("one more year to go pal.")
elif age >= 65:
    print("you are a seniour citizen.")
else:           # else
    print("you are basically a kid.")
```

### Comparison Operators

- **What is it?** Operators that compare two values and evaluate to a boolean (`True` or `False`).
- **Operators:** 
    * `==` (equal to), `!=` (not equal to)
    * `<` (less than), `>` (greater than)
    * `<=` (less than or equal to), `>=` (greater than or equal to)
- **Syntax:** `value1 op value2`
- **Caveat:** Be careful not to confuse `==` (comparison) with `=` (variable assignment).

---
