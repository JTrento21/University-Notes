Asymptotic Complexity (revision) 

## Algorithm Complexity

Complexity describes **how an algorithm's resource requirements change as the input size `n` increases**.

The two resources we're mainly interested in are:

|Type|Measures|
|---|---|
|**Time complexity**|How execution time / number of operations grows|
|**Space complexity**|How much memory usage grows|

The important idea is **growth**, not the exact number of seconds.

For example:

`T(n) = 2n² + 9n`

For large `n`, the `n²` term dominates, so we treat this as:

**O(n²)**

---

# 2. Asymptotic Notation

Asymptotic notation lets us describe algorithm efficiency without actually running the program.

When determining complexity:

**Ignore constants → ignore smaller terms → keep the dominant term.**

Example:

`4n³ + 7n² + n log n`

Dominant term = `n³`

Therefore:

**O(n³)**

### Big-O — O

Big-O describes an **asymptotic upper bound**.

In this module, you'll normally use it to describe how an algorithm's running time grows.

Examples:

`3n + 10` → **O(n)**

`5n² + 2n + 7` → **O(n²)**

`3n log n - n` → **O(n log n)**

`4n³ + 7n² + n log n` → **O(n³)**

### Big-Omega — Ω

**Ω** describes an asymptotic **lower bound**.

Think:

> The algorithm/function grows **at least this quickly**.

### Big-Theta — Θ

**Θ** gives a **tight bound**.

Think:

> The function grows at this rate asymptotically.

For example:

`3n² + 5n + 2 = Θ(n²)`

because `n²` accurately describes its asymptotic growth.

### Important Big-O detail

Technically:

`n² = O(n²)`

but also:

`n² = O(n³)`

and even:

`n² = O(2ⁿ)`

because Big-O is an **upper bound**.

However, you normally give the **tightest useful bound**, so you'd write:

**O(n²)**

rather than O(n³).

---

# 3. Common Growth Rates

Know this general ordering:

**O(1) < O(log n) < O(n) < O(n log n) < O(n²) < O(n³) < O(2ⁿ) < O(n!)**

### What they mean

|Complexity|Name|Example|
|---|---|---|
|**O(1)**|Constant|Accessing `array[i]`|
|**O(log n)**|Logarithmic|Binary search|
|**O(n)**|Linear|Linear search|
|**O(n log n)**|Linearithmic|Common efficient sorting complexity|
|**O(n²)**|Quadratic|Bubble sort|
|**O(2ⁿ)**|Exponential|Extremely expensive as `n` grows|

The further right you go, the worse the algorithm scales.

### Why O(log n) is so good

Suppose you repeatedly halve a problem.

With roughly **1,000 elements**, only around 10 halvings are needed because:

`2¹⁰ = 1024`

With roughly **1,000,000 elements**, it's only around 20:

`2²⁰ ≈ 1,000,000`

That's the principle behind binary search.

---

# 4. Arrays

An **array** is a sequence of elements stored so they can be addressed using consecutive indices.

Python sequences such as:

`list`, `tuple`, `str`

support array-style indexing.

Python uses **zero-based indexing**:

```
Index:  0    1    2    3
Array: [A]  [B]  [C]  [D]
```

For an array containing `n` elements, the valid indices are:

**0 → n - 1**

So an array of 10 elements has indices:

**0–9**

---

# 5. Arrays in Memory

One of the most important properties of an array is its relationship with memory.

Conceptually, array elements occupy **contiguous memory locations**.

```
        consecutive memory
              ↓
[A][B][C][D][E]
 0  1  2  3  4
```

Because the elements have predictable locations, the computer can calculate where an element is directly.

Conceptually:

**address of element = starting address + offset**

This is why:

`a[1]`

and

`a[100]`

can both be accessed in:

**O(1)**

The computer doesn't need to walk through elements `0 → 99` first.

---

# 6. Array Operations — Know This

This is probably the most useful quick-reference table from the lecture.

|Operation|Complexity|Why?|
|---|---|---|
|Access by index|**O(1)**|Address calculated directly|
|Linear search|**O(n)**|May inspect every element|
|Binary search|**O(log n)**|Search area halves each step|
|Insert|**O(1) – O(n)**|Depends on whether elements must shift|
|Delete|**O(1) – O(n)**|Depends on whether elements must shift|

**Binary search requires the array to be sorted.**

---

# 7. Inserting into an Array

Suppose:

```
[A][B][C][D]
```

and we want to insert `X` at index 1.

We can't simply overwrite `B`.

The existing elements need to move:

```
Before:

[A][B][C][D]
    ↑
  insert X


Shift elements right:

[A][B][B][C][D]
    

Insert X:

[A][X][B][C][D]
```

The lecture's insertion algorithm essentially does:

1. Shift the necessary elements **one position right**.
2. Place the new value into the free position.

### Complexity

If inserting near the end, very little shifting may be required.

If inserting near the beginning, nearly every element might need to move.

For `n` elements, there can be up to approximately `n` copies.

Therefore:

**Worst-case insertion = O(n)**

---

# 8. Deleting from an Array

Deletion has the opposite problem.

Suppose:

```
[A][B][C][D][E]
```

Delete `B`:

```
[A][ ][C][D][E]
```

We don't want to leave a gap, so elements shift left:

```
[A][C][D][E][ ]
```

The lecture's algorithm therefore:

1. Moves later elements **one position left**.
2. Marks the final position as unoccupied.

### Complexity

Again, potentially `n - 1` elements need moving.

Therefore:

**Worst-case deletion = O(n)**

This illustrates a fundamental array trade-off:

> **Very fast random access, but potentially expensive insertion and deletion.**

---

# 9. Searching Arrays

The lecture introduces two searching algorithms:

### Linear Search

Works on:

**sorted OR unsorted arrays**

It checks elements sequentially.

```
Target = 7

[4][2][9][7][1]
 ↑
    ↑
       ↑
          ✓
```

Conceptually:

```
for element in array:    if element == target:        return found
```

### Complexity

Best case:

Target is first element.

**O(1)**

Worst case:

Target is last or isn't present.

Need to inspect `n` elements.

**O(n)**

The lecture therefore describes linear search overall as:

**O(n)**

For a successful search, the average number of comparisons is roughly:

**n / 2**

An unsuccessful search requires:

**n comparisons**

---

# 10. Binary Search

Binary search is significantly faster than linear search — **but the data must be sorted**.

Example:

```
Target = 70

[10][20][30][40][50][60][70][80][90]
                 ↑
               middle
```

Compare target with the middle value.

`70 > 50`

Everything below 50 can now be ignored:

```
[60][70][80][90]
```

Choose the middle again and continue.

Every iteration removes approximately **half of the remaining search space**.

---

# 11. Binary Search Variables

The lecture uses three important variables:

`l` = left boundary

`r` = right boundary

`m` = middle index

Initially:

```
l                         r
↓                         ↓
[10][20][30][40][50][60][70]
             ↑
             m
```

Then compare:

### `target == a[m]`

Found it.

### `target < a[m]`

Target must be on the **left**.

Set:

`r = m - 1`

### `target > a[m]`

Target must be on the **right**.

Set:

`l = m + 1`

Repeat while:

`l ≤ r`

If eventually:

`l > r`

the target isn't present.

---

# 12. Why Binary Search is O(log n)

This is worth understanding rather than memorising.

Imagine there are 16 elements.

```
16
↓
8
↓
4
↓
2
↓
1
```

Every comparison halves the search space.

That's only about **4 steps**.

In general, the question is:

> How many times can I divide `n` by 2 before reaching 1?

Answer:

**log₂(n)**

Therefore:

**Binary search = O(log n)**

The lecture gives the maximum number of comparisons as approximately:

**⌊log₂ n⌋ + 1**

---

# 13. Linear Search vs Binary Search

||Linear Search|Binary Search|
|---|---|---|
|Complexity|**O(n)**|**O(log n)**|
|Sorted array required?|❌ No|✅ Yes|
|Strategy|Check one-by-one|Repeatedly halve search area|
|Unsuccessful search|Up to `n` comparisons|About `log₂ n` comparisons|

Example with **1,000,000 elements**:

Linear search could require roughly:

**1,000,000 comparisons**

Binary search requires only roughly:

**20 comparisons**

because:

`2²⁰ ≈ 1,048,576`

That's a massive difference.

---

# 14. The Core Array Trade-Off

Remember this:

> **Arrays give fast O(1) indexed access because of their memory layout, but maintaining the array's structure can make insertion and deletion O(n).**

Then searching depends on what you know about the data:

```
ARRAY
 │
 ├── Access by index ─────────── O(1)
 │
 ├── Search
 │    ├── Linear ─────────────── O(n)
 │    └── Binary (sorted) ────── O(log n)
 │
 ├── Insert ──────────────────── up to O(n)
 │
 └── Delete ──────────────────── up to O(n)
```