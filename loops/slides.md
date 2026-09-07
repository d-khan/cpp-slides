---
theme: dracula
background: https://cover.sli.dev
title: Loops
author: Dr Danish Khan
transition: fade-out
mdc: true

---

# Loops


Dr. Danish Khan | dkhan@sdccd.edu


Press Space for next page

---

# Learning Outcomes

<div class="normal-text" style="font-size: 1.6rem !important;">

- Explain the purpose of `while`, `for`, and `do-while` loops.
- Use loops for counting, summing, and processing input.
- Apply `break` and `continue` to control loop execution.
- Trace loops and identify logic errors and infinite loops.
- Select and use the appropriate loop structure, including nested loops.

</div>

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

# Why Is Repetition Needed?

<div class="definition-box">
Repetition allows a program to perform the same task multiple times without rewriting the same code. In C++, repetition is implemented using loops such as <code>while</code>, <code>for</code>, and <code>do-while</code>.
</div>

<div class="normal-text" style="font-size: 1.4rem !important; margin-top: 1.5rem;">

Imagine a computer game that asks:

**"Do you want to play again?"**

If the player enters **Y**, the game runs again. If the player enters **N**, the program ends.

A **loop** allows the program to repeat the game as long as the player wants to continue.

</div>

---

# `while` Loop

<div class="grid grid-cols-2 gap-8">

<div class="normal-text" style="font-size: 1.35rem !important;">

### General Form

```cpp
while (condition) {
    statement;
    statement;
}
```

The condition is checked **before** each iteration.

</div>

<div>

<div class="code-title">Counter-Controlled while Loop</div>

```cpp
#include <iostream>
using namespace std;

int main() {
    int x = 5;

    while (x > 0) {
        cout << x << endl;
        x--;
    }

    return 0;
}
```

</div>

</div>

<div class="definition-box" style="margin-top: 10px !important; font-size: 1.4rem !important;">
A <code>while</code> loop repeatedly executes a block of code as long as its condition remains true. The loop must eventually change something that causes the condition to become false; otherwise, an infinite loop may occur.
</div>

---

# Sentinel-Controlled `while` Loops

<div class="definition-box" style="margin-top: 8px !important; font-size: 1.3rem !important; line-height: 1.4 !important;">
A sentinel-controlled <code>while</code> loop repeats until a special value, called a <strong>sentinel</strong>, signals the end of input.
</div>

<div class="grid grid-cols-3 gap-6" style="margin-top: 10px;">

<div class="normal-text" style="font-size: 1.1rem !important; line-height: 1.45 !important;">

- The sentinel is **not part of the valid data**.

- Use it when the number of iterations is **not known in advance**.

- Example: `-1` signals that no more values will be entered.

</div>

<div class="col-span-2">

<div class="code-title" style="margin-top: -15px;">Sentinel-Controlled while Loop</div>

<div class="scroll-code" style="--code-height: 330px;">

```cpp
#include <iostream>
using namespace std;

int main() {
    int num;
    int sum = 0;

    cout << "Enter numbers (-1 to stop): ";
    cin >> num;

    while (num != -1) {
        sum += num;
        cin >> num;
    }

    cout << "Sum = " << sum << endl;

    return 0;
}
```

</div>
</div>
</div>

---

# Flag-Controlled `while` Loops

<div class="definition-box" style="margin-top: 8px !important; font-size: 1.3rem !important; line-height: 1.4 !important;">
A flag-controlled <code>while</code> loop uses a Boolean variable, called a <strong>flag</strong>, to determine whether the loop should continue or stop.
</div>

<div class="grid grid-cols-3 gap-6" style="margin-top: 10px;">

<div class="normal-text" style="font-size: 1.1rem !important; line-height: 1.45 !important;">

- The flag is usually initialized to `true`.

- The loop continues while the flag remains `true`.

- An event or condition changes the flag to `false`, causing the loop to stop.

</div>

<div class="col-span-2">

<div class="code-title" style="margin-top: -10px;">Flag-Controlled while Loop</div>

<div class="scroll-code" style="--code-height: 300px;">

```cpp
#include <iostream>
using namespace std;

int main() {
    bool running = true;
    int number;

    while (running) {
        cout << "Enter a number (0 to stop): ";
        cin >> number;

        if (number == 0) {
            running = false;
        }
        else {
            cout << "You entered: "
                 << number << endl;
        }
    }

    return 0;
}
```

</div>

</div>

</div>



---

# EOF Signal

<div class="definition-box" style="margin-top: 8px !important; font-size: 1.3rem !important; line-height: 1.4 !important;">
EOF (End-of-File) is a <strong>signal</strong> that indicates there is no more input to read. EOF is not a character stored in the file.
</div>

<div class="grid grid-cols-3 gap-6" style="margin-top: 10px;">

<div class="normal-text" style="font-size: 1.05rem !important; line-height: 1.4 !important;">

- `cin.get()` returns `EOF` when no more characters can be read.

- **macOS/Linux:** Ctrl+D signals end-of-input.

- **Windows:** Ctrl+Z followed by Enter typically signals end-of-input.

- Store the result of `cin.get()` in an `int` so it can represent both a character and `EOF`.

</div>

<div class="col-span-2">

<div class="code-title" style="margin-top: -10px;">Reading Until EOF</div>

```cpp
#include <iostream>
using namespace std;

int main() {
    int ch;

    while ((ch = cin.get()) != EOF) {
        cout << static_cast<char>(ch);
    }

    cout << "\nEOF reached" << endl;

    return 0;
}
```

</div>

</div>





---

# `for` Loop

<div class="definition-box" style="margin-top: 5px !important; font-size: 1.15rem !important; line-height: 1.25 !important;">
A <code>for</code> loop repeats a block of code and is commonly used when the number of iterations is known in advance.
</div>

<div class="grid grid-cols-3 gap-6" style="margin-top: 5px;">

<div class="normal-text" style="font-size: 0.95rem !important; line-height: 1.25 !important;">

**General Form**

`for (initialization; condition; update)`

- **Initialization** — runs once.
- **Condition** — checked before each iteration.
- **Update** — runs after each iteration.

**Execution Order**

`initialize` → `condition` → `body` → `update`

</div>

<div class="col-span-2">

<div class="code-title" style="margin-top: -15px;">Print Numbers 1 to 5</div>

```cpp
#include <iostream>
using namespace std;

int main() {
    for (int i = 1; i <= 5; i++) {
        cout << i << " ";
    }
    return 0;
}
```

</div>

</div>


---

# Scope of Variables

<div class="definition-box" style="margin-top: 8px !important; font-size: 1.2rem !important; line-height: 1.3 !important;">
The <strong>scope</strong> of a variable determines where it can be accessed in a program. A variable declared in a <code>for</code> loop is available only within that loop.
</div>

<div class="grid grid-cols-2 gap-6" style="margin-top: 10px;">

<div>

<div class="code-title" style="margin-top: 0;">Declared Inside the Loop</div>

```cpp
for (int i = 1; i <= 5; i++) {
    cout << i << " ";
}

// cout << i;   // Error
```

<div class="normal-text" style="font-size: 1rem !important; line-height: 1.3 !important;">

`i` is **out of scope** after the loop.

</div>

</div>

<div>

<div class="code-title" style="margin-top: 0;">Declared Before the Loop</div>

```cpp
int i;

for (i = 1; i <= 5; i++) {
    cout << i << " ";
}

cout << i;   // Valid
```

<div class="normal-text" style="font-size: 1rem !important; line-height: 1.3 !important;">

`i` remains **in scope** after the loop.

</div>

</div>

</div>

---

# Examples of `for` Loops

<div class="grid grid-cols-2 gap-6" style="margin-top: 8px;">

<div>

<div class="code-title" style="margin-top: 0;">1. Even Numbers: 2 to 10</div>

```cpp
for (int i = 2; i <= 10; i += 2) {
    cout << i << " ";
}
```

</div>

<div>

<div class="code-title" style="margin-top: 0;">2. Countdown: 5 to 1</div>

```cpp
for (int i = 5; i >= 1; i--) {
    cout << i << " ";
}
```

</div>

</div>

<div style="margin-top: 8px;">

<div class="code-title" style="margin-top: 0;">3. Multiplication Table of 3</div>

```cpp
for (int i = 1; i <= 10; i++) {
    cout << "3 x " << i << " = "
         << 3 * i << endl;
}
```

</div>

---

# Common Mistakes Using `for` Loops

<div class="code-title" style="margin-top: 5px;">1. Missing Semicolons in the Header</div>

```cpp
// Incorrect
for (int i = 0 i < 5 i++) {
    cout << i << " ";
}
```

<div class="code-title" style="margin-top: 10px;">2. Extra Semicolon After the Loop Header</div>

```cpp
// Incorrect
for (int i = 0; i < 5; i++); {
    cout << "Hello";
}
```

<div class="code-title" style="margin-top: 10px;">3. Update Moves in the Wrong Direction</div>

```cpp
// Incorrect
for (int i = 5; i > 0; i++) {
    cout << i << " ";
}
```

---

# Common Mistakes Using `for` Loops

<div class="code-title" style="margin-top: 5px;">4. Off-by-One Error</div>

```cpp
// Intended: 0 through 4
for (int i = 0; i <= 5; i++) {
    cout << i << " ";
}
```

<div class="code-title" style="margin-top: 10px;">5. Using a Loop Variable Outside Its Scope</div>

```cpp
for (int i = 0; i < 5; i++) {
    cout << i << " ";
}

cout << i;   // Error: i is out of scope
```

<div class="code-title" style="margin-top: 10px;">6. Modifying the Counter Inside the Loop</div>

```cpp
for (int i = 0; i < 5; i++) {
    i += 2;              // Unexpected extra update
    cout << i << " ";
}
```

---

# Nested `for` Loops

<div class="definition-box" style="margin-top: 8px !important; font-size: 1.25rem !important; line-height: 1.35 !important;">
A nested loop is a loop placed inside another loop. For each iteration of the <strong>outer loop</strong>, the <strong>inner loop</strong> completes all of its iterations.
</div>

<div class="grid grid-cols-2 gap-8" style="margin-top: 15px;">

<div>

<div class="code-title" style="margin-top: 0;">Nested for Loop</div>

```cpp
for (int row = 1; row <= 5; row++) {

    for (int col = 1; col <= 5; col++) {
        cout << row * col << " ";
    }

    cout << '\n';
}
```

</div>

<div class="normal-text" style="font-size: 1.05rem !important; line-height: 1.4 !important;">

- The **outer loop** controls the rows.

- The **inner loop** controls the columns.

- For each row, the inner loop runs **5 times**.

- Outer loop: **5 iterations**

- Total calculations: **5 × 5 = 25**

</div>

</div>

---

# Nested `for` Loops: Multiplication Table

<div class="grid grid-cols-3 gap-6" style="margin-top: 10px;">

<div class="col-span-2">

<div class="code-title" style="margin-top: 0;">Multiplication Table: 1 to 5</div>

```cpp
#include <iostream>
#include <iomanip>
using namespace std;

int main() {
    for (int row = 1; row <= 5; row++) {
        for (int col = 1; col <= 5; col++) {
            cout << setw(4) << row * col;
        }

        cout << '\n';
    }

    return 0;
}
```

</div>

<div>

<div class="code-title" style="margin-top: 0;">Output</div>

```text
   1   2   3   4   5
   2   4   6   8  10
   3   6   9  12  15
   4   8  12  16  20
   5  10  15  20  25
```

<div class="normal-text" style="font-size: 0.95rem !important; line-height: 1.3 !important; margin-top: 10px;">

`row * col` calculates the value at each position in the table.

`setw(4)` aligns the output into columns.

</div>

</div>

</div>

---

# When should we be careful with nested `for` loops?

<div class="code-title" style="margin-top: 12px;">1. Performance</div>

<div class="normal-text-small" style="font-size: 1.3rem; line-height: 1.45; margin-top: 8px;">

- One loop over `n` items → **O(n)**
- Two full nested loops → often **O(n²)**
- For `n = 1000`: about **1,000** vs. **1,000,000** iterations

</div>

<div class="code-title" style="margin-top: 18px;">2. Readability</div>

<div class="normal-text-small" style="font-size: 1.3rem; line-height: 1.45; margin-top: 8px;">

- Deep nesting can make program flow difficult to follow.
- More levels of nesting usually make debugging harder.
- Complex inner-loop logic can often be moved into a function.

</div>

<div class="definition-box" style="margin-top: 18px !important; font-size: 1.25rem !important; line-height: 1.4 !important;">
Nested loops are not bad programming. They are often the natural solution for tables, grids, matrices, and comparing combinations of values.
</div>

---

# When should we be careful with nested `for` loops?

<div class="code-title" style="margin-top: 10px;">3. Scalability</div>

<div class="normal-text-small" style="font-size: 1.2rem; line-height: 1.4; margin-top: 6px;">

- Code may run quickly with small input but become much slower as the input grows.
- Each additional level of nesting can greatly increase the amount of work.

</div>

<div class="code-title" style="margin-top: 16px;">4. Consider Other Approaches</div>

<div class="normal-text-small" style="font-size: 1.15rem; line-height: 1.45; margin-top: 8px;">

<div>
  <span style="display:inline-flex; align-items:center; gap:4px;">
    <strong>Functions</strong>
    <VTooltip>
      <span style="cursor:help;">💬</span>
      <template #popper>
        Move complex inner-loop logic into a function to make the program easier to read, test, and debug.
      </template>
    </VTooltip>
  </span>
  — simplify complex loop logic
</div>

<div style="margin-top: 8px;">
  <span style="display:inline-flex; align-items:center; gap:4px;">
    <strong>STL algorithms</strong>
    <VTooltip>
      <span style="cursor:help;">💬</span>
      <template #popper>
        C++ provides algorithms such as
        <span style="font-family:'Courier New', monospace; font-weight:700; color:#2949b8;">std::sort</span>,
        <span style="font-family:'Courier New', monospace; font-weight:700; color:#2949b8;">std::find</span>, and
        <span style="font-family:'Courier New', monospace; font-weight:700; color:#2949b8;">std::count_if</span>
        for common operations such as sorting, searching, and counting.
      </template>
    </VTooltip>
  </span>
  — use existing C++ algorithms when appropriate
</div>

<div style="margin-top: 8px;">
  <span style="display:inline-flex; align-items:center; gap:4px;">
    <strong>Data structures</strong>
    <VTooltip>
      <span style="cursor:help;">💬</span>
      <template #popper>
        Containers such as
        <span style="font-family:'Courier New', monospace; font-weight:700; color:#2949b8;">std::unordered_map</span>
        and
        <span style="font-family:'Courier New', monospace; font-weight:700; color:#2949b8;">std::unordered_set</span>
        provide fast lookup and may reduce repeated searching.
      </template>
    </VTooltip>
  </span>
  — choose a structure that supports efficient access
</div>

<div style="margin-top: 8px;">
  <span style="display:inline-flex; align-items:center; gap:4px;">
    <strong>Better algorithms</strong>
    <VTooltip>
      <span style="cursor:help;">💬</span>
      <template #popper>
        A more efficient algorithm may solve the same problem with fewer operations by avoiding unnecessary repeated work.
      </template>
    </VTooltip>
  </span>
  — reduce unnecessary repeated work
</div>

</div>

<div class="definition-box" style="margin-top: 15px !important; font-size: 1.15rem !important; line-height: 1.3 !important;">
Use nested loops when they naturally match the problem. Consider alternatives when nesting causes unnecessary work or makes the code difficult to understand.
</div>



---

# `do...while` Loop

<div class="definition-box" style="margin-top: 15px !important; font-size: 1.4rem !important; line-height: 1.4 !important;">
A <code>do...while</code> loop executes the loop body first and checks the condition afterward. Therefore, the loop body executes at least once.
</div>

<div class="code-title" style="margin-top: 18px;">General Form</div>

```cpp
do {
    // statements
} while (condition);
```

<div class="normal-text-small" style="font-size: 1.25rem; line-height: 1.45; margin-top: 12px;">

- The loop body executes **before** the condition is tested.
- If the condition is `true`, the loop repeats.
- If the condition is `false`, the loop ends.
- The semicolon after `while (condition)` is required.

</div>

<div class="definition-box" style="margin-top: 18px !important; font-size: 1.25rem !important; line-height: 1.35 !important;">
A <code>do...while</code> loop is called a <strong>post-test loop</strong> because the condition is checked after the loop body.
</div>

---

# `while` vs. `do...while`

<div class="normal-text-small" style="font-size: 1.15rem; line-height: 1.4;">

The key difference is **when the condition is tested**.

</div>

<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 24px; margin-top: 10px;">

<div>

<div class="code-title" style="margin-top: 0;">while — Pre-Test</div>

```cpp
int i = 11;

while (i <= 10) {
    cout << i << " ";
    i += 5;
}
```

<div class="normal-text-small" style="font-size: 1.05rem; line-height: 1.35; margin-top: 8px;">

The condition is checked **first**.

`11 <= 10` is `false`.

**Executes 0 times**

</div>

</div>

<div>

<div class="code-title" style="margin-top: 0;">do...while — Post-Test</div>

```cpp
int i = 11;

do {
    cout << i << " ";
    i += 5;
} while (i <= 10);
```

<div class="normal-text-small" style="font-size: 1.05rem; line-height: 1.35; margin-top: 8px;">

The loop body executes **first**.

The condition is checked afterward.

**Executes 1 time → prints `11`**

</div>

</div>

</div>

<div class="definition-box" style="margin-top: 16px !important; font-size: 1.2rem !important; line-height: 1.35 !important;">
A <code>while</code> loop may execute zero times. A <code>do...while</code> loop always executes at least once.
</div>



---

# `break` and `continue` Statements

<div class="definition-box" style="margin-top: 15px !important; font-size: 1.35rem !important; line-height: 1.4 !important;">
The <code>break</code> and <code>continue</code> statements change the normal flow of a loop.
</div>

<div class="normal-text" style="font-size: 1.35rem !important; line-height: 1.5; margin-top: 18px;">

- `break` — immediately exits the loop.
- `continue` — skips the rest of the current iteration and begins the next iteration.

</div>

<div class="code-title" style="margin-top: 18px;">Using break</div>

```cpp
for (int i = 1; i <= 5; i++) {
    if (i == 3) {
        break;
    }

    cout << i << " ";
}
```

<div class="normal-text-small" style="font-size: 1.15rem; margin-top: 8px;">

Output: `1 2`

When `i` becomes `3`, `break` immediately terminates the loop.

</div>



---

# Lecture Summary

<div class="normal-text" style="font-size: 1.15rem !important; line-height: 1.4; margin-top: 15px;">

- **Loops** repeat statements efficiently and reduce repetitive code.

- `while` — checks the condition **before** each iteration; can use counters, sentinels, flags, or EOF.

- `for` — combines **initialization, condition, and update**; commonly used when the number of iterations is known.

- `do...while` — checks the condition **after** the loop body, so the body executes at least once.

- **Nested loops** place one loop inside another and are useful for tables, grids, and repeated combinations.

- Common problems include **infinite loops, off-by-one errors, incorrect updates, and scope errors**.

- `break` **exits the loop**; `continue` **skips the rest of the current iteration**.

</div>

<div class="definition-box" style="margin-top: 15px !important; font-size: 1.25rem !important; line-height: 1.35 !important;">
Choose the loop that best matches the problem, and always ensure that its condition can eventually become false.
</div>





---

<div class="definition-box">
Choose the loop that best matches the problem, and always ensure that its condition can eventually become false.
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
  question="1. What does this code display?"
  :options="[
    '5 4 3 2 1',
    '5 4 3 2 1 0',
    '4 3 2 1',
    'The loop never ends'
  ]"
  correct="5 4 3 2 1"
  explanation="The `while` loop continues as long as `x > 0`. Each iteration displays `x` and then decreases it by 1. When `x` becomes 0, the condition is false and the loop stops."
>

```cpp
int x = 5;

while (x > 0) {
    cout << x << " ";
    x--;
}
```

</QuizQuestion>

---

<QuizQuestion
  question="2. What is the purpose of `-1` in this loop?"
  :options="[
    'It is added to the sum',
    'It is a sentinel that stops the loop',
    'It resets the sum',
    'It causes the loop to repeat'
  ]"
  correct="It is a sentinel that stops the loop"
  explanation="A sentinel is a special value that signals the end of input. When `num` becomes `-1`, the condition `num != -1` becomes false and the loop stops. The sentinel is not added to the sum."
>

```cpp
int num;
int sum = 0;

cin >> num;

while (num != -1) {
    sum += num;
    cin >> num;
}
```

</QuizQuestion>

---

<QuizQuestion
  question="3. What causes this flag-controlled loop to stop?"
  :options="[
    '`number` becomes negative',
    '`running` is changed to false',
    '`running` is changed to true',
    '`number` becomes greater than 10'
  ]"
  correct="`running` is changed to false"
  explanation="The Boolean variable `running` acts as the flag. When the user enters `0`, `running` becomes `false`. The next time the `while` condition is checked, the loop ends."
>

```cpp
bool running = true;
int number;

while (running) {
    cin >> number;

    if (number == 0) {
        running = false;
    }
}
```

</QuizQuestion>

---

<QuizQuestion
  question="4. Why is the result of `cin.get()` stored in an `int`?"
  :options="[
    'Because `cin.get()` reads only integers',
    'So it can represent both a character value and EOF',
    'Because char variables cannot be compared',
    'Because EOF is a character stored in the file'
  ]"
  correct="So it can represent both a character value and EOF"
  explanation="The result of `cin.get()` is stored in an `int` so it can represent both character values and the special `EOF` signal. The program checks for `EOF` before converting the value to `char` for output."
>

```cpp
int ch;

while ((ch = cin.get()) != EOF) {
    cout << static_cast<char>(ch);
}
```

</QuizQuestion>

---

<QuizQuestion
  question="5. In what order are the parts of this `for` loop executed?"
  :options="[
    'condition → initialization → body → update',
    'initialization → condition → body → update',
    'initialization → body → condition → update',
    'initialization → update → condition → body'
  ]"
  correct="initialization → condition → body → update"
  explanation="The initialization runs once when the loop begins. The condition is then checked. If it is true, the loop body executes, followed by the update. The condition is then checked again."
>

```cpp
for (int i = 1; i <= 5; i++) {
    cout << i << " ";
}
```

</QuizQuestion>

---

<QuizQuestion
  question="6. Why does the final `cout` statement cause an error?"
  :options="[
    '`i` is out of scope after the loop',
    '`i` automatically becomes 0',
    '`cout` cannot display loop variables',
    '`i` must be declared as a double'
  ]"
  correct="`i` is out of scope after the loop"
  explanation="Because `i` is declared inside the `for` loop header, its scope is limited to that loop. After the loop ends, `i` no longer exists in that scope."
>

```cpp
for (int i = 1; i <= 5; i++) {
    cout << i << " ";
}

cout << i;
```

</QuizQuestion>

---

<QuizQuestion
  question="7. What is the problem with this loop?"
  :options="[
    'The counter moves in the wrong direction',
    'The condition should use ==',
    'The loop must begin at 0',
    'The loop executes only once'
  ]"
  correct="The counter moves in the wrong direction"
  explanation="The condition requires `i` to eventually reach 0 or less, but `i++` increases the counter. The counter moves away from the stopping condition, so the loop does not terminate normally. Using `i--` would move it toward 0."
>

```cpp
for (int i = 5; i > 0; i++) {
    cout << i << " ";
}
```

</QuizQuestion>

---

<QuizQuestion
  question="8. How many times does the inner `cout` statement execute?"
  :options="[
    '5 times',
    '10 times',
    '20 times',
    '25 times'
  ]"
  correct="25 times"
  explanation="The outer loop executes 5 times. For each outer-loop iteration, the inner loop executes 5 times. Therefore, the `cout` statement executes 5 × 5 = 25 times."
>

```cpp
for (int row = 1; row <= 5; row++) {
    for (int col = 1; col <= 5; col++) {
        cout << row * col << " ";
    }
}
```

</QuizQuestion>

---

<QuizQuestion
  question="9. What does this `do...while` loop display?"
  :options="[
    'Nothing',
    '11',
    '11 16',
    'The loop never ends'
  ]"
  correct="11"
  explanation="A `do...while` loop executes its body before checking the condition. Therefore, `11` is displayed first. Then `i` becomes 16, the condition `i <= 10` is false, and the loop ends."
>

```cpp
int i = 11;

do {
    cout << i << " ";
    i += 5;
} while (i <= 10);
```

</QuizQuestion>

---

<QuizQuestion
  question="10. What does this code display?"
  :options="[
    '1 2',
    '1 2 3',
    '1 2 4 5',
    '1 2 3 4 5'
  ]"
  correct="1 2 4 5"
  explanation="When `i` is 3, `continue` skips the remaining statement in that iteration, so 3 is not displayed. The loop itself continues, so the output is `1 2 4 5`. Unlike `break`, `continue` does not terminate the loop."
>

```cpp
for (int i = 1; i <= 5; i++) {
    if (i == 3) {
        continue;
    }

    cout << i << " ";
}
```

</QuizQuestion>

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