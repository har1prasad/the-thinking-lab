# Algorithms

An algorithm is just a clear, step-by-step set of instructions to solve a problem or complete a task. In programming, it's the logic behind your code — the thinking before the typing.

Important points (keep these in your head):

- It must be **step-by-step**
- It must be **clear** — no ambiguity
- It must **end** — finite steps
- It must **solve a specific problem**

👉 **Coding is just writing an algorithm in a programming language.**  

If your thinking is weak, your code will be weak — no matter how many languages you learn.

---

#### Find Minimum — A Simple Example

A good first algorithm to understand: find the smallest number in a list.

The approach is straightforward:

1. Set `minimum` to positive infinity — `float("inf")` — so any real number will be smaller
2. Walk through each number in the list; if it's smaller than `minimum`, update `minimum`
3. At the end, `minimum` holds the answer

```python title="find_minimum.py"
def find_minimum(nums):
    if not nums:
        return None

    min = float("inf")

    for num in nums:
        if num < min:
            min = num

    return min
```

!!! tip "Real talk"
    Python has a built-in `min()` function that does this in one line. But writing it manually is the point — this is how you start *seeing* what an algorithm actually is.

---

#### Efficiency Matters — Even for Simple Problems

Now consider finding the longest string in a list: 

```python title="find_longest_string.py"
def find_longest_string(lst):
    longest_so_far = ""

    for s in lst:
        if len(s) > len(longest_so_far):
            longest_so_far = s

    return longest_so_far
```

With five strings, this is instant. With 5 billion? That's where it gets interesting — and that's exactly the kind of question computer science asks you to sit with.

!!! info
    If you've heard (usually exaggerated) stories about Leetcode and whiteboarding interviews, you might hear the word "algorithm" and think it's synonymous with "hard problem." That's really not the case, and believing it will only psych you out.


!!! quote "Quote"
    *"We suffer more often in imagination than in reality."*

    -- Seneca

---

