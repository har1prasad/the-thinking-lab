# Data Structures 

## The simple definition

A **data structure** is a way to organize data in memory so it's easy to access and modify. That's it.

It has three things going on at once — it stores data values, it captures relationships between those values, and it provides operations (functions) to read or change the data.

Python's `list` and `dict` are both data structures. You've been using them. You just didn't have a name for the category.

## Data structures and algorithms 

Here's the thing — data structures *use* algorithms to work internally, and then those data structures get *used by* other algorithms. The line between them is blurry on purpose. A list's indexing operation? That's an algorithm. A sorting function? It uses a list. They're inseparable.

---

## Lists  

A list is ordered by index. Index zero, then one, then two. The *values* inside can be added in any order you want, but the positions are always tracked.

Because of that, some operations are blazing fast and some are surprisingly slow.

- **Append** → O(1). Adding to the end is fast. The list just drops the new item at the next available slot.
- **Index lookup** → O(1). When you do `animals[2]`, the computer jumps *directly* to that address in memory. No scanning. No counting. Direct jump.
- **Delete from middle** → O(n). If you remove an item at index 5, everything from index 6 onward has to shift down by one. The longer the list, the more shifting — that's O(n).
- **Search** → O(n). If you want to find a specific value (say, `"Ford"` in a list of cars), you have to check every item until you find it. The list doesn't know where `"Ford"` lives — only where index 3 lives.

Lists work great until you hit one of two situations:

- You're frequently **deleting items from the middle** — every deletion triggers a cascade of shifts
- You're frequently **searching for a specific value** — every search is a full scan

That's not a failure of lists. It's just a signal that a different data structure might fit better.

#### Index lookup vs iteration — what's actually different

A common confusion: why is `list[753]` instant, but `for item in list` slow?

Because an index is like a memory address. The computer doesn't need to "walk" to position 753 — it knows exactly where to find it in RAM. It's a direct lookup.

Iteration is a deliberate walk. You start at index 0 and move forward one step at a time. You *can* stop early with `break` or `return`, but worst case you go all the way to the end — O(n).

---

## Tuple

A tuple is a list that made a promise — *I will not change.* Same ordered structure, same index-based access, but once it's created, it's locked.

Because of that, some operations carry over from lists and some simply don't exist.

- **Index lookup** → O(1). Same as a list — `point[0]` jumps directly to that address in memory.
- **Search** → O(n). No special ordering of values, so finding a specific one still means walking through the whole thing.
- **No append, no delete.** Tuples are immutable. There's nothing to add or remove.

Tuples work great when:

- The data has a fixed shape that **shouldn't change** — coordinates, RGB values, a (name, age) pair
- You want to use the data as a **dictionary key** — lists can't do this because they're mutable, tuples can

That's not a limitation. It's the point. Immutability is a feature, not a missing feature.

#### Why immutability matters beyond safety

When Python sees a tuple, it knows the size is fixed forever. That lets it store it more efficiently in memory compared to a list, which has to keep some extra room in case you append. Small gain, but real.

---

## Set

A set throws away two things you might take for granted — **order** and **duplicates**. What it gives you in return is blazing-fast lookup.

- **Add** → O(1) on average. Drop an item in. Python hashes it and places it at the right spot internally.
- **Membership check** → O(1) on average. `"apple" in my_set` doesn't scan anything. It hashes `"apple"`, jumps to that location, checks if it's there. Done.
- **Delete** → O(1) on average. Same idea — hash, jump, remove.
- **Search by value** → O(1). This is the headline. Compare that to O(n) for a list.

Sets work great when:

- You need to **check if something exists** — frequently and fast
- You need to **remove duplicates** from a collection
- You're doing **set math** — unions, intersections, differences between two groups of data

Sets hurt when:

- You need to **preserve order** — sets have none
- You need to **access items by position** — `my_set[0]` doesn't exist

#### Why is membership check O(1)?

Because a set uses a **hash table** under the hood. When you add `"apple"`, Python runs it through a hash function — a formula that converts the value into a number, which maps to a memory slot. When you later ask *"is apple in here?"*, it runs the same formula, jumps to the same slot, and checks. No scanning. The value tells you where to look.

---

## Dictionary

A dictionary is what you get when you want the fast lookup of a set, but you also want to *store something* at each key — not just know if it exists.

- **Insert / Update** → O(1) on average. `user["name"] = "Hari"` hashes the key and stores the value at that location.
- **Key lookup** → O(1) on average. `user["name"]` hashes `"name"`, jumps to the slot, returns the value. Same idea as a set.
- **Delete** → O(1) on average. Hash the key, find the slot, remove it.
- **Search by value** → O(n). Keys are hashed and fast. Values are not — finding a specific value means walking every entry.

Dictionaries work great when:

- You're **labeling data** — `{"age": 24, "city": "Bangalore"}` beats a mystery list like `[24, "Bangalore"]`
- You need **fast lookup by a meaningful key** — names, IDs, usernames
- You're **counting or grouping** — `{"marketer": 12, "engineer": 30}`

Dictionaries hurt when:

- You need to **find something by value** — that's O(n), no shortcuts
- You need **ordering by insertion or sorting** — modern Python (3.7+) does preserve insertion order, but a dict is still not the right tool if ordering is the primary concern

#### Set vs Dictionary — they're cousins

A set is essentially a dictionary with keys and no values. Both use the same hash table mechanism internally. That's why their lookup speeds are identical — and why both can only store **hashable** (immutable) keys. You can use a string or a tuple as a key. You can't use a list.

---

> For the technical breakdown of each — syntax, methods, and gotchas — head over to the:

 - [Python List](../python/python-basics.md#list) 
 - [Python Set](../python/python-basics.md#sets) 
 - [Python Tuple](../python/python-basics.md#tuples) 
 - [Python Dictionaries](../python/python-basics.md#dictionaries)


!!! tip "The one-line takeaway"
    A data structure is just data + structure + operations — and every operation has a Big-O cost you should know before you pick one.