# Sorting Algorithms

Almost every action you take in a web app relies on sorted data. Just looking up a user's profile in a database likely relies on a sorted index 

Fortunately, most programming languages provide their own standard sorting implementation. In Python, for example, we can use the sorted function:

```python
items = [1, 5, 3]
print(sorted(items)) # [1, 3, 5]
```

---

## Bubble Sort

if the standard `sorted()` function exists, why should we learn to write a sorting algorithm from scratch?

In all seriousness, in this we'll be building some of the most famous sorting algorithms from scratch because:

- It's good to understand how they work under the hood
- It's great algorithmic thinking practice

Bubble sort is the sorting algorithm that everyone learns but no one actually uses in the real world — because it's so slow. We learn it because it's easy to understand. And once we appreciate how slow it is, the other sorting algorithms are just that much more impressive.

It all starts with an unsorted list of numbers. Then we loop from left to right and compare each pair of neighbouring numbers. If the number on the right is smaller than the number on the left, we swap them. Otherwise, we leave them alone.

When we get to the end, we go back to the start and do it again. We repeat this over and over until we complete a full pass from left to right without making a single swap — at that point, the list is sorted.

#### Let's walk through a concrete example with `[5, 3, 8, 1, 6]`.

<div style="border:1px solid var(--md-default-fg-color--lightest);border-radius:8px;padding:1.5rem;margin:1.5rem 0;background:var(--md-code-bg-color);">

<div id="bs-bars" style="display:flex;align-items:flex-end;justify-content:center;gap:12px;height:160px;margin-bottom:1rem;"></div>

<div style="display:flex;gap:16px;justify-content:center;margin-bottom:0.75rem;font-size:0.75rem;color:var(--md-default-fg-color--light);">
  <span><span style="display:inline-block;width:12px;height:12px;background:#378ADD;border-radius:2px;margin-right:4px;vertical-align:middle;"></span>Comparing</span>
  <span><span style="display:inline-block;width:12px;height:12px;background:#EF9F27;border-radius:2px;margin-right:4px;vertical-align:middle;"></span>Swapped</span>
  <span><span style="display:inline-block;width:12px;height:12px;background:#639922;border-radius:2px;margin-right:4px;vertical-align:middle;"></span>Sorted</span>
</div>

<div id="bs-info" style="text-align:center;font-size:0.85rem;color:var(--md-default-fg-color--light);min-height:22px;margin-bottom:1rem;">Press Next Step to begin.</div>

<div style="display:flex;gap:8px;justify-content:center;flex-wrap:wrap;">
  <button onclick="bsReset()" style="padding:6px 16px;border-radius:4px;border:1px solid var(--md-default-fg-color--lightest);background:transparent;color:var(--md-default-fg-color);cursor:pointer;font-size:0.85rem;">&#8635; Reset</button>
  <button onclick="bsPrev()"  style="padding:6px 16px;border-radius:4px;border:1px solid var(--md-default-fg-color--lightest);background:transparent;color:var(--md-default-fg-color);cursor:pointer;font-size:0.85rem;">&#8592; Prev</button>
  <button onclick="bsNext()"  style="padding:6px 16px;border-radius:4px;border:1px solid var(--md-default-fg-color--lightest);background:transparent;color:var(--md-default-fg-color);cursor:pointer;font-size:0.85rem;">Next &#8594;</button>
</div>

</div>

<script>
(function () {
  const ORIGINAL = [5, 3, 8, 1, 6];
  const C = { def: '#B4B2A9', cmp: '#378ADD', swp: '#EF9F27', done: '#639922' };
  const MAX = Math.max(...ORIGINAL);
  let history = [], ptr = 0, timer = null;

  function buildHistory(arr) {
    const steps = [], a = [...arr];
    let swapped;
    steps.push({ arr: [...a], i: -1, j: -1, swapped: false, done: false, msg: 'Starting state — unsorted.' });
    do {
      swapped = false;
      for (let j = 0; j < a.length - 1; j++) {
        if (a[j] > a[j + 1]) {
          steps.push({ arr: [...a], i: j, j: j+1, swapped: false, done: false, msg: 'Comparing ' + a[j] + ' and ' + a[j+1] + ' — ' + a[j] + ' > ' + a[j+1] + ', so swap them.' });
          [a[j], a[j+1]] = [a[j+1], a[j]];
          swapped = true;
          steps.push({ arr: [...a], i: j, j: j+1, swapped: true, done: false, msg: 'Swapped! ' + a[j] + ' is now on the left.' });
        } else {
          steps.push({ arr: [...a], i: j, j: j+1, swapped: false, done: false, msg: 'Comparing ' + a[j] + ' and ' + a[j+1] + ' — already in order, no swap needed.' });
        }
      }
      steps.push(swapped
        ? { arr: [...a], i: -1, j: -1, swapped: false, done: false, msg: 'End of pass — going back to the start.' }
        : { arr: [...a], i: -1, j: -1, swapped: false, done: true,  msg: 'No swaps this pass — the list is sorted!' });
    } while (swapped);
    return steps;
  }

  function render(idx) {
    const s = history[idx];
    const el = document.getElementById('bs-bars');
    if (!el) return;
    el.innerHTML = '';
    s.arr.forEach(function(val, i) {
      var color = C.def;
      if (s.done) color = C.done;
      else if (i === s.i || i === s.j) color = s.swapped ? C.swp : C.cmp;
      var h = Math.max(20, Math.round((val / MAX) * 130));
      el.innerHTML += '<div style="display:flex;flex-direction:column;align-items:center;gap:4px;">'
        + '<div style="width:48px;height:' + h + 'px;background:' + color + ';border-radius:4px 4px 0 0;transition:background 0.2s;"></div>'
        + '<span style="font-size:13px;font-weight:500;color:var(--md-default-fg-color--light);">' + val + '</span>'
        + '</div>';
    });
    var info = document.getElementById('bs-info');
    if (!info) return;
    info.innerHTML = s.done
      ? '<span style="background:#e8f5e9;color:#2e7d32;padding:2px 12px;border-radius:99px;font-size:0.8rem;font-weight:500;">Sorted!</span> ' + s.msg
      : s.msg;
  }

  window.bsNext  = function() { if (ptr < history.length - 1) render(++ptr); };
  window.bsPrev  = function() { if (ptr > 0) render(--ptr); };
  window.bsReset = function() { clearInterval(timer); ptr = 0; render(0); };

  history = buildHistory(ORIGINAL);
  render(0);
})();
</script>

Notice what happened — the largest number, 8, got pushed all the way to the right in just one pass. Like a bubble rising to the surface. That's where the name comes from.

**Pass 2, Pass 3...** keep happening until a full pass produces zero swaps. At that point the algorithm knows it's done.

The key insight is this — in the worst case, for every single item in the list, you might have to loop over the entire list again. A **loop inside a loop**. That's **O(n²)** — and it's why bubble sort falls apart the moment your data gets large.

Bubble sort repeatedly steps through a slice and compares adjacent elements, swapping them if they are out of order. It continues to loop over the slice until the whole list is completely sorted. Here's the pseudocode:

### Pseudocode 🧠

1. Set `swapping` to **True**

2. Set `end` to the length of the input list

3. While `swapping` is **True**:

    1. Set `swapping` to **False**

    2. For i from the 2nd element to end:

        - If the `(i-1)th` element of the input list is greater than the `ith` element:

            a. Swap the `(i-1)th` element and the `ith` element  
            b. Set `swapping` to **True**

    3. Decrement `end` by one

4. Return the sorted list


!!! note ""
    **Try to Create the bubble_sort algorithm according to the described Pseudocode above.**


??? example "Reveal: bubble_sort"
    ```python
    def bubble_sort(nums):
    swapping = True
    end = len(nums)

    while swapping:
        swapping = False
        for i in range(1, end):
            if nums[i-1] > nums[i]:
                #swapping 2 values without temp
                nums[i-1], nums[i] = nums[i], nums[i-1] 
                swapping = True
        end-=1
    return nums
    ```

### Best and Worst Case

In the case of bubble sort, the best and worst case scenarios can actually change the time complexity: 

- **Best case**: If the data is pre-sorted, bubble sort becomes really fast. Because it only need to do one pass
- **Worst case**: If the data is in reverse order, bubble sort becomes really slow (but still in the same complexity class as random data). Because every comparison leads to a swap, resulting in the maximum number of operations (O(n²)).

---

