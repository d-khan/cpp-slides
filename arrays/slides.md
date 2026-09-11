---
theme: dracula
background: https://cover.sli.dev
title: Arrays
author: Dr Danish Khan
transition: fade-out
mdc: true

---

# Arrays


Dr. Danish Khan | dkhan@sdccd.edu


Press Space for next page

---

# Learning Outcomes

::div{class="normal-text-small" style="font-size:1.1rem; line-height:1.6;"}

By the end of this lecture, you should be able to:

- **Declare, initialize, access, and traverse** built-in arrays in C++.
- Explain how array elements are organized in **contiguous memory** and how indexing works.
- Create and manage **dynamically allocated arrays** using `new[]` and `delete[]`.
- Use `std::vector` to create and manipulate **dynamic-size collections**.
- Distinguish between a vector's **size** and **capacity**.
- Declare, initialize, access, and traverse **two-dimensional arrays and vectors**.
- Explain how 2D arrays are stored using **row-major order**.
- Use `std::array` for **fixed-size collections** in modern C++.
- Select an appropriate container among **built-in arrays, `std::array`, and `std::vector`**.
- Pass arrays and standard library containers to **functions** appropriately.

::


---

# Navigation

Hover on the bottom-left corner to see the navigation's controls panel, [learn more](https://sli.dev/guide/ui#navigation-bar)

## Keyboard Shortcuts

|                                                     |                             |
| --------------------------------------------------- | --------------------------- |
| <kbd>right</kbd> / <kbd>space</kbd>                 | next animation or slide     |
| <kbd>left</kbd>  / <kbd>shift</kbd><kbd>space</kbd> | previous animation or slide |
| <kbd>up</kbd>                                       | previous slide              |
| <kbd>down</kbd>                                     | next slide                  |

<!-- https://sli.dev/guide/animations.html#click-animation -->
<img
  v-click
  class="absolute -bottom-9 -left-7 w-80 opacity-50"
  src="https://sli.dev/assets/arrow-bottom-left.svg"
  alt=""
/>
<p v-after class="absolute bottom-23 left-45 opacity-30 transform -rotate-10">Here!</p>

---

# Arrays in C++

::div{class="normal-text-small" style="font-size:1.15rem; line-height:1.5;"}

An **array** stores multiple values of the **same data type** under one variable name.

### Without an Array

```cpp
int score1 = 85;
int score2 = 90;
int score3 = 78;
int score4 = 92;
int score5 = 88;
```

### With an Array

```cpp
int scores[5] = {85, 90, 78, 92, 88};
```

Instead of managing five separate variables, we can work with one collection called `scores`.

::

::div{class="definition-box" style="margin-top:20px !important; font-size:1.15rem !important;"}
An **array** is a fixed-size collection of elements of the **same data type**.
::

---

# Array Elements and Indexes

::div{class="normal-text-small" style="font-size:1.15rem; line-height:1.4;"}

Each value stored in an array is called an **element**. Each element is accessed using its **index**.

```cpp
int scores[5] = {85, 90, 78, 92, 88};
```

::

::div{style="margin-top:18px; display:flex; justify-content:center;"}

<div style="display:grid; grid-template-columns:90px repeat(5, 100px); text-align:center; font-size:1.15rem;">

<div style="padding:5px; font-weight:bold; text-align:left;">Index</div>
<div style="padding:5px;">0</div>
<div style="padding:5px;">1</div>
<div style="padding:5px;">2</div>
<div style="padding:5px;">3</div>
<div style="padding:5px;">4</div>

<div style="padding:14px 5px; font-weight:bold; text-align:left;">scores</div>
<div style="padding:14px; border:2px solid #aaa;">85</div>
<div style="padding:14px; border:2px solid #aaa; border-left:0;">90</div>
<div style="padding:14px; border:2px solid #aaa; border-left:0;">78</div>
<div style="padding:14px; border:2px solid #aaa; border-left:0;">92</div>
<div style="padding:14px; border:2px solid #aaa; border-left:0;">88</div>

</div>

::

::div{class="normal-text-small" style="font-size:1.1rem; margin-top:24px;"}

- The first element is at index **`0`**
- The second element is at index **`1`**
- The fifth element is at index **`4`**

::

::div{class="definition-box" style="margin-top:18px !important; font-size:1.15rem !important;"}
**Key idea:** Array indexing starts at `0`.
::

---

# Accessing Array Elements

::div{class="grid grid-cols-2 gap-10 mt-6"}

::div{class="normal-text-small" style="font-size:1.1rem; line-height:1.45;"}

### Accessing by Index

Use the array name followed by an **index inside square brackets**.

```cpp
int scores[5] = {85, 90, 78, 92, 88};

cout << scores[0];   // 85
cout << scores[2];   // 78
cout << scores[4];   // 88
```

The index identifies which element of the array you want to access.

::

::div{class="normal-text-small" style="font-size:1.1rem; line-height:1.45;"}

### Valid Index Range

For an array containing `n` elements:

```text
First index:  0
Last index:   n - 1
```

For example:

```cpp
int scores[5];
```

has **5 elements**, but the valid indexes are:

```text
0, 1, 2, 3, 4
```

::

::

::div{class="definition-box" style="margin-top:22px !important; font-size:1.15rem !important; line-height:1.3 !important;"}
**Key idea:** An array with `n` elements has valid indexes from **`0` through `n - 1`**.
::

---

# Arrays in Memory

::div{class="normal-text-small" style="font-size:1.08rem; line-height:1.35;"}

Array elements are stored **contiguously** — one element immediately after another in memory.

```cpp
int numbers[5] = {10, 20, 30, 40, 50};
```

::

::div{style="display:flex; justify-content:center; margin-top:8px;"}

<div style="display:grid; grid-template-columns:70px repeat(5, 72px); text-align:center; font-size:0.95rem;">

<div style="padding:4px;"></div>
<div style="grid-column:2 / 7; padding:4px; font-weight:bold;">Contiguous Memory</div>

<div style="padding:10px 5px; font-weight:bold; text-align:left;">Value</div>
<div style="padding:10px; border:2px solid #aaa;">10</div>
<div style="padding:10px; border:2px solid #aaa; border-left:0;">20</div>
<div style="padding:10px; border:2px solid #aaa; border-left:0;">30</div>
<div style="padding:10px; border:2px solid #aaa; border-left:0;">40</div>
<div style="padding:10px; border:2px solid #aaa; border-left:0;">50</div>

<div style="padding:5px; font-weight:bold; text-align:left;">Index</div>
<div style="padding:5px;">0</div>
<div style="padding:5px;">1</div>
<div style="padding:5px;">2</div>
<div style="padding:5px;">3</div>
<div style="padding:5px;">4</div>

</div>

::

::div{class="grid grid-cols-2 gap-10" style="margin-top:2px;"}

::div{class="normal-text-small" style="font-size:1.02rem; line-height:1.35;"}

### Same Data Type

All elements have the **same data type**.

```cpp
int numbers[5];
```

Each element is an `int` and therefore occupies the same amount of memory.

::

::div{class="normal-text-small" style="font-size:1.02rem; line-height:1.35;"}

### Consecutive Addresses

If an `int` occupies **4 bytes**, consecutive elements are typically 4 bytes apart.

```text
numbers[0]  →  address 1000
numbers[1]  →  address 1004
numbers[2]  →  address 1008
```

::

::

::div{class="definition-box" style="margin-top:1px !important; font-size:1.05rem !important; line-height:1.25 !important;"}
**Key idea:** Contiguous storage allows an array element to be located directly from its **index**.
::

---

# Direct Access

::div{class="normal-text-small" style="font-size:1.08rem; line-height:1.4;"}

An array does not need to search through earlier elements to access a particular position.

```cpp
int scores[5] = {85, 90, 78, 92, 88};

cout << scores[3];   // 92
```

The expression `scores[3]` directly accesses the element at **index `3`**.

::

::div{style="display:flex; justify-content:center; margin-top:16px;"}

<div style="display:grid; grid-template-columns:80px repeat(5, 78px); text-align:center; font-size:1rem;">

<div style="padding:5px; font-weight:bold; text-align:left;">Index</div>
<div style="padding:5px;">0</div>
<div style="padding:5px;">1</div>
<div style="padding:5px;">2</div>
<div style="padding:5px;">3</div>
<div style="padding:5px;">4</div>

<div style="padding:12px 5px; font-weight:bold; text-align:left;">scores</div>
<div style="padding:12px; border:2px solid #aaa;">85</div>
<div style="padding:12px; border:2px solid #aaa; border-left:0;">90</div>
<div style="padding:12px; border:2px solid #aaa; border-left:0;">78</div>
<div style="padding:12px; border:2px solid #aaa; border-left:0;">92</div>
<div style="padding:12px; border:2px solid #aaa; border-left:0;">88</div>

<div></div>
<div></div>
<div></div>
<div></div>
<div style="padding-top:6px; font-size:1.25rem;">↑</div>
<div></div>

<div></div>
<div></div>
<div></div>
<div></div>
<div style="font-weight:bold;"><code>scores[3]</code></div>
<div></div>

</div>

::

::div{class="normal-text-small" style="font-size:1.05rem; line-height:1.35; margin-top:18px;"}

Because the location of each element can be determined from its **index**, the program can access any element directly.

::

::div{class="definition-box" style="margin-top:16px !important; font-size:1.1rem !important; line-height:1.25 !important;"}
**Key idea:** Accessing an array element by index takes **constant time — O(1)**.
::

---

# When Are Arrays Appropriate?

::div{class="grid grid-cols-2 gap-10 mt-5"}

::div{class="normal-text-small" style="font-size:1.08rem; line-height:1.5;"}

### Arrays Work Well When

- Values have the **same data type**
- The number of elements is **known**
- The collection has a **fixed size**
- Elements need frequent **indexed access**
- Contiguous storage is useful

### Examples

```cpp
int scores[30];

double temperatures[7];

char grades[5];
```

::

::div{class="normal-text-small" style="font-size:1.08rem; line-height:1.5;"}

### Consider the Limitations

Built-in arrays have a **fixed size**.

Adding or removing an element is not a built-in array operation.

If elements must be inserted or removed while maintaining their order, other elements may need to be **shifted manually**.

Collections that frequently grow or shrink are usually better handled with other data structures.

::

::

::div{class="definition-box" style="margin-top:18px !important; font-size:1.1rem !important;"}
**Key idea:** Arrays are well suited for **fixed-size collections** that require fast indexed access.
::

---

# Declaring and Initializing Arrays

::div{class="normal-text-small" style="font-size:1.12rem; line-height:1.45;"}

You can specify the array size explicitly:

```cpp
int numbers[5] = {10, 20, 30, 40, 50};
```

Or let the compiler determine the size from the initializer list:

```cpp
int numbers[] = {10, 20, 30, 40, 50};
```

Both create an array containing **5 integers**.

### General Form

```cpp
dataType arrayName[size] = {values};
```

::

::div{class="definition-box" style="margin-top:18px !important; font-size:1.3rem !important;"}
When an initializer list is provided, the compiler can determine the array size if the size is omitted.
::

---

# Accessing Elements with a Counter

::div{class="normal-text-small" style="font-size:1.1rem; line-height:1.4;"}

A counter-based `for` loop accesses elements using their **indexes**.

```cpp
#include <iostream>
using namespace std;

int main() {
    int numbers[] = {10, 20, 30, 40};

    for (int i = 0; i < 4; i++) {
        cout << numbers[i] << endl;
    }
    return 0;
}
```

### How It Works

```text
i = 0  →  numbers[0]  →  10
i = 1  →  numbers[1]  →  20
i = 2  →  numbers[2]  →  30
i = 3  →  numbers[3]  →  40
```

::

::div{class="definition-box" style="margin-top:16px !important; font-size:1.3rem !important;"}
Use a counter-based loop when you need the **index** of each array element.
::

---

# Range-Based `for` Loop

::div{class="normal-text-small" style="font-size:1.0rem; line-height:1.4;"}

A range-based `for` loop accesses each **element directly** without using an index.

```cpp
#include <iostream>
using namespace std;
int main() {
    int numbers[] = {10, 20, 30, 40};
    for (auto value : numbers) {
        cout << value << endl;
    }
    return 0;
}
```

In each iteration, the current array element is **copied** into `value`.

```cpp
for (auto value : numbers) {
    value = value * 2;
}
```

Changing `value` changes only the **copy**. The original array is unchanged.

::

::div{class="definition-box" style="margin-top:12px !important; font-size:1.1rem !important;"}
`auto value` receives a **copy** of each array element.
::

---

# Range-Based Loop with References

::div{class="normal-text-small" style="font-size:1.1rem; line-height:1.4;"}

Use a **reference** when you want to work with the original array element.

::div{class="grid grid-cols-2 gap-10 mt-4"}

::div

### Modify Elements

```cpp
int numbers[] = {10, 20, 30, 40};

for (auto& value : numbers) {
    value = value * 2;
}
```

`value` is a **reference (alias)** to the actual array element.

After the loop:

```text
20  40  60  80
```

::

::div

### Read-Only Access

```cpp
for (const auto& value : numbers) {
    cout << value << endl;
}
```

`const auto&` provides access to the original element but prevents modification through `value`.

::

::

::div{class="definition-box" style="margin-top:18px !important; font-size:1.1rem !important;"}
**`auto value`** → copy &nbsp;&nbsp; | &nbsp;&nbsp; **`auto& value`** → reference &nbsp;&nbsp; | &nbsp;&nbsp; **`const auto& value`** → read-only reference
::


---

# Traversing Arrays — Summary

::div{class="normal-text-small" style="font-size:0.95rem; line-height:1.2;"}

<table style="width:100%; margin-top:12px; border-collapse:collapse;">
<thead>
<tr>
<th style="text-align:left; padding:8px 10px;">Loop</th>
<th style="text-align:left; padding:8px 10px;">Example</th>
<th style="text-align:left; padding:8px 10px;">Variable Represents</th>
<th style="text-align:left; padding:8px 10px;">Can Modify Element?</th>
<th style="text-align:left; padding:8px 10px;">Use When</th>
</tr>
</thead>
<tbody>
<tr>
<td style="padding:10px;"><strong>Range-based<br>(Copy)</strong></td>
<td style="padding:10px;"><code>for (auto value : numbers)</code></td>
<td style="padding:10px;">Copy of element</td>
<td style="padding:10px;"><strong>No</strong></td>
<td style="padding:10px;">Reading small/simple values</td>
</tr>
<tr>
<td style="padding:10px;"><strong>Range-based<br>(Reference)</strong></td>
<td style="padding:10px;"><code>for (auto& value : numbers)</code></td>
<td style="padding:10px;">Reference to element</td>
<td style="padding:10px;"><strong>Yes</strong></td>
<td style="padding:10px;">Modifying elements</td>
</tr>
<tr>
<td style="padding:10px;"><strong>Range-based<br>(Const Reference)</strong></td>
<td style="padding:10px;"><code>for (const auto& value : numbers)</code></td>
<td style="padding:10px;">Read-only reference</td>
<td style="padding:10px;"><strong>No</strong></td>
<td style="padding:10px;">Reading without copying</td>
</tr>
<tr>
<td style="padding:10px;"><strong>Counter-based</strong></td>
<td style="padding:10px;"><code>for (std::size_t i = 0; i &lt; std::size(numbers); ++i)</code></td>
<td style="padding:10px;">Index</td>
<td style="padding:10px;"><strong>Yes</strong>, through <code>numbers[i]</code></td>
<td style="padding:10px;">The index is needed</td>
</tr>
</tbody>
</table>

::

::div{class="definition-box" style="margin-top:14px !important; font-size:1.2rem !important; line-height:1.25 !important;"}
**Choose based on your goal:** use an **index** when position matters, a **reference** to modify elements, and a **const reference** for read-only access without copying.
::



---

# Dynamic Arrays

::div{class="normal-text-small" style="font-size:1.12rem; line-height:1.45;"}

Sometimes the number of elements is **not known until the program runs**.

```cpp
int size;
cin >> size;

int* numbers = new int[size];
```

Here, the value of `size` is determined at **runtime**.

The program then dynamically allocates storage for that many integers.

::

::div{class="definition-box" style="margin-top:22px !important; font-size:1.3rem !important; line-height:1.3 !important;"}
**Dynamic allocation** allows the array size to be chosen at runtime. Once allocated, that particular raw array has a **fixed number of elements**.
::

---

# Fixed-Size vs. Dynamically Allocated Arrays

::div{class="grid grid-cols-2 gap-10 mt-6"}

::div{class="normal-text-small" style="font-size:1.08rem; line-height:1.4;"}

### Fixed-Size Array

```cpp
int numbers[5];
```

- Contains exactly **5 elements**
- Size is specified in the declaration
- Local array storage is managed automatically
- No `new[]` or `delete[]`

```text
Size: 5
```

::

::div{class="normal-text-small" style="font-size:1.08rem; line-height:1.4;"}

### Dynamically Allocated Array

```cpp
int size;
cin >> size;

int* numbers = new int[size];
```

- Number of elements determined at **runtime**
- Storage created using `new[]`
- Accessed through a pointer
- Storage must later be released

```text
Size: determined at runtime
```

::

::

::div{class="definition-box" style="margin-top:18px !important; font-size:1.3rem !important;"}
The important difference is **when the size is determined** and **how the storage is managed**.
::

---

# Understanding `new[]`

::div{class="normal-text-small" style="font-size:1.08rem; line-height:1.4;"}

Consider:

```cpp
int* numbers = new int[size];
```

::

::div{class="grid grid-cols-3 gap-6 mt-7"}

::div

### 1. Declare

```cpp
int* numbers
```

`numbers` is a **pointer to `int`**.

::

::div

### 2. Allocate

```cpp
new int[size]
```

Creates a contiguous block containing `size` integers.

::

::div

### 3. Point

```cpp
numbers = ...
```

The pointer returned by `new[]` is stored in `numbers`.

::

::

::div{class="definition-box" style="margin-top:26px !important; font-size:1.3rem !important; line-height:1.3 !important;"}
The **pointer** and the **dynamically allocated array** are two different things: the pointer provides access to the allocated elements.
::

---

# Dynamic Array in Memory

::div{class="normal-text-small" style="font-size:1.08rem; line-height:1.4;"}

Suppose:

```cpp
int* numbers = new int[5];
```

::

::div{class="grid grid-cols-2 gap-12 mt-6"}

::div

### Pointer

```text
numbers
   │
   │
   └──────────────►
```

`numbers` holds the address of the **first element**.

::

::div

### Allocated Elements

```text
Index    0     1     2     3     4

       [   ] [   ] [   ] [   ] [   ]
         ▲
         │
      numbers
```

The five integers are stored **contiguously**.

::

::

::div{class="definition-box" style="margin-top:20px !important; font-size:1.3rem !important;"}
The pointer refers to the first element, and normal array indexing can locate the remaining elements.
::

---

# Accessing Dynamic Array Elements

::div{class="normal-text-small" style="font-size:1.08rem; line-height:1.4;"}

Dynamic arrays use the **same indexing syntax** as built-in arrays.

::

::div{class="grid grid-cols-2 gap-10 mt-5"}

::div

### Assign Values

```cpp
for (int i = 0; i < size; ++i) {
    numbers[i] = i * 10;
}
```

For `size = 5`:

```text
Index    0    1    2    3    4
Value    0   10   20   30   40
```

::

::div

### Read Values

```cpp
for (int i = 0; i < size; ++i) {
    cout << numbers[i] << " ";
}
```

Output:

```text
0 10 20 30 40
```

::

::

::div{class="definition-box" style="margin-top:20px !important; font-size:1.3rem !important;"}
Dynamic allocation changes **how the storage is created**, not how the elements are indexed.
::

---

# Releasing Dynamic Memory

::div{class="normal-text-small" style="font-size:1.1rem; line-height:1.45;"}

Storage allocated with `new[]` must be released with `delete[]`.

::div{class="grid grid-cols-2 gap-12 mt-6"}

::div

### Allocate

```cpp
int* numbers = new int[size];
```

::

::div

### Release

```cpp
delete[] numbers;
numbers = nullptr;
```

::

::

::div{class="normal-text-small" style="font-size:1.08rem; margin-top:24px;"}

After `delete[]`:

- The dynamically allocated array no longer exists
- The old address must not be used
- Setting the pointer to `nullptr` makes it clear that it no longer refers to an array

::

::div{class="definition-box" style="margin-top:18px !important; font-size:1.3rem !important;"}
Memory obtained with `new[]` should be released with the matching `delete[]`.
::

---

# Memory Leaks

::div{class="normal-text-small" style="font-size:1.1rem; line-height:1.45;"}

What happens if dynamically allocated memory is never released?

```cpp
int* numbers = new int[1000];

// use the array

// delete[] numbers;   // forgotten
```

The allocated storage remains unavailable for reuse by the program while it continues running.

This is a **memory leak**.

Repeated memory leaks can cause a long-running program to consume increasing amounts of memory.

::

::div{class="definition-box" style="margin-top:22px !important; font-size:1.3rem !important;"}
A **memory leak** occurs when allocated memory is no longer needed but the program has lost or failed to release it.
::

---

# Dynamic Array — Complete Example

<style>
.slidev-code-group pre {
  max-height: 350px !important;
}
</style>

::code-group

```cpp [Code]
#include <iostream>
using namespace std;

int main() {
    int size;

    cout << "Enter number of elements: ";
    cin >> size;

    if (size <= 0) {
        cout << "Size must be positive." << endl;
        return 1;
    }

    int* numbers = new int[size];

    for (int i = 0; i < size; ++i) {
        numbers[i] = i * 10;
    }

    for (int i = 0; i < size; ++i) {
        cout << numbers[i] << " ";
    }

    delete[] numbers;
    numbers = nullptr;

    return 0;
}
```

```text [Example Output]
Enter number of elements: 5
0 10 20 30 40
```

::

::div{class="definition-box" style="margin-top:15px !important; font-size:1.3rem !important;"}
**Lifecycle:** determine size → allocate → access → release.
::

---

# Does a Dynamic Array Resize?

::div{class="normal-text-small" style="font-size:1.1rem; line-height:1.45;"}

No. Consider:

```cpp
int* numbers = new int[5];
```

That allocation contains exactly **5 elements**.

If the program later needs 10 elements, it cannot simply extend the existing raw array.

It must conceptually:

```text
1. Allocate a new array with 10 elements
              ↓
2. Copy the existing elements
              ↓
3. Release the old array
              ↓
4. Use the new array
```

::

::div{class="definition-box" style="margin-top:22px !important; font-size:1.1rem !important;"}
**Dynamic** means the size is chosen at runtime — not that a raw array automatically grows or shrinks.
::

---

# Raw Dynamic Array vs. `std::vector`

::div{class="normal-text-small" style="font-size:1rem; line-height:1.2;"}

<table style="width:100%; margin-top:16px; border-collapse:collapse;">
<thead>
<tr>
<th style="text-align:left; padding:8px 12px;">Feature</th>
<th style="text-align:left; padding:8px 12px;">Raw Dynamic Array</th>
<th style="text-align:left; padding:8px 12px;"><code>std::vector</code></th>
</tr>
</thead>
<tbody>
<tr>
<td style="padding:8px 12px;">Size chosen at runtime</td>
<td style="padding:8px 12px;">Yes</td>
<td style="padding:8px 12px;">Yes</td>
</tr>
<tr>
<td style="padding:8px 12px;">Contiguous elements</td>
<td style="padding:8px 12px;">Yes</td>
<td style="padding:8px 12px;">Yes</td>
</tr>
<tr>
<td style="padding:8px 12px;">Can grow automatically</td>
<td style="padding:8px 12px;">No</td>
<td style="padding:8px 12px;">Yes</td>
</tr>
<tr>
<td style="padding:8px 12px;">Tracks number of elements</td>
<td style="padding:8px 12px;">No</td>
<td style="padding:8px 12px;"><code>.size()</code></td>
</tr>
<tr>
<td style="padding:8px 12px;">Manual memory release</td>
<td style="padding:8px 12px;"><code>delete[]</code></td>
<td style="padding:8px 12px;">No</td>
</tr>
</tbody>
</table>

::

::div{class="definition-box" style="margin-top:16px !important; font-size:1.3rem !important;"}
Raw dynamic arrays are useful for learning **pointers and dynamic memory**. In modern C++, `std::vector` is generally preferred when a resizable array-like container is needed.
::

---

# Dynamic Arrays — Summary

::div{class="normal-text-small" style="font-size:1.12rem; line-height:1.5;"}

- The number of elements can be determined at **runtime**
- `new[]` dynamically allocates a **contiguous block** of elements
- A pointer refers to the **first element**
- Elements are accessed with normal array indexing: `numbers[i]`
- `delete[]` releases storage allocated with `new[]`
- Failing to release unused memory can cause a **memory leak**
- A raw dynamic array does **not automatically resize**
- `std::vector` is usually preferred when automatic resizing is required

::

::div{class="definition-box" style="margin-top:20px !important; font-size:1.3rem !important; line-height:1.3 !important;"}
**Key idea:** Dynamic arrays allow the size to be chosen at runtime, but raw dynamic memory requires explicit management by the programmer.
::


---

# From Dynamic Arrays to `std::vector`

::div{class="grid grid-cols-2 gap-10 mt-6"}

::div{class="normal-text-small" style="font-size:1.12rem !important; line-height:1.4 !important;"}

### Raw Dynamic Array

```cpp
int* numbers = new int[size];

// use the array

delete[] numbers;
```

It allows the size to be chosen at **runtime**, but:

- Memory must be managed manually
- The size must be tracked separately
- The array cannot automatically grow

::

::div{class="normal-text-small" style="font-size:1.12rem !important; line-height:1.4 !important;"}

### `std::vector`

```cpp
std::vector<int> numbers;
```

A vector provides:

- Automatic memory management
- Automatic size tracking
- Dynamic growth
- Familiar indexed access

```cpp
numbers[i]
```

::

::

::div{class="definition-box" style="margin-top:18px !important; font-size:1.3rem !important;"}
`std::vector` provides the flexibility of dynamic arrays with **much less manual memory management**.
::

---

# Introducing `std::vector`

::div{class="normal-text-small" style="font-size:1.12rem !important; line-height:1.45 !important;"}

`std::vector` is a **dynamic-size sequence container** provided by the C++ Standard Library.

```cpp
#include <vector>

std::vector<int> numbers;
```

A vector:

- Stores elements of the **same type**
- Stores its elements **contiguously**
- Can grow as elements are added
- Keeps track of its number of elements
- Manages its own storage automatically

::

::div{class="definition-box" style="margin-top:20px !important; font-size:1.3rem !important;"}
A useful mental model is to think of `std::vector` as a **managed dynamic array**.
::

---

# Declaring a `std::vector`

::div{class="normal-text-small" style="font-size:1.1rem !important; line-height:1.45 !important;"}

Include the `<vector>` header:

```cpp
#include <vector>
```

The general form is:

```cpp
std::vector<dataType> vectorName;
```

Examples:

```cpp
std::vector<int> scores;

std::vector<double> temperatures;

std::vector<char> grades;

std::vector<std::string> names;
```

::

::div{class="definition-box" style="margin-top:18px !important; font-size:1.3rem !important;"}
The type inside `< >` determines the type of elements stored in the vector.
::

---

# Creating and Initializing Vectors

::div{class="grid grid-cols-2 gap-10 mt-5"}

::div{class="normal-text-small"}

### Empty Vector

```cpp
std::vector<int> numbers;
```

Contains no elements:

```text
size = 0
```

Elements can be added later:

```cpp
numbers.push_back(10);
```

### Vector with a Size

```cpp
std::vector<int> numbers(5);
```

Creates five integers initialized to `0`.

::

::div{class="normal-text-small"}

### Vector with Values

```cpp
std::vector<int> numbers =
    {10, 20, 30, 40};
```

Creates four elements:

```text
Index    0    1    2    3
Value   10   20   30   40
```

The vector knows its size:

```cpp
cout << numbers.size();
```

Output:

```text
4
```

::

::

---

# Accessing Vector Elements

::div{class="normal-text-small" style="font-size:1.08rem !important; line-height:1.4 !important;"}

Vector elements use **zero-based indexing**, just like arrays.

```cpp
std::vector<int> numbers = {10, 20, 30, 40};
```

::

::div{style="display:flex; justify-content:center; margin-top:14px;"}

<div style="display:grid; grid-template-columns:80px repeat(4, 80px); text-align:center; font-size:1rem;">

<div style="padding:5px; font-weight:bold; text-align:left;">Index</div>
<div style="padding:5px;">0</div>
<div style="padding:5px;">1</div>
<div style="padding:5px;">2</div>
<div style="padding:5px;">3</div>

<div style="padding:11px 5px; font-weight:bold; text-align:left;">Value</div>
<div style="padding:11px; border:2px solid #aaa;">10</div>
<div style="padding:11px; border:2px solid #aaa; border-left:0;">20</div>
<div style="padding:11px; border:2px solid #aaa; border-left:0;">30</div>
<div style="padding:11px; border:2px solid #aaa; border-left:0;">40</div>

</div>

::

::div{class="normal-text-small" style="font-size:1.08rem; margin-top:18px;"}

```cpp
cout << numbers[0];   // 10
cout << numbers[2];   // 30
```

::

::div{class="definition-box" style="margin-top:14px !important; font-size:1.3rem !important;"}
Like built-in arrays, vector indexes range from **`0` to `size() - 1`**.
::

---

# `[]` vs. `at()`

::div{class="grid grid-cols-2 gap-10 mt-6"}

::div{class="normal-text-small"}

### Using `[]`

```cpp
std::vector<int> numbers =
    {10, 20, 30, 40};

cout << numbers[2];
```

Output:

```text
30
```

`[]` provides indexed access but performs **no bounds checking**.

::

::div{class="normal-text-small"}

### Using `at()`

```cpp
std::vector<int> numbers =
    {10, 20, 30, 40};

cout << numbers.at(2);
```

Output:

```text
30
```

`at()` performs **bounds checking**.

::

::

::div{class="definition-box" style="margin-top:20px !important; font-size:1.3rem !important;"}
Both access an element by position, but `at()` verifies that the requested position is valid.
::

---

# What If the Index Is Invalid?

::div{class="grid grid-cols-2 gap-10 mt-6"}

::div{class="normal-text-small"}

### `[]` — Unchecked

```cpp
std::vector<int> values =
    {1, 2, 3, 4, 5};

cout << values[10];
```

Index `10` does not exist.

Accessing outside the vector using `[]` results in **undefined behavior**.

::

::div{class="normal-text-small"}

### `at()` — Bounds Checked

```cpp
std::vector<int> values =
    {1, 2, 3, 4, 5};

cout << values.at(10);
```

The invalid position is detected.

`at()` throws:

```text
std::out_of_range
```

::

::

::div{class="definition-box" style="margin-top:20px !important; font-size:1.3rem !important;"}
`at()` is useful when you want invalid indexes to be **detected rather than silently accessing outside the vector**.
::

---

# Adding Elements with `push_back()`

::div{class="grid grid-cols-2 gap-10 mt-6"}

::div{class="normal-text-small" style="font-size:1.1rem !important; line-height:1.4 !important;"}

### Adding Elements

`push_back()` adds an element to the **end** of a vector.

```cpp
std::vector<int> numbers = {10, 20, 30};

numbers.push_back(40);
numbers.push_back(50);
```

The vector updates its size automatically:

```cpp
cout << numbers.size();   // 5
```

::

::div{class="normal-text-small" style="font-size:1.1rem !important; line-height:1.4 !important;"}

### Before

```text
10    20    30
```

### After

```text
10    20    30    40    50
```

Two elements were added to the **end** of the vector.

::

::

::div{class="definition-box" style="margin-top:18px !important; font-size:1.3rem !important;"}
With `std::vector`, the programmer does not manually allocate a larger array when adding elements.
::

---

# Removing the Last Element

::div{class="normal-text-small" style="font-size:1.12rem !important; line-height:1.45 !important;"}

`pop_back()` removes the **last element**.

```cpp
std::vector<int> numbers =
    {10, 20, 30, 40};

numbers.pop_back();
```

Before:

```text
10    20    30    40
```

After:

```text
10    20    30
```

The vector updates its size:

```cpp
cout << numbers.size();   // 3
```

::

::div{class="definition-box" style="margin-top:18px !important; font-size:1.3rem !important;"}
`pop_back()` removes the last element but does **not return the removed value**.
::

---

# Common `std::vector` Operations

::div{class="normal-text-small-compact"}

Assume:

```cpp
std::vector<int> values = {10, 20, 30};
```

::

::div{class="grid grid-cols-2 gap-10 mt-4"}

::div{class="normal-text-small"}

### Add an Element

```cpp
values.push_back(40);
```

### Remove Last Element

```cpp
values.pop_back();
```

### Number of Elements

```cpp
values.size();
```

::

::div{class="normal-text-small"}

### Check Whether Empty

```cpp
values.empty();
```

### Remove All Elements

```cpp
values.clear();
```

### Bounds-Checked Access

```cpp
values.at(1);
```

::

::

---

# Traversing a Vector

::div{class="grid grid-cols-2 gap-10 mt-6"}

::div{class="normal-text-small"}

### Counter-Based Loop

```cpp
for (std::size_t i = 0;
     i < numbers.size(); ++i) {

    cout << numbers[i] << '\n';
}
```

Use this when you need the **index**.

::

::div{class="normal-text-small"}

### Range-Based Loop

```cpp
for (const auto& value : numbers) {
    cout << value << '\n';
}
```

Use this when you only need each **element**.

::

::

::div{class="definition-box" style="margin-top:20px !important; font-size:1.08rem !important;"}
Vectors support the same **index-based and range-based loops** used with arrays.
::

---

# Inside a `std::vector`

::div{class="grid grid-cols-2 gap-10 mt-5"}

::div{class="normal-text-small" style="font-size:1.05rem !important; line-height:1.35 !important;"}

### What Does a Vector Manage?

A vector manages a **contiguous block of elements**.

Conceptually, it keeps track of:

- Where its elements are stored
- **Size** — number of elements currently stored
- **Capacity** — available element storage before reallocation is required

```cpp
std::vector<int> numbers = {10, 20, 30};
```

::

::div{class="normal-text-small" style="font-size:1.05rem !important;"}

### Element Storage

::div{style="display:flex; justify-content:center; margin-top:12px;"}

<div style="display:grid; grid-template-columns:65px repeat(3, 72px); text-align:center; font-size:0.95rem;">
<div style="padding:5px; font-weight:bold;">Index</div>
<div style="padding:5px;">0</div>
<div style="padding:5px;">1</div>
<div style="padding:5px;">2</div>
<div style="padding:12px 5px; font-weight:bold;">Value</div>
<div style="padding:12px; border:2px solid #aaa;">10</div>
<div style="padding:12px; border:2px solid #aaa; border-left:0;">20</div>
<div style="padding:12px; border:2px solid #aaa; border-left:0;">30</div>
</div>

::

::div{style="text-align:center; margin-top:16px;"}

**`numbers` manages this storage**

`size = 3`

::

::

::

::div{class="definition-box" style="margin-top:14px !important; font-size:1.3rem !important; line-height:1.25 !important;"}
The exact internal representation is implementation-dependent. C++ guarantees that vector elements are stored **contiguously**.
::

---

# `size()` vs. `capacity()`

::div{class="normal-text-small" style="font-size:1.08rem !important; line-height:1.35 !important;"}

A vector can have more storage available than the number of elements currently stored.

::

::div{style="display:flex; justify-content:center; margin-top:14px;"}

<div style="display:grid; grid-template-columns:80px repeat(5, 80px); text-align:center; font-size:1rem;">

<div style="padding:5px; font-weight:bold;">Position</div>
<div style="padding:5px;">0</div>
<div style="padding:5px;">1</div>
<div style="padding:5px;">2</div>
<div style="padding:5px;">3</div>
<div style="padding:5px;">4</div>

<div style="padding:12px 5px; font-weight:bold;">Storage</div>
<div style="padding:12px; border:2px solid #aaa;">10</div>
<div style="padding:12px; border:2px solid #aaa; border-left:0;">20</div>
<div style="padding:12px; border:2px solid #aaa; border-left:0;">30</div>
<div style="padding:12px; border:2px dashed #777; border-left:0;">unused</div>
<div style="padding:12px; border:2px dashed #777; border-left:0;">unused</div>

</div>

::

::div{class="grid grid-cols-2 gap-10 mt-6"}

::div{class="normal-text-small" style="font-size:1.05rem !important;"}

### `size()`

Number of elements that **currently exist**.

```cpp
numbers.size();
```

```text
size = 3
```

Only `10`, `20`, and `30` are elements of the vector.

::

::div{class="normal-text-small" style="font-size:1.05rem !important;"}

### `capacity()`

Number of elements that can fit in the current storage **before reallocation is required**.

```cpp
numbers.capacity();
```

```text
capacity = 5
```

There is storage available for two more elements.

::

::

::div{class="definition-box" style="margin-top:12px !important; font-size:1.1rem !important;"}
**Size = elements that exist.** &nbsp;&nbsp;&nbsp; **Capacity = available element storage before reallocation.**
::

---

# Why Does a Vector Have Extra Capacity?

::div{class="normal-text-small" style="font-size:1.05rem !important; line-height:1.35 !important;"}

A vector may allocate **more storage than it currently needs**.

::

::div{class="grid grid-cols-2 gap-10 mt-5"}

::div{class="normal-text-small"}

### Before `push_back()`

::div{style="display:grid; grid-template-columns:repeat(5, 62px); text-align:center; margin-top:14px;"}
<div style="padding:12px; border:2px solid #aaa;">10</div>
<div style="padding:12px; border:2px solid #aaa; border-left:0;">20</div>
<div style="padding:12px; border:2px solid #aaa; border-left:0;">30</div>
<div style="padding:12px; border:2px dashed #777; border-left:0;">&nbsp;</div>
<div style="padding:12px; border:2px dashed #777; border-left:0;">&nbsp;</div>
::

::div{style="display:grid; grid-template-columns:186px 124px; text-align:center; font-size:0.9rem; margin-top:5px;"}
<div>3 elements</div>
<div>unused storage</div>
::

```text
size     = 3
capacity = 5
```

::

::div{class="normal-text-small"}

### After `push_back(40)`

```cpp
numbers.push_back(40);
```

::div{style="display:grid; grid-template-columns:repeat(5, 62px); text-align:center; margin-top:10px;"}
<div style="padding:12px; border:2px solid #aaa;">10</div>
<div style="padding:12px; border:2px solid #aaa; border-left:0;">20</div>
<div style="padding:12px; border:2px solid #aaa; border-left:0;">30</div>
<div style="padding:12px; border:2px solid #aaa; border-left:0;">40</div>
<div style="padding:12px; border:2px dashed #777; border-left:0;">&nbsp;</div>
::

The new element uses the **existing available storage**.

```text
size     = 4
capacity = 5
```

::

::

::div{class="definition-box" style="margin-top:12px !important; font-size:1.3rem !important;"}
Extra capacity allows a vector to add elements **without requiring a new memory allocation every time**.
::

---

# What Happens When Capacity Is Full?

::div{class="normal-text-small-compact"}

Suppose the vector has **no unused capacity**:

```text
size = 3
capacity = 3
```

::div{style="display:flex; justify-content:center; margin-top:8px;"}
::div{style="display:grid; grid-template-columns:repeat(3, 72px); text-align:center;"}
<div style="padding:12px; border:2px solid #aaa;">10</div>
<div style="padding:12px; border:2px solid #aaa; border-left:0;">20</div>
<div style="padding:12px; border:2px solid #aaa; border-left:0;">30</div>
::
::

Now another element is added:

```cpp
numbers.push_back(40);
```

::

::div{class="grid grid-cols-2 gap-10 mt-3"}

::div{class="normal-text-small" style="font-size:1rem !important;"}

### What the Vector Does

The vector may need to:

1. Allocate a **larger contiguous block**
2. Move or copy the existing elements
3. Add the new element
4. Release the old storage

This process is called **reallocation**.

::

::div{class="normal-text-small" style="font-size:1rem !important;"}

### After Reallocation

::div{style="display:grid; grid-template-columns:repeat(5, 58px); text-align:center; margin-top:12px;"}
<div style="padding:11px; border:2px solid #aaa;">10</div>
<div style="padding:11px; border:2px solid #aaa; border-left:0;">20</div>
<div style="padding:11px; border:2px solid #aaa; border-left:0;">30</div>
<div style="padding:11px; border:2px solid #aaa; border-left:0;">40</div>
<div style="padding:11px; border:2px dashed #777; border-left:0;">&nbsp;</div>
::

::div{style="text-align:center; margin-top:8px; font-size:0.95rem;"}
The elements now occupy a **new contiguous block**.
::

::

::

::div{class="definition-box" style="margin-top:10px !important; font-size:1.02rem !important;"}
Vector growth and reallocation are handled **automatically**. The new capacity is larger, but the exact growth amount is implementation-dependent.
::

---

# Vector Memory Management

::div{class="grid grid-cols-2 gap-10 mt-6"}

::div{class="normal-text-small"}

### Raw Dynamic Array

```cpp
int* numbers = new int[size];

// use numbers

delete[] numbers;
```

The programmer must explicitly release the dynamically allocated storage.

::

::div{class="normal-text-small"}

### `std::vector`

```cpp
{
    std::vector<int> numbers(100);

    // use numbers
}
```

When the vector is destroyed, its managed element storage is released automatically.

No manual `delete[]` is required.

::

::

::div{class="definition-box" style="margin-top:20px !important; font-size:1.08rem !important;"}
`std::vector` manages the lifetime of its element storage automatically.
::

---

# Raw Dynamic Array vs. `std::vector`

::div{class="normal-text-small" style="font-size:1rem !important;"}

<table style="width:100%; margin-top:12px; font-size:1.02rem; line-height:1.15; border-collapse:collapse;">
<thead>
<tr>
<th style="text-align:left; padding:8px 10px;">Feature</th>
<th style="text-align:left; padding:8px 10px;">Raw Dynamic Array</th>
<th style="text-align:left; padding:8px 10px;"><code>std::vector</code></th>
</tr>
</thead>
<tbody>
<tr>
<td style="padding:8px 10px;">Runtime size</td>
<td style="padding:8px 10px;">Yes</td>
<td style="padding:8px 10px;">Yes</td>
</tr>
<tr>
<td style="padding:8px 10px;">Contiguous elements</td>
<td style="padding:8px 10px;">Yes</td>
<td style="padding:8px 10px;">Yes</td>
</tr>
<tr>
<td style="padding:8px 10px;">Automatic growth</td>
<td style="padding:8px 10px;">No</td>
<td style="padding:8px 10px;">Yes</td>
</tr>
<tr>
<td style="padding:8px 10px;">Tracks its size</td>
<td style="padding:8px 10px;">No</td>
<td style="padding:8px 10px;"><code>size()</code></td>
</tr>
<tr>
<td style="padding:8px 10px;">Memory management</td>
<td style="padding:8px 10px;">Manual</td>
<td style="padding:8px 10px;">Automatic</td>
</tr>
<tr>
<td style="padding:8px 10px;">Release storage</td>
<td style="padding:8px 10px;"><code>delete[]</code></td>
<td style="padding:8px 10px;">Automatic</td>
</tr>
<tr>
<td style="padding:8px 10px;">Bounds-checked access</td>
<td style="padding:8px 10px;">No built-in option</td>
<td style="padding:8px 10px;"><code>at()</code></td>
</tr>
</tbody>
</table>

::

::div{class="definition-box" style="margin-top:14px !important; font-size:1.3rem !important;"}
For most dynamically sized sequences in modern C++, **`std::vector` is preferred over manually managing a raw dynamic array**.
::

---

# Arrays and Vectors — Big Picture

::div{class="normal-text-small" style="font-size:0.98rem !important;"}

<table style="width:100%; margin-top:14px; font-size:1rem; line-height:1.15; border-collapse:collapse;">
<thead>
<tr>
<th style="text-align:left; padding:8px 10px;">Type</th>
<th style="text-align:left; padding:8px 10px;">Example</th>
<th style="text-align:left; padding:8px 10px;">Size</th>
<th style="text-align:left; padding:8px 10px;">Can Grow?</th>
<th style="text-align:left; padding:8px 10px;">Storage Management</th>
</tr>
</thead>
<tbody>
<tr>
<td style="padding:8px 10px;">Built-in Array</td>
<td style="padding:8px 10px;"><code>int a[5];</code></td>
<td style="padding:8px 10px;">Fixed</td>
<td style="padding:8px 10px;">No</td>
<td style="padding:8px 10px;">Automatic for a local array</td>
</tr>
<tr>
<td style="padding:8px 10px;">Raw Dynamic Array</td>
<td style="padding:8px 10px;"><code>int* a = new int[n];</code></td>
<td style="padding:8px 10px;">Chosen at runtime</td>
<td style="padding:8px 10px;">Not automatically</td>
<td style="padding:8px 10px;">Manual</td>
</tr>
<tr>
<td style="padding:8px 10px;"><code>std::vector</code></td>
<td style="padding:8px 10px;"><code>std::vector&lt;int&gt; a;</code></td>
<td style="padding:8px 10px;">Dynamic</td>
<td style="padding:8px 10px;">Yes</td>
<td style="padding:8px 10px;">Automatic</td>
</tr>
</tbody>
</table>

::

::div{class="definition-box" style="margin-top:18px !important; font-size:1.08rem !important;"}
The progression is: **fixed-size array → runtime-sized raw array → automatically managed and resizable `std::vector`**.
::

---

# `std::vector` — Summary

::div{class="normal-text-small" style="font-size:1.1rem !important; line-height:1.45 !important;"}

- `std::vector` is a **dynamic-size sequence container**
- It stores elements of the **same type**
- Elements are stored **contiguously**
- `size()` reports the number of elements
- `capacity()` reports the currently available element storage
- `push_back()` adds an element to the end
- `pop_back()` removes the last element
- `[]` provides unchecked indexed access
- `at()` provides bounds-checked indexed access
- The vector manages its storage and growth automatically
- No manual `new[]` or `delete[]` is required

::

::div{class="definition-box" style="margin-top:16px !important; font-size:1.1rem !important; line-height:1.3 !important;"}
**Key idea:** `std::vector` provides familiar array-style access while adding **dynamic growth, size tracking, and automatic memory management**.
::

---

# From 1D to 2D Arrays

::div{class="grid grid-cols-2 gap-10 mt-6"}

::div{class="normal-text-small" style="font-size:1.08rem !important; line-height:1.4 !important;"}

### One-Dimensional Array

A 1D array works well for a **single sequence of values**.

```cpp
int scores[4] = {80, 85, 70, 90};
```

Each element requires one index:

```cpp
scores[0]
scores[1]
scores[2]
scores[3]
```

::

::div{class="normal-text-small" style="font-size:1.08rem !important; line-height:1.4 !important;"}

### What About Rows and Columns?

Some data naturally forms a table.

| Student | Math | English | CS |
|---|---:|---:|---:|
| John | 80 | 75 | 90 |
| Mary | 85 | 92 | 88 |
| Alex | 70 | 80 | 85 |

A value now needs both a **row** and a **column**.

::

::

::div{class="definition-box" style="margin-top:16px !important; font-size:1.08rem !important;"}
A **two-dimensional array** organizes elements using **rows and columns**.
::

---

# Structure of a 2D Array

::div{class="normal-text-small" style="font-size:1.07rem !important; line-height:1.4 !important;"}

Consider:

```cpp
int matrix[3][4];
```

This creates **3 rows**, with **4 elements in each row**.

::

::div{style="display:flex; justify-content:center; margin-top:14px;"}

<table style="border-collapse:collapse; text-align:center; font-size:0.95rem;">
<tr>
<th style="padding:8px 14px;"></th>
<th style="padding:8px 18px;">Col 0</th>
<th style="padding:8px 18px;">Col 1</th>
<th style="padding:8px 18px;">Col 2</th>
<th style="padding:8px 18px;">Col 3</th>
</tr>
<tr>
<th style="padding:12px;">Row 0</th>
<td style="padding:12px 18px; border:1px solid #777;"><code>[0][0]</code></td>
<td style="padding:12px 18px; border:1px solid #777;"><code>[0][1]</code></td>
<td style="padding:12px 18px; border:1px solid #777;"><code>[0][2]</code></td>
<td style="padding:12px 18px; border:1px solid #777;"><code>[0][3]</code></td>
</tr>
<tr>
<th style="padding:12px;">Row 1</th>
<td style="padding:12px 18px; border:1px solid #777;"><code>[1][0]</code></td>
<td style="padding:12px 18px; border:1px solid #777;"><code>[1][1]</code></td>
<td style="padding:12px 18px; border:1px solid #777;"><code>[1][2]</code></td>
<td style="padding:12px 18px; border:1px solid #777;"><code>[1][3]</code></td>
</tr>
<tr>
<th style="padding:12px;">Row 2</th>
<td style="padding:12px 18px; border:1px solid #777;"><code>[2][0]</code></td>
<td style="padding:12px 18px; border:1px solid #777;"><code>[2][1]</code></td>
<td style="padding:12px 18px; border:1px solid #777;"><code>[2][2]</code></td>
<td style="padding:12px 18px; border:1px solid #777;"><code>[2][3]</code></td>
</tr>
</table>

::

::div{class="definition-box" style="margin-top:14px !important; font-size:1.05rem !important;"}
`matrix[3][4]` contains **12 elements**: 3 rows × 4 columns.
::

---

# Declaring a 2D Array

::div{class="grid grid-cols-2 gap-10 mt-5"}

::div{class="normal-text-small-compact"}

### General Form

```cpp
dataType name[rows][columns];
```

Examples:

```cpp
int scores[3][4];
double temps[7][24];
char board[8][8];
```

::

::div{class="normal-text-small-compact"}

### Example

```cpp
int scores[3][4];
```

Creates **3 rows × 4 columns = 12 elements**.

```text
Rows:     0, 1, 2
Columns:  0, 1, 2, 3
```

Access an element:

```cpp
scores[row][column]
```

::

::

::div{class="definition-box" style="margin-top:10px !important; font-size:1.3rem !important;"}
The first dimension specifies the **rows**; the second specifies the **columns**. Indexes start at `0`.
::

---

# Initializing a 2D Array

::div{class="grid grid-cols-2 gap-10 mt-5"}

::div{class="normal-text-small" style="font-size:1.05rem !important; line-height:1.35 !important;"}

### Row-by-Row Initialization

```cpp
int grid[2][3] = {
    {1, 2, 3},
    {4, 5, 6}
};
```

Each inner set of braces represents a row.

| | Col 0 | Col 1 | Col 2 |
|---|---:|---:|---:|
| **Row 0** | 1 | 2 | 3 |
| **Row 1** | 4 | 5 | 6 |

::

::div{class="normal-text-small" style="font-size:1.05rem !important; line-height:1.35 !important;"}

### Partial Initialization

```cpp
int grid[2][3] = {
    {1, 2, 3},
    {4}
};
```

Elements without an explicit initializer are initialized to `0`.

| | Col 0 | Col 1 | Col 2 |
|---|---:|---:|---:|
| **Row 0** | 1 | 2 | 3 |
| **Row 1** | 4 | 0 | 0 |

::

::

::div{class="definition-box" style="margin-top:12px !important; font-size:1.3rem !important;"}
Nested braces clearly show which values belong to each **row**.
::

---

# Accessing 2D Array Elements

::div{class="grid grid-cols-2 gap-10 mt-5"}

::div{class="normal-text-small" style="font-size:1.06rem !important; line-height:1.4 !important;"}

### Reading Elements

```cpp
int grid[2][3] = {
    {10, 20, 30},
    {40, 50, 60}
};
```

Use:

```cpp
grid[row][column]
```

Examples:

```cpp
cout << grid[0][0];  // 10
cout << grid[0][2];  // 30
cout << grid[1][1];  // 50
```

::

::div{class="normal-text-small" style="font-size:1.06rem !important; line-height:1.4 !important;"}

### Modifying Elements

```cpp
grid[0][1] = 25;
grid[1][2] = 100;
```

The array becomes:

| | Col 0 | Col 1 | Col 2 |
|---|---:|---:|---:|
| **Row 0** | 10 | **25** | 30 |
| **Row 1** | 40 | 50 | **100** |

::

::

::div{class="definition-box" style="margin-top:14px !important; font-size:1.3rem !important;"}
Think **`grid[row][column]`** — choose the row first, then the element within that row.
::

---

# A 2D Array Is an Array of Arrays

::div{class="grid grid-cols-2 gap-10 mt-5"}

::div{class="normal-text-small" style="font-size:1.07rem !important; line-height:1.4 !important;"}

Consider:

```cpp
int grid[2][3] = {
    {10, 20, 30},
    {40, 50, 60}
};
```

`grid` contains **2 elements**.

But each element is itself an array containing **3 integers**.

```text
grid
 ├─ row 0 → 10  20  30
 └─ row 1 → 40  50  60
```

::

::div{class="normal-text-small" style="font-size:1.07rem !important; line-height:1.4 !important;"}

### Reading the Expression

```cpp
grid[1]
```

selects the second **row**.

Then:

```cpp
grid[1][2]
```

selects element `2` from that row.

Result:

```text
60
```

::

::

::div{class="definition-box" style="margin-top:14px !important; font-size:1.3rem !important;"}
A built-in 2D array is an **array whose elements are themselves arrays**.
::

---

# Traversing a 2D Array

::div{class="grid grid-cols-2 gap-10 mt-5"}

::div{class="normal-text-small" style="font-size:1.04rem !important;"}

### Nested Loops

```cpp
for (int row = 0; row < 2; ++row) {

    for (int col = 0; col < 3; ++col) {
        cout << grid[row][col] << " ";
    }

    cout << '\n';
}
```

Output:

```text
10 20 30
40 50 60
```

::

::div{class="normal-text-small" style="font-size:1.04rem !important; line-height:1.4 !important;"}

### Traversal Order

For `row = 0`:

```text
[0][0] → [0][1] → [0][2]
```

Then for `row = 1`:

```text
[1][0] → [1][1] → [1][2]
```

The inner loop finishes an entire row before the outer loop moves to the next row.

::

::

::div{class="definition-box" style="margin-top:12px !important; font-size:1.3rem !important;"}
The **outer loop** selects a row; the **inner loop** visits the columns within that row.
::

---

# How Is a 2D Array Stored?

::div{class="normal-text-small" style="font-size:1.05rem !important; line-height:1.35 !important;"}

Consider:

```cpp
int grid[2][3] = {
    {10, 20, 30},
    {40, 50, 60}
};
```

Although we visualize rows and columns, the elements occupy **one contiguous region of memory**.

::

::div{style="display:flex; justify-content:center; margin-top:14px;"}

<div style="display:grid; grid-template-columns:repeat(6, 82px); text-align:center; font-size:0.9rem;">

<div style="padding:5px;"><code>[0][0]</code></div>
<div style="padding:5px;"><code>[0][1]</code></div>
<div style="padding:5px;"><code>[0][2]</code></div>
<div style="padding:5px;"><code>[1][0]</code></div>
<div style="padding:5px;"><code>[1][1]</code></div>
<div style="padding:5px;"><code>[1][2]</code></div>

<div style="padding:13px; border:2px solid #aaa;">10</div>
<div style="padding:13px; border:2px solid #aaa; border-left:0;">20</div>
<div style="padding:13px; border:2px solid #aaa; border-left:0;">30</div>
<div style="padding:13px; border:2px solid #aaa; border-left:0;">40</div>
<div style="padding:13px; border:2px solid #aaa; border-left:0;">50</div>
<div style="padding:13px; border:2px solid #aaa; border-left:0;">60</div>

</div>

::

::div{style="display:flex; justify-content:center; margin-top:7px;"}
::div{style="display:grid; grid-template-columns:246px 246px; text-align:center; font-size:0.9rem;"}
<div>Row 0</div>
<div>Row 1</div>
::
::

::div{class="definition-box" style="margin-top:14px !important; font-size:1.3rem !important;"}
C++ stores built-in multidimensional arrays in **row-major order**: one complete row is followed by the next row.
::

---

# Row-Major Order and Memory Addresses

::div{class="grid grid-cols-2 gap-10 mt-5"}

::div{class="normal-text-small" style="font-size:1.03rem !important; line-height:1.35 !important;"}

Suppose:

```cpp
int grid[2][3];
```

and, **for this example**:

```text
Base address = 0x100
sizeof(int)  = 4 bytes
```

Then:

```text
grid[0][0] → 0x100
grid[0][1] → 0x104
grid[0][2] → 0x108
```

::

::div{class="normal-text-small" style="font-size:1.03rem !important; line-height:1.35 !important;"}

After the first row comes the second:

```text
grid[1][0] → 0x10C
grid[1][1] → 0x110
grid[1][2] → 0x114
```

Notice:

```text
[0][2] → 0x108
[1][0] → 0x10C
```

The next row begins immediately after the previous row.

::

::

::div{class="definition-box" style="margin-top:14px !important; font-size:1.3rem !important;"}
The addresses above assume a particular example where `sizeof(int) == 4`; the C++ language does not require `int` to be exactly 4 bytes.
::

---

# How Does C++ Locate an Element?

::div{class="grid grid-cols-2 gap-10 mt-5"}

::div{class="normal-text-small-compact"}

### Example

```cpp
int matrix[3][4];
```

Locate:

```cpp
matrix[1][2]
```

Each row contains **4 elements**.

Skip row `0`:

```text
1 × 4 = 4 elements
```

Move to column `2`:

```text
4 + 2 = 6 elements
```

::

::div{class="normal-text-small-compact"}

### Convert to a Memory Offset

The element is **6 positions** from the beginning.

If, for this example:

```text
sizeof(int) = 4 bytes
```

then:

```text
6 × 4 = 24 bytes
```

Therefore, `matrix[1][2]` begins:

```text
24 bytes from the start
```

::

::

::div{class="definition-box" style="margin-top:10px !important; font-size:1.05rem !important;"}
**Element offset:** `(row × columns) + column` → `(1 × 4) + 2 = 6`
::

---

# Address Calculation

::div{class="grid grid-cols-2 gap-10 mt-5"}

::div{class="normal-text-small-compact"}

### 1. Element Offset

For:

```cpp
matrix[row][column]
```

calculate how many elements come before it:

```text
(row × columns) + column
```

Example:

```text
matrix[1][2]

(1 × 4) + 2 = 6 elements
```

::

::div{class="normal-text-small-compact"}

### 2. Memory Address

Convert the element offset to bytes:

```text
element offset
    × sizeof(element_type)
```

Then:

```text
address =
    base address + byte offset
```

If each element is 4 bytes:

```text
6 × 4 = 24 bytes
```

::

::

::div{class="definition-box" style="margin-top:10px !important; font-size:1.05rem !important;"}
The **number of columns** determines how many elements must be skipped to move from one row to the next.
::

---

# More Than Two Dimensions

::div{class="grid grid-cols-3 gap-6 mt-6"}

::div{class="normal-text-small" style="font-size:1.02rem !important;"}

### 1D Array

A single sequence:

```cpp
int students[10];
```

Access:

```cpp
students[i]
```

**1 index**

::

::div{class="normal-text-small" style="font-size:1.02rem !important;"}

### 2D Array

Rows and columns:

```cpp
int classroom[5][6];
```

Access:

```cpp
classroom[row][col]
```

**2 indexes**

::

::div{class="normal-text-small" style="font-size:1.02rem !important;"}

### 3D Array

Multiple layers:

```cpp
int building[3][5][6];
```

Access:

```cpp
building[layer][row][col]
```

**3 indexes**

::

::

::div{class="definition-box" style="margin-top:18px !important; font-size:1.3rem !important;"}
Each additional dimension adds another **index** needed to select an element.
::

---

# Where Are Multidimensional Arrays Useful?

::div{class="normal-text-small" style="font-size:1.03rem !important;"}

<table style="width:100%; border-collapse:collapse; margin-top:14px;">
<tr style="border-bottom:1px solid #666;">
<th style="padding:9px; text-align:left;">Application</th>
<th style="padding:9px; text-align:left;">Example</th>
</tr>
<tr style="border-bottom:1px solid #444;">
<td style="padding:9px;"><strong>Games</strong></td>
<td style="padding:9px;">Chessboards, tic-tac-toe boards, maps, and mazes</td>
</tr>
<tr style="border-bottom:1px solid #444;">
<td style="padding:9px;"><strong>Images</strong></td>
<td style="padding:9px;">Pixels organized into rows and columns</td>
</tr>
<tr style="border-bottom:1px solid #444;">
<td style="padding:9px;"><strong>Scientific Data</strong></td>
<td style="padding:9px;">Measurements organized across multiple dimensions</td>
</tr>
<tr style="border-bottom:1px solid #444;">
<td style="padding:9px;"><strong>Simulations</strong></td>
<td style="padding:9px;">Values associated with positions in 2D or 3D space</td>
</tr>
<tr>
<td style="padding:9px;"><strong>Matrices</strong></td>
<td style="padding:9px;">Rows and columns used in mathematical computations</td>
</tr>
</table>

::

::div{class="definition-box" style="margin-top:14px !important; font-size:1.3rem !important;"}
Multidimensional arrays are useful when the data naturally has a **fixed multidimensional structure**.
::

---

# Limitations of Built-In Multidimensional Arrays

::div{class="grid grid-cols-2 gap-10 mt-6"}

::div{class="normal-text-small" style="font-size:1.05rem !important; line-height:1.4 !important;"}

### Good Fit

Built-in multidimensional arrays work well when:

- Dimensions are fixed
- The structure is rectangular
- Every row has the same number of columns
- Direct indexed access is useful

For example:

```cpp
char chessboard[8][8];
```

::

::div{class="normal-text-small" style="font-size:1.05rem !important; line-height:1.4 !important;"}

### Less Flexible

They are less convenient when:

- Dimensions need to change
- Rows need different lengths
- Data grows or shrinks
- The required dimensions are determined at runtime

Built-in arrays do **not automatically resize**.

::

::

::div{class="definition-box" style="margin-top:16px !important; font-size:1.3rem !important;"}
Built-in multidimensional arrays are a good choice when the data has a **fixed, rectangular shape**.
::

---

# Multidimensional Arrays — Summary

::div{class="grid grid-cols-2 gap-10 mt-6"}

::div{class="normal-text-small" style="font-size:1.07rem !important; line-height:1.45 !important;"}

### Programming View

```cpp
int grid[2][3];
```

- A 2D array is an **array of arrays**
- First index selects the row
- Second index selects the column
- Nested loops traverse rows and columns
- More dimensions require more indexes

::

::div{class="normal-text-small" style="font-size:1.07rem !important; line-height:1.45 !important;"}

### Memory View

- Elements occupy **contiguous memory**
- Rows are stored in **row-major order**
- One complete row is followed by the next
- The column count is needed to locate a particular element

::

::

::div{class="definition-box" style="margin-top:18px !important; font-size:1.3rem !important;"}
A multidimensional array gives us a **row-and-column abstraction**, while the underlying elements remain contiguous in memory.
::

---

# From 2D Arrays to 2D Vectors

::div{class="grid grid-cols-2 gap-10 mt-5"}

::div{class="normal-text-small-compact"}

### Traditional 2D Array

```cpp
int matrix[3][4];
```

- Fixed number of rows and columns
- All rows have the same length
- Elements form one contiguous block
- Dimensions cannot change after creation

::

::div{class="normal-text-small-compact"}

### 2D Vector

```cpp
std::vector<std::vector<int>> matrix;
```

This is a **vector of vectors**.

- The outer vector represents the rows
- Each row is a separate `vector<int>`
- Rows can be resized independently
- Rows may have different lengths

::

::

::div{class="definition-box" style="margin-top:10px !important; font-size:1.3rem !important;"}
A 2D vector provides familiar `matrix[row][column]` access while allowing the structure to change at runtime.
::

---

# Understanding a 2D Vector

::div{class="grid grid-cols-2 gap-10 mt-5"}

::div{class="normal-text-small-compact"}

Consider:

```cpp
std::vector<std::vector<int>> matrix;
```

Read it from the inside out:

```cpp
std::vector<int>
```

represents **one row**.

The outer vector:

```cpp
std::vector< ... >
```

stores those row vectors.

::

::div{class="normal-text-small-compact"}

Therefore:

```cpp
matrix[1]
```

selects **row 1**.

Then:

```cpp
matrix[1][2]
```

selects element `2` from that row.

Conceptually:

```text
matrix[1]       → one row
matrix[1][2]    → one element
```

::

::

::div{class="definition-box" style="margin-top:10px !important; font-size:1.3rem !important;"}
`matrix[row][column]` first selects a **row vector**, then selects an element from that vector.
::

---

# Creating a 2D Vector

::div{class="grid grid-cols-2 gap-10 mt-5"}

::div{class="normal-text-small-compact"}

### Empty 2D Vector

```cpp
std::vector<std::vector<int>> matrix;
```

Initially there are no rows:

```cpp
matrix.size();   // 0
```

### Specify Dimensions

```cpp
int rows = 3;
int cols = 4;

std::vector<std::vector<int>> matrix(
    rows,
    std::vector<int>(cols)
);
```

::

::div{class="normal-text-small-compact"}

This creates:

```text
3 rows × 4 elements per row
```

For `int`, the elements are initialized to `0`.

Access and modify elements using:

```cpp
matrix[1][2] = 10;

cout << matrix[1][2];
```

The syntax is similar to a traditional 2D array:

```cpp
matrix[row][column]
```

::

::

::div{class="definition-box" style="margin-top:8px !important; font-size:1.3rem !important;"}
With a 2D vector, the number of rows and the size of each row can be determined at **runtime**.
::

---

# Initializing a 2D Vector

::div{class="grid grid-cols-2 gap-10 mt-5"}

::div{class="normal-text-small-compact"}

### Initializer List

```cpp
std::vector<std::vector<int>> grid = {
    {1, 2, 3},
    {4, 5, 6},
    {7, 8, 9}
};
```

This creates **3 row vectors**, each containing **3 integers**.

::

::div{class="normal-text-small-compact"}

### Access and Modify

```cpp
cout << grid[0][0];   // 1
cout << grid[1][2];   // 6
cout << grid[2][1];   // 8
```

Modify an element:

```cpp
grid[1][2] = 25;
```

Now:

```cpp
cout << grid[1][2];   // 25
```

::

::

::div{class="definition-box" style="margin-top:10px !important; font-size:1.3rem !important;"}
The first index selects the **row**; the second index selects the **element within that row**.
::

---

# Traversing a 2D Vector

::div{class="grid grid-cols-2 gap-10 mt-5"}

::div{class="normal-text-small-compact"}

### Index-Based Loop

```cpp
for (std::size_t i = 0;
     i < grid.size(); ++i) {

    for (std::size_t j = 0;
         j < grid[i].size(); ++j) {

        cout << grid[i][j] << " ";
    }

    cout << '\n';
}
```

Use this when you need the **row and column indexes**.

::

::div{class="normal-text-small-compact"}

### Range-Based Loop

```cpp
for (const auto& row : grid) {
    for (const auto& value : row) {
        cout << value << " ";
    }
    cout << '\n';
}
```

Here:

```cpp
grid.size()
```

gives the number of rows.

```cpp
grid[i].size()
```

gives the number of elements in row `i`.

::

::

::div{class="definition-box" style="margin-top:8px !important; font-size:1.03rem !important;"}
Use each row's `size()` when traversing because different rows can have **different lengths**.
::

---

# How Is a 2D Vector Stored?

::div{class="grid grid-cols-2 gap-10 mt-5"}

::div{class="normal-text-small-compact"}

### Traditional 2D Array

```cpp
int matrix[3][4];
```

All 12 integers are stored as **one contiguous block**.

One row immediately follows another in memory.

This is why the compiler can calculate an element's location using the number of columns.

::

::div{class="normal-text-small-compact"}

### 2D Vector

```cpp
std::vector<std::vector<int>> matrix;
```

The outer vector contains **vector objects**.

Each inner vector manages the storage for its own elements.

Therefore:

```cpp
matrix[0]
matrix[1]
matrix[2]
```

are independent row vectors.

::

::

::div{class="definition-box" style="margin-top:8px !important; font-size:1.3rem !important;"}
Elements within each row vector are **contiguous**, but a `vector<vector<int>>` does not guarantee that all rows form one contiguous block.
::

---

# Rows Can Change Independently

::div{class="grid grid-cols-2 gap-10 mt-5"}

::div{class="normal-text-small-compact"}

Start with:

```cpp
std::vector<std::vector<int>> matrix = {
    {1, 2, 3},
    {4, 5, 6},
    {7, 8, 9}
};
```

Add an element to row `0`:

```cpp
matrix[0].push_back(10);
```

Only that row changes.

::

::div{class="normal-text-small-compact"}

### Before

```text
Row 0:  1  2  3
Row 1:  4  5  6
Row 2:  7  8  9
```

### After

```text
Row 0:  1  2  3  10
Row 1:  4  5  6
Row 2:  7  8  9
```

The other rows are unaffected.

::

::

::div{class="definition-box" style="margin-top:8px !important; font-size:1.3rem !important;"}
Because each row is a separate vector, operations such as `push_back()`, `erase()`, and `resize()` can be applied to an individual row.
::

---

# Removing an Element from One Row

::div{class="grid grid-cols-2 gap-10 mt-5"}

::div{class="normal-text-small-compact"}

Suppose:

```cpp
std::vector<std::vector<int>> matrix = {
    {1, 2, 3},
    {4, 5, 6},
    {7, 8, 9}
};
```

Remove element at index `1` from row `0`:

```cpp
matrix[0].erase(
    matrix[0].begin() + 1
);
```

::

::div{class="normal-text-small-compact"}

### Before

```text
Row 0:  1  2  3
Row 1:  4  5  6
Row 2:  7  8  9
```

### After

```text
Row 0:  1  3
Row 1:  4  5  6
Row 2:  7  8  9
```

Only **row 0** changed.

::

::

::div{class="definition-box" style="margin-top:8px !important; font-size:1.3rem !important;"}
Removing an element from one row does **not** automatically remove elements from the other rows.
::

---

# What Does "Remove a Column" Mean?

::div{class="normal-text-small-compact"}

In a `vector<vector<int>>`, there is no separate **column object**.

A column is simply the elements at the same position in multiple rows.

To remove column `1` from a rectangular 2D vector:

```cpp
for (auto& row : matrix) {
    row.erase(row.begin() + 1);
}
```

::

::div{class="grid grid-cols-2 gap-10 mt-3"}

::div{class="normal-text-small-compact"}

### Before

```text
1  2  3
4  5  6
7  8  9
```

::

::div{class="normal-text-small-compact"}

### After

```text
1  3
4  6
7  9
```

::

::

::div{class="definition-box" style="margin-top:8px !important; font-size:1.3rem !important;"}
To remove a complete column, you must remove the corresponding element from **each row**.
::

---

# Jagged 2D Vectors

::div{class="grid grid-cols-2 gap-10 mt-5"}

::div{class="normal-text-small-compact"}

Rows do not have to contain the same number of elements:

```cpp
std::vector<std::vector<int>> data = {
    {1, 2, 3, 4},
    {5, 6},
    {7, 8, 9}
};
```

This is commonly called a **jagged** structure.

::

::div{class="normal-text-small-compact"}

Each row has its own size:

```cpp
data[0].size();   // 4
data[1].size();   // 2
data[2].size();   // 3
```

So:

```text
Row 0:  1  2  3  4
Row 1:  5  6
Row 2:  7  8  9
```

is completely valid.

::

::

::div{class="definition-box" style="margin-top:8px !important; font-size:1.3rem !important;"}
A 2D vector can represent a **rectangular grid** or a **jagged structure** with different row lengths.
::

---

# Memory Layout of a Jagged 2D Vector

::div{class="grid grid-cols-2 gap-10 mt-5"}

::div{class="normal-text-small-compact"}

### Each Row Is Contiguous

Consider:

```cpp
std::vector<std::vector<int>> data = {
    {10, 20, 30, 40},
    {50, 60},
    {70, 80, 90}
};
```

Each inner vector manages its own contiguous storage:

```text
Row 0:  10  20  30  40

Row 1:  50  60

Row 2:  70  80  90
```

Within a row, elements are stored **next to each other in memory**.

::

::div{class="normal-text-small-compact"}

### But Rows Are Independent

The outer vector contains separate `vector<int>` objects.

Each row manages its **own element storage**, so the rows may be located at different memory addresses.

Therefore:

```text
Row 0 storage  → one location

Row 1 storage  → another location

Row 2 storage  → another location
```

There may be unrelated memory between these allocations.

::

::

::div{class="definition-box" style="margin-top:10px !important; font-size:1.03rem !important;"}
In a `vector<vector<int>>`, elements within **each row are contiguous**, but the elements of different rows are **not guaranteed to form one contiguous block**.
::

---

# Memory Utilization of a Jagged Vector

::div{class="grid grid-cols-2 gap-10 mt-5"}

::div{class="normal-text-small-compact"}

### Rectangular Structure

Suppose every row reserves space for 5 integers:

```text
Row 0:  ■ ■ ■ ■ ■
Row 1:  ■ ■ ■ ■ ■
Row 2:  ■ ■ ■ ■ ■
```

Total elements:

```text
3 × 5 = 15
```

If some rows need fewer elements, part of that rectangular structure may be unnecessary for the logical data.

::

::div{class="normal-text-small-compact"}

### Jagged Structure

Each row can contain only the elements it needs:

```text
Row 0:  ■ ■ ■ ■ ■
Row 1:  ■ ■
Row 2:  ■ ■ ■
```

Total elements:

```text
5 + 2 + 3 = 10
```

This can avoid storing **unused logical elements**.

However, each inner vector also has its own management information and may have unused **capacity**.

::

::

::div{class="definition-box" style="margin-top:0px !important; font-size:1.1rem !important;"}
Jagged vectors can save **element storage when row lengths naturally differ**, but they also have per-row vector and allocation overhead.
::

---

# 2D Array vs. 2D Vector

::div{class="normal-text-small-compact"}

<table style="width:100%; border-collapse:collapse; font-size:0.96rem;">
<tr style="border-bottom:1px solid #666;">
<th style="text-align:left; padding:7px;">Feature</th>
<th style="text-align:left; padding:7px;">2D Array</th>
<th style="text-align:left; padding:7px;">2D Vector</th>
</tr>
<tr style="border-bottom:1px solid #555;">
<td style="padding:7px;">Example</td>
<td style="padding:7px;"><code>int a[3][4]</code></td>
<td style="padding:7px;"><code>vector&lt;vector&lt;int&gt;&gt;</code></td>
</tr>
<tr style="border-bottom:1px solid #555;">
<td style="padding:7px;">Dimensions</td>
<td style="padding:7px;">Fixed</td>
<td style="padding:7px;">Can change</td>
</tr>
<tr style="border-bottom:1px solid #555;">
<td style="padding:7px;">Row lengths</td>
<td style="padding:7px;">Same</td>
<td style="padding:7px;">Can differ</td>
</tr>
<tr style="border-bottom:1px solid #555;">
<td style="padding:7px;">Resize a row</td>
<td style="padding:7px;">No</td>
<td style="padding:7px;">Yes</td>
</tr>
<tr style="border-bottom:1px solid #555;">
<td style="padding:7px;">Whole structure contiguous</td>
<td style="padding:7px;">Yes</td>
<td style="padding:7px;">Not guaranteed</td>
</tr>
<tr>
<td style="padding:7px;">Element access</td>
<td style="padding:7px;"><code>a[row][column]</code></td>
<td style="padding:7px;"><code>a[row][column]</code></td>
</tr>
</table>

::

::div{class="definition-box" style="margin-top:10px !important; font-size:1.3rem !important;"}
Use a 2D array for a **fixed rectangular structure**. Use a 2D vector when the dimensions or individual row lengths need to **change at runtime**.
::



---

# Introducing `std::array`

::div{class="grid grid-cols-2 gap-10 mt-5"}

::div{class="normal-text-small" style="font-size:1.08rem !important; line-height:1.4 !important;"}

### What Is `std::array`?

`std::array` is a **fixed-size container** provided by the C++ Standard Library.

```cpp
#include <array>

std::array<int, 5> scores;
```

Like a built-in array:

- The number of elements is fixed
- Elements have the same type
- Elements are stored contiguously
- Elements can be accessed using `[]`

::

::div{class="normal-text-small" style="font-size:1.08rem !important; line-height:1.4 !important;"}

### Why Use It?

`std::array` provides useful container operations:

```cpp
scores.size();
scores.at(2);
scores.front();
scores.back();
```

It also works naturally with:

- Range-based loops
- Iterators
- Standard Library algorithms
- Copying and assignment

::

::

::div{class="definition-box" style="margin-top:14px !important; font-size:1.3rem !important;"}
Think of `std::array` as a **modern C++ fixed-size array**.
::

---

# Creating a `std::array`

::div{class="grid grid-cols-2 gap-10 mt-5"}

::div{class="normal-text-small"}

### General Form

```cpp
std::array<dataType, size> name;
```

Example:

```cpp
std::array<int, 5> scores;
```

Both the **element type** and **size** are part of the type.

```cpp
std::array<int, 5> a;
std::array<int, 10> b;
```

These are different types.

::

::div{class="normal-text-small"}

### Initialization

```cpp
std::array<int, 5> scores =
    {85, 90, 78, 92, 88};
```

Access elements using indexes:

```cpp
cout << scores[0];   // 85
cout << scores[2];   // 78
cout << scores[4];   // 88
```

For five elements, valid indexes are:

```text
0, 1, 2, 3, 4
```

::

::

---

# Accessing `std::array` Elements

::div{class="grid grid-cols-2 gap-10 mt-5"}

::div{class="normal-text-small"}

### Indexed Access

```cpp
std::array<int, 4> data =
    {10, 20, 30, 40};

cout << data[2];
```

Output:

```text
30
```

`[]` does **not perform bounds checking**.

```cpp
data[10];   // invalid index
```

This results in **undefined behavior**.

::

::div{class="normal-text-small"}

### Member Functions

```cpp
cout << data.at(2);   // 30

cout << data.front(); // 10

cout << data.back();  // 40

cout << data.size();  // 4
```

`at()` performs bounds checking.

An invalid index causes:

```text
std::out_of_range
```

::

::

::div{class="definition-box" style="margin-top:12px !important; font-size:1.3rem !important;"}
Just like `std::vector`: `[]` is unchecked, while `at()` performs bounds checking.
::

---

# Traversing a `std::array`

::div{class="grid grid-cols-2 gap-10 mt-5"}

::div{class="normal-text-small"}

### Counter-Based Loop

```cpp
std::array<int, 4> data =
    {10, 20, 30, 40};

for (std::size_t i = 0;
     i < data.size(); ++i) {

    cout << data[i] << ' ';
}
```

Use this when you need the **index**.

::

::div{class="normal-text-small"}

### Range-Based Loop

```cpp
std::array<int, 4> data =
    {10, 20, 30, 40};

for (const auto& value : data) {
    cout << value << ' ';
}
```

Use this when you only need each **element**.

::

::

::div{class="definition-box" style="margin-top:12px !important; font-size:1.3rem !important;"}
The same traversal techniques used with arrays and vectors also work with `std::array`.
::

---

# `std::array` with Standard Algorithms

::div{class="grid grid-cols-2 gap-10 mt-5"}

::div{class="normal-text-small"}

### Sorting

```cpp
#include <algorithm>
#include <array>

std::array<int, 5> values =
    {5, 2, 4, 1, 3};

std::sort(
    values.begin(),
    values.end()
);
```

After sorting:

```text
1  2  3  4  5
```

::

::div{class="normal-text-small"}

### Calculating a Sum

```cpp
#include <numeric>

int sum = std::accumulate(
    values.begin(),
    values.end(),
    0
);
```

Result:

```text
15
```

`begin()` and `end()` provide iterators that can be used with Standard Library algorithms.

::

::

---

# Comparing Array Types

::div{class="normal-text-small-compact" style="font-size:0.92rem !important;"}

<table style="width:100%; table-layout:fixed; border-collapse:collapse;">
<tr>
<th style="width:25%; padding:9px 12px; text-align:left;">Feature</th>
<th style="width:25%; padding:9px 12px; text-align:center;">Built-In Array</th>
<th style="width:25%; padding:9px 12px; text-align:center;"><code>std::array</code></th>
<th style="width:25%; padding:9px 12px; text-align:center;"><code>std::vector</code></th>
</tr>
<tr>
<td style="padding:9px 12px; text-align:left;"><strong>Example</strong></td>
<td style="padding:9px 12px; text-align:center;"><code>int a[5]</code></td>
<td style="padding:9px 12px; text-align:center;"><code>std::array&lt;int, 5&gt;</code></td>
<td style="padding:9px 12px; text-align:center;"><code>std::vector&lt;int&gt;</code></td>
</tr>
<tr>
<td style="padding:9px 12px; text-align:left;"><strong>Size</strong></td>
<td style="padding:9px 12px; text-align:center;">Fixed</td>
<td style="padding:9px 12px; text-align:center;">Fixed</td>
<td style="padding:9px 12px; text-align:center;">Dynamic</td>
</tr>
<tr>
<td style="padding:9px 12px; text-align:left;"><strong>Contiguous</strong></td>
<td style="padding:9px 12px; text-align:center;">Yes</td>
<td style="padding:9px 12px; text-align:center;">Yes</td>
<td style="padding:9px 12px; text-align:center;">Yes</td>
</tr>
<tr>
<td style="padding:9px 12px; text-align:left;"><strong><code>size()</code></strong></td>
<td style="padding:9px 12px; text-align:center;">—</td>
<td style="padding:9px 12px; text-align:center;">Yes</td>
<td style="padding:9px 12px; text-align:center;">Yes</td>
</tr>
<tr>
<td style="padding:9px 12px; text-align:left;"><strong><code>at()</code></strong></td>
<td style="padding:9px 12px; text-align:center;">—</td>
<td style="padding:9px 12px; text-align:center;">Yes</td>
<td style="padding:9px 12px; text-align:center;">Yes</td>
</tr>
<tr>
<td style="padding:9px 12px; text-align:left;"><strong>Resizable</strong></td>
<td style="padding:9px 12px; text-align:center;">No</td>
<td style="padding:9px 12px; text-align:center;">No</td>
<td style="padding:9px 12px; text-align:center;">Yes</td>
</tr>
<tr>
<td style="padding:9px 12px; text-align:left;"><strong>Container assignment</strong></td>
<td style="padding:9px 12px; text-align:center;">No</td>
<td style="padding:9px 12px; text-align:center;">Yes</td>
<td style="padding:9px 12px; text-align:center;">Yes</td>
</tr>
</table>

::

::div{class="definition-box" style="margin-top:18px !important; font-size:1.02rem !important; line-height:1.3 !important;"}
**Choosing between them:** Use `std::array` for a **fixed number of elements**. Use `std::vector` when the number of elements may **change at runtime**.
::


---

# `std::array` or `std::vector`?

::div{class="normal-text-small" style="font-size:1.05rem !important; line-height:1.35 !important;"}

Choose based primarily on whether the number of elements can change.

::

::div{class="grid grid-cols-2 gap-10 mt-4"}

::div{class="normal-text-small"}

### Use `std::array`

When the number of elements is **fixed and known at compile time**.

```cpp
std::array<double, 7> temperatures;

std::array<int, 12> monthlySales;

std::array<int, 3> coordinates;
```

Examples:

- Days of the week
- Months of the year
- RGB values
- Fixed-size coordinates

::

::div{class="normal-text-small"}

### Use `std::vector`

When the number of elements is **dynamic or determined at runtime**.

```cpp
std::vector<int> scores;

scores.push_back(85);
scores.push_back(90);
```

Or:

```cpp
int numberOfStudents;
cin >> numberOfStudents;

std::vector<double> grades(
    numberOfStudents
);
```

::

::

::div{class="definition-box" style="margin-top:10px !important; font-size:1.3rem !important; text-align:center;"}
**Fixed size → `std::array` &nbsp;&nbsp;&nbsp; | &nbsp;&nbsp;&nbsp; Dynamic size → `std::vector`**
::

---

# Passing Arrays to Functions

::div{class="normal-text-small" style="font-size:1.12rem !important; line-height:1.45 !important;"}

Arrays and array-like containers can be passed to functions.

However, the three types we have studied behave differently:

```cpp
int numbers[5];

std::array<int, 5> numbers;

std::vector<int> numbers;
```

The important question is:

::div{style="font-size:1.4rem !important; line-height:1.3 !important; margin-top:28px !important; text-align:center;"}
**What information does the function receive?**
::

::

::div{class="definition-box" style="margin-top:22px !important; font-size:1.08rem !important;"}
We will compare how **built-in arrays**, `std::array`, and `std::vector` are passed to functions.
::

---

# Passing a Built-In Array

::div{class="grid grid-cols-2 gap-10 mt-5"}

::div{class="normal-text-small" style="font-size:1.05rem !important; line-height:1.4 !important;"}

### Function

```cpp
void printArray(
    const int arr[],
    int size
) {
    for (int i = 0; i < size; ++i) {
        cout << arr[i] << " ";
    }
}
```

### Function Call

```cpp
int numbers[] =
    {10, 20, 30, 40, 50};

printArray(numbers, 5);
```

::

::div{class="normal-text-small" style="font-size:1.05rem !important; line-height:1.4 !important;"}

### What Happens?

For a function parameter:

```cpp
const int arr[]
```

is adjusted to:

```cpp
const int* arr
```

The function can access the elements, but it does **not automatically know the number of elements**.

That is why we also pass:

```cpp
int size
```

::

::

::div{class="definition-box" style="margin-top:16px !important; font-size:1.0rem !important;"}
A built-in array parameter behaves as a **pointer to its first element**, so the size is commonly passed separately.
::

---

# Passing `std::array`

::div{class="grid grid-cols-2 gap-10 mt-5"}

::div{class="normal-text-small" style="font-size:1.05rem !important; line-height:1.4 !important;"}

### Function

```cpp
void printArray(
    const std::array<int, 5>& arr
) {
    for (int value : arr) {
        cout << value << " ";
    }
}
```

### Function Call

```cpp
std::array<int, 5> numbers =
    {10, 20, 30, 40, 50};

printArray(numbers);
```

::

::div{class="normal-text-small" style="font-size:1.05rem !important; line-height:1.4 !important;"}

### What's Different?

The function receives a **reference to the `std::array` object**.

The container retains its size information:

```cpp
arr.size()
```

For:

```cpp
std::array<int, 5>
```

the size `5` is part of the type.

No separate size argument is needed.

::

::

::div{class="definition-box" style="margin-top:0px !important; font-size:1rem !important;"}
`std::array` is especially useful when the number of elements is **fixed** but you want a modern container interface.
::

---

# Passing `std::vector`

::div{class="grid grid-cols-2 gap-10 mt-5"}

::div{class="normal-text-small" style="font-size:1.05rem !important; line-height:1.4 !important;"}

### Function

```cpp
void printVector(
    const std::vector<int>& values
) {
    for (int value : values) {
        cout << value << " ";
    }
}
```

### Function Call

```cpp
std::vector<int> scores =
    {90, 85, 88, 92};

printVector(scores);
```

::

::div{class="normal-text-small" style="font-size:1.05rem !important; line-height:1.4 !important;"}

### What's Different?

The vector keeps track of its own size:

```cpp
values.size()
```

The number of elements is **not part of the type**:

```cpp
std::vector<int>
```

The same function can therefore receive vectors containing different numbers of elements.

::

::

::div{class="definition-box" style="margin-top:16px !important; font-size:1.3rem !important;"}
Use `std::vector` when the number of elements may **change at runtime**.
::

---

# `const &` — Why Do We Use It?

::div{class="grid grid-cols-2 gap-10 mt-6"}

::div{class="normal-text-small" style="font-size:1.05rem !important; line-height:1.4 !important;"}

### Read Only

```cpp
void display(
    const std::vector<int>& values
) {
    for (int value : values)
        cout << value << " ";
}
```

`&` means the vector is **not copied**.

`const` means the function cannot modify it through `values`.

Use this when the function only needs to **read** the elements.

::

::div{class="normal-text-small" style="font-size:1.05rem !important; line-height:1.4 !important;"}

### Allow Modification

```cpp
void addScore(
    std::vector<int>& values
) {
    values.push_back(100);
}
```

Without `const`, the function can modify the original vector.

After:

```cpp
addScore(scores);
```

the original `scores` vector contains the new element.

::

::

::div{class="definition-box" style="margin-top:18px !important; font-size:1.03rem !important;"}
`const T&` → read without copying &nbsp;&nbsp;&nbsp;&nbsp; `T&` → allow modification without copying
::

---

# Passing Arrays

::div{class="grid grid-cols-3 gap-6 mt-8"}

::div{class="normal-text-small" style="text-align:center; font-size:1.02rem !important;"}

### Built-In Array

```cpp
void process(
    const int arr[],
    int size
);
```

**Size information is not carried by the pointer-style parameter**

Size is commonly passed separately.

::

::div{class="normal-text-small" style="text-align:center; font-size:1.02rem !important;"}

### `std::array`

```cpp
void process(
    const std::array<int, 5>& arr
);
```

**Fixed size**

Size is part of the type.

```cpp
arr.size()
```

::

::div{class="normal-text-small" style="text-align:center; font-size:1.02rem !important;"}

### `std::vector`

```cpp
void process(
    const std::vector<int>& values
);
```

**Dynamic size**

Container tracks its size.

```cpp
values.size()
```

::

::

::div{class="definition-box" style="margin-top:26px !important; font-size:1.05rem !important;"}
Built-in array → size handled separately &nbsp;&nbsp; | &nbsp;&nbsp; `std::array` → fixed size known by the container &nbsp;&nbsp; | &nbsp;&nbsp; `std::vector` → dynamic size managed by the container
::

---

# Which Should I Use?

::div{class="grid grid-cols-3 gap-7 mt-8"}

::div{class="normal-text-small" style="text-align:center; font-size:1.04rem !important;"}

### Built-In Array

```cpp
int values[5];
```

Useful for understanding fundamental C++ array behavior and when working with APIs that use raw arrays.

::

::div{class="normal-text-small" style="text-align:center; font-size:1.04rem !important;"}

### `std::array`

```cpp
std::array<int, 5> values;
```

Use when the number of elements is **fixed**.

Provides a modern container interface while retaining fixed size.

::

::div{class="normal-text-small" style="text-align:center; font-size:1.04rem !important;"}

### `std::vector`

```cpp
std::vector<int> values;
```

Use when the number of elements may **change at runtime**.

The most flexible choice for dynamically sized sequences.

::

::

::div{class="definition-box" style="margin-top:28px !important; font-size:1.08rem !important;"}
For new C++ code: **fixed number of elements → `std::array`** &nbsp;&nbsp;&nbsp; **variable number of elements → `std::vector`**
::


---

# Lecture Summary

::div{class="normal-text-small" style="font-size:1.12rem !important; line-height:1.5 !important;"}

- **Built-in arrays** store fixed-size collections of elements of the same type.
- Array elements are stored **contiguously** and accessed using zero-based indexes.
- **2D arrays** organize elements into rows and columns and are stored in row-major order.
- **Dynamic arrays** allow the size to be chosen at runtime but require manual memory management with `new[]` and `delete[]`.
- `std::vector` provides a **dynamic-size container** with automatic memory management.
- A `vector<vector<T>>` can represent 2D and **jagged** collections; each inner vector manages its own contiguous storage.
- `std::array` provides a modern container interface for **fixed-size** collections.
- When passing containers to functions, use **`const &`** for read-only access without copying and **`&`** when modification is required.

::

::div{class="definition-box" style="margin-top:2px !important; font-size:1.02rem !important;"}
**Modern C++:** Use `std::array` when the size is fixed and `std::vector` when the size may change at runtime.
::


---

<div class="definition-box">
Arrays organize same-type elements in contiguous memory for indexed access; use <code>std::array</code> for fixed-size collections and <code>std::vector</code> for dynamic-size collections.
</div>


---
layout: default
---

<div class="grid grid-cols-[40%] gap-4 h-full items-center">

<div class="flex justify-start -translate-y-6">
  <img
    src="/images/owl.png"
    class="w-[100%] rounded-xl"
  />
</div>


</div>

---

<QuizQuestion
  question="Q1. Which statement correctly describes a built-in array in C++?"
  :options="[
    'It automatically checks whether every index is valid',
    'It stores a fixed number of same-type elements in contiguous memory',
    'It can store elements of different data types under one variable name',
    'Its size automatically increases when new elements are added'
  ]"
  correct="It stores a fixed number of same-type elements in contiguous memory"
  explanation="A built-in array is a fixed-size collection of elements of the same type, and its elements are stored contiguously in memory."
/>

---

# Q2. Examine the following code:

::div{style="font-size:0.85rem !important; margin-top:12px; margin-bottom:28px;"}

```cpp
int values[] = {10, 20, 30, 40, 50};
cout << values[3];
```

::

::div{style="margin-top:12px;"}

<QuizQuestion
  question="What is printed?"
  :options="[
    '30',
    '50',
    '40',
    'Undefined behavior'
  ]"
  correct="40"
  explanation="Array indexing starts at 0. Therefore, `values[3]` accesses the fourth element, which contains 40."
/>

::

---

# Q3. Examine the following code:

::div{style="font-size:0.85rem !important; margin-top:12px; margin-bottom:28px;"}

```cpp
int numbers[] = {10, 20, 30};

for (auto& value : numbers) {
    value = value * 2;
}
```

::

::div{style="margin-top:12px;"}

<QuizQuestion
  question="What are the contents of `numbers` after the loop?"
  :options="[
    '`{20, 40, 60}`',
    '`{10, 20, 30}`',
    '`{10, 40, 30}`',
    '`{20, 20, 30}`'
  ]"
  correct="`{20, 40, 60}`"
  explanation="`auto&` makes `value` a reference to each actual array element. Modifying `value` therefore modifies the original array."
/>

::

---

# Q4. Examine the following code:

::div{style="font-size:0.85rem !important; margin-top:12px; margin-bottom:28px;"}

```cpp
int* numbers = new int[100];

// use numbers

numbers = nullptr;
```

::

::div{style="margin-top:12px;"}

<QuizQuestion
  question="What problem does this code create?"
  :options="[
    'The array contains only 99 elements',
    '`nullptr` automatically deletes only the first element',
    'The array becomes a fixed-size local array',
    'The allocated memory is not released before its address is lost'
  ]"
  correct="The allocated memory is not released before its address is lost"
  explanation="The storage created by `new[]` was not released with `delete[]` before `numbers` was set to `nullptr`. The allocated storage can no longer be reached through this pointer, resulting in a memory leak."
/>

::

---

# Q5. Examine the following code:

::div{style="font-size:0.85rem !important; margin-top:12px; margin-bottom:28px;"}

```cpp
std::vector<int> numbers = {10, 20, 30};

numbers.push_back(40);
numbers.push_back(50);
numbers.pop_back();
```

::

::div{style="margin-top:12px;"}

<QuizQuestion
  question="What are the final size and contents of `numbers`?"
  :options="[
    'size = 5, contents = {10, 20, 30, 40, 50}',
    'size = 4, contents = {10, 20, 30, 40}',
    'size = 3, contents = {10, 20, 30}',
    'size = 4, contents = {20, 30, 40, 50}'
  ]"
  correct="size = 4, contents = {10, 20, 30, 40}"
  explanation="The two `push_back()` calls add 40 and 50. `pop_back()` removes the last element, 50, leaving four elements."
/>

::

---

<QuizQuestion
  question="Q6. Which statement correctly describes `size()` and `capacity()` for a `std::vector`?"
  :options="[
    '`size()` and `capacity()` must always have the same value',
    '`capacity()` is the maximum number of elements the vector can ever contain',
    '`size()` is the number of existing elements; `capacity()` is how many elements can fit in the current storage before reallocation',
    '`size()` is the available storage; `capacity()` is the number of existing elements'
  ]"
  correct="`size()` is the number of existing elements; `capacity()` is how many elements can fit in the current storage before reallocation"
  explanation="`size()` reports how many elements currently exist. `capacity()` reports how many elements can fit in the vector's current storage before reallocation is required."
/>

---

# Q7. Examine the following code:

::div{style="font-size:0.85rem !important; margin-top:12px; margin-bottom:28px;"}

```cpp
int grid[2][3] = {
    {10, 20, 30},
    {40, 50, 60}
};

cout << grid[1][2];
```

::

::div{style="margin-top:12px;"}

<QuizQuestion
  question="What is printed?"
  :options="[
    '40',
    '30',
    '50',
    '60'
  ]"
  correct="60"
  explanation="`grid[1]` selects the second row, {40, 50, 60}. `[2]` then selects the third element of that row, which is 60."
/>

::

---

# Q8. Examine the following code:

::div{style="font-size:0.85rem !important; margin-top:12px; margin-bottom:28px;"}

```cpp
std::vector<std::vector<int>> data = {
    {1, 2, 3},
    {4, 5, 6},
    {7, 8, 9}
};

data[1].push_back(10);
```

::

::div{style="margin-top:12px;"}

<QuizQuestion
  question="What are the sizes of rows 0, 1, and 2 after the code executes?"
  :options="[
    '3, 4, 3',
    '4, 4, 4',
    '3, 3, 3',
    '4, 3, 3'
  ]"
  correct="3, 4, 3"
  explanation="Each row is a separate vector. `data[1].push_back(10)` adds an element only to row 1, so its size becomes 4 while rows 0 and 2 remain size 3."
/>

::

---

<QuizQuestion
  question="Q9. A program always stores exactly 12 monthly sales values. Which container is the most appropriate choice?"
  :options="[
    '`double*` created using `new[]`',
    '`std::vector<double>`',
    '`std::array<double, 12>`',
    '`std::vector<std::vector<double>>`'
  ]"
  correct="`std::array<double, 12>`"
  explanation="The number of elements is fixed and known at compile time, making `std::array` an appropriate modern C++ fixed-size container."
/>

---

# Q10. Examine the following function:

::div{style="font-size:0.85rem !important; margin-top:12px; margin-bottom:28px;"}

```cpp
void printArray(const int arr[], int size) {
    for (int i = 0; i < size; ++i) {
        cout << arr[i] << ' ';
    }
}
```

::

::div{style="margin-top:12px;"}

<QuizQuestion
  question="Why is `size` passed as a separate parameter?"
  :options="[
    'The `size` parameter automatically performs bounds checking',
    'The pointer-style array parameter does not carry the original array length',
    'The function uses `size` to dynamically allocate the array',
    'Built-in arrays cannot be traversed without two parameters'
  ]"
  correct="The pointer-style array parameter does not carry the original array length"
  explanation="In a function parameter, `const int arr[]` is adjusted to `const int*`. The function can access the elements, but the pointer does not carry the original array's element count, so the size is commonly passed separately."
/>

::

---

# Success

<div class="grid grid-cols-[32%_68%] gap-14 mt-2 items-center">

<div>
  <img
    src="/images/success.png"
    class="w-full rounded-xl"
  />
</div>

<div class="definition-box text-center !mt-0 -translate-y-15">
“Student success is built one step at a time — practice programming for just 30 minutes every day, and watch small efforts grow into big achievements.”
</div>

</div>

---

