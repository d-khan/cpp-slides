---
theme: dracula
background: https://cover.sli.dev
title: Basic elements of C++
author: Dr Danish Khan
transition: fade-out
mdc: true

---

# Decision statements


Dr. Danish Khan | dkhan@sdccd.edu


Press Space for next page

---

# Learning Outcomes

<div class="normal-text" style="font-size: 24px;">

By the end of this lesson, you will be able to:

- Use `if`, `else if`, and `else` statements to make decisions
- Use `switch` statements for multi-way selection
- Determine when to use an `if` chain or a `switch` statement
- Use comparison and logical operators to create conditions
- Explain precedence and short-circuit evaluation in logical expressions
- Use the conditional (`?:`) operator for simple decisions
- Identify and correct common errors in decision statements

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

# Why Decision Statements?

<div class="definition-box">
Programs need to make decisions. A <strong>decision statement</strong> allows a program to choose what to do based on whether a condition is <strong>true</strong> or <strong>false</strong>.
</div>

<div class="normal-text" style="font-size: 24px; margin-top: 20px;">

### Example

- Is the user's password correct?
- Is the temperature above a certain value?
- Did the student pass the course?
- Which menu option did the user select?

Without decision statements, a program would simply execute the same sequence of instructions every time.

</div>


---

# Boolean Conditions & Truth Values

<div class="definition-box">
A <code>bool</code> has one of two values: <strong>true</strong> or <strong>false</strong>. Decision statements use Boolean conditions to determine which code executes.
</div>

<div class="normal-text" style="font-size: 22px; margin-top: 15px;">

<div class="grid grid-cols-2 gap-10">

<div>

### Comparison Operators

| Operator | Meaning |
|:--------:|---------|
| `==` | Equal to |
| `!=` | Not equal to |
| `<` | Less than |
| `>` | Greater than |
| `<=` | Less than or equal to |
| `>=` | Greater than or equal to |

</div>

<div>

### Logical Operators

- `&&` — AND
- `||` — OR
- `!` — NOT

### Example

```cpp
int age = 20;

bool adult = age >= 18;

if (adult) {
    cout << "Adult";
}
```

</div>

</div>
</div>

---

# Basic `if`, `else if`, `else`

<div class="grid grid-cols-2 gap-8" style="margin-top: 20px;">

<div>

<div class="definition-box">
Conditions are checked <strong>from top to bottom</strong>. The first condition that evaluates to <strong>true</strong> executes, and the remaining branches are skipped.
</div>

<div class="normal-text" style="font-size: 21px; margin-top: 20px;">

- `if` checks the first condition
- `else if` checks additional conditions
- `else` handles all remaining cases
- Use `{ }` braces for clarity and safety

</div>

</div>

<div>

<div class="code-title">Assigning a Letter Grade</div>

<div style="height: 390px; overflow-y: auto;">

```cpp
#include <iostream>
using namespace std;

int main() {
    int score = 85;

    if (score >= 90) {
        cout << "Grade: A";
    }
    else if (score >= 80) {
        cout << "Grade: B";
    }
    else if (score >= 70) {
        cout << "Grade: C";
    }
    else if (score >= 60) {
        cout << "Grade: D";
    }
    else {
        cout << "Grade: F";
    }

    return 0;
}
```

</div>

</div>
</div>

---

# Nested Decisions

<div class="grid grid-cols-2 gap-8" style="margin-top: -28px !important;">

<div>

<div class="definition-box">
A <strong>nested decision</strong> is an <code>if</code> statement placed inside another <code>if</code> or <code>else</code> statement.
</div>

<div class="normal-text" style="font-size: 19px; margin-top: 22px;">

### How It Works

- The outer condition is checked first
- The inner condition is checked only if its branch is reached
- Each `else` belongs to the nearest unmatched `if`
- Use `{ }` and indentation to make the structure clear

</div>

</div>

<div>

<div class="code-title">Checking Age and ID</div>

<div style="height: 390px; overflow-y: auto;">

```cpp
#include <iostream>
using namespace std;

int main() {
    int age = 20;
    bool hasID = true;

    if (age >= 18) {

        if (hasID) {
            cout << "Entry allowed";
        }
        else {
            cout << "ID required";
        }

    }
    else {
        cout << "Must be 18 or older";
    }

    return 0;
}
```

</div>

</div>
</div>


---

# Short-Circuit Evaluation

<div class="definition-box">
With <code>&&</code> and <code>||</code>, C++ evaluates conditions from <strong>left to right</strong> and stops when the result is already known.
</div>

<div class="grid grid-cols-2 gap-8" style="margin-top: 8px;">

<div class="normal-text" style="font-size: 18px;">

### Short-Circuit Rules

- `A && B` → if `A` is **false**, `B` is skipped
- `A || B` → if `A` is **true**, `B` is skipped

### Example

```cpp
int x = 0;

if (x != 0 && 10 / x > 2) {
    cout << "True";
}
```

Since `x != 0` is false, C++ skips `10 / x > 2`, preventing division by zero.

</div>

<div class="normal-text" style="font-size: 18px;">

### Truth Table

<div class="compact-table">

| A | B | `A && B` | `A \|\| B` |
|:-:|:-:|:--------:|:----------:|
| F | F | F | F |
| F | T | F | T |
| T | F | F | T |
| T | T | T | T |

</div>

### Remember

- `&&` → **both** conditions must be true
- `||` → **at least one** condition must be true

</div>

</div>

<style>
.compact-table table {
  margin-top: 4px !important;
  margin-bottom: 10px !important;
}

.compact-table th,
.compact-table td {
  padding: 3px 10px !important;
  line-height: 1.1 !important;
}
</style>

---

# The Ternary Operator `?:`

<div class="definition-box" style="margin-top: -10px !important;">
The <strong>ternary operator</strong> provides a compact way to choose between two values based on a condition.
</div>

<div class="grid grid-cols-2 gap-8" style="margin-top: 10px;">

<div class="normal-text" style="font-size: 18px;">

### Syntax

```cpp
condition ? value_if_true : value_if_false
```

### How It Works

- Condition is `true` → first value is selected
- Condition is `false` → second value is selected

### Remember

Think of it as:

```text
condition ? TRUE choice : FALSE choice
```

</div>

<div class="normal-text" style="font-size: 18px;">

### Example

```cpp
int age = 17;

string status =
    (age >= 18) ? "Adult" : "Minor";

cout << status;
```

Since `age >= 18` is false:

```text
Minor
```

</div>

</div>

<div class="definition-box" style="font-size: 18px; margin-top: 8px;">
Use <code>?:</code> for <strong>simple choices</strong>. Use <code>if</code> and <code>else</code> for complex or multi-step decisions.
</div>

---

# Input Validation

<div class="definition-box" style="margin-top: 0px !important; font-size: 20px;">
<strong>Input validation</strong> checks whether user input is valid before the program uses it.
</div>

<div class="grid grid-cols-2 gap-10" style="margin-top: 8px;">

<div class="normal-text compact-validation" style="font-size: 18px;">

### What Should We Check?

1. <strong>Is the input the correct type?</strong>
   - Did `cin` successfully read the value?

2. <strong>Is the value acceptable?</strong>
   - Does it satisfy the program's requirements?

### Key Idea

<strong>Validate first.</strong> Use the input only after it passes all required checks.

</div>

<div class="normal-text" style="font-size: 18px;">

### Example Inputs

<div class="compact-input-table">

| Input | Result | Reason |
|:---:|:---:|---|
| `25` | Valid | Correct type and acceptable value |
| `-5` | Invalid | Value is not acceptable |
| `hello` | Invalid | Not an integer |

</div>

</div>

</div>

<style>
.compact-validation ol,
.compact-validation ul {
  margin-top: 3px !important;
  margin-bottom: 8px !important;
}

.compact-validation li {
  margin-top: 2px !important;
  margin-bottom: 3px !important;
  line-height: 1.2 !important;
}

.compact-validation li ul {
  margin-top: 1px !important;
  margin-bottom: 5px !important;
}

.compact-input-table table {
  margin-top: 5px !important;
  width: 100% !important;
}

.compact-input-table th,
.compact-input-table td {
  padding: 4px 7px !important;
  line-height: 1.1 !important;
  height: auto !important;
  font-size: 16px !important;
}
</style>

---

# Input Validation Example

<div class="definition-box" style="margin-top: 0px !important;">
First check whether the input operation <strong>succeeded</strong>. Then check whether the value is within the <strong>acceptable range</strong>.
</div>

<div style="margin-top: 10px;">

<div class="code-title">Validating a Positive Integer</div>

<div style="height: 290px; overflow-y: auto;">

```cpp
#include <iostream>
using namespace std;

int main() {
    int number{};

    cout << "Enter a positive integer: ";

    // Check the input type
    if (!(cin >> number)) {
        cerr << "Invalid input\n";
        return 1;
    }

    // Check the value
    if (number <= 0) {
        cerr << "Number must be positive\n";
        return 1;
    }

    cout << "Valid input: " << number;

    return 0;
}
```

</div>

</div>

---

# What is `cerr`?

<div class="definition-box" style="margin-top: 0px !important; font-size: 19px;">
<code>cerr</code> is the C++ <strong>standard error stream</strong>, used for error messages and diagnostic information.
</div>

<div class="grid grid-cols-2 gap-8" style="margin-top: 5px;">

<div class="normal-text cerr-content" style="font-size: 17px;">

### `cout` vs `cerr`

- `cout` → normal program output
- `cerr` → error messages
- Both are provided by `<iostream>`

### Example

```cpp
if (number <= 0) {
    cerr << "Error: number must be positive\n";
    return 1;
}
```

`cerr` indicates that the message represents an **error**, not normal output.

</div>

<div class="normal-text cerr-content" style="font-size: 17px;">

### Why Use `cerr`?

Separating normal output from errors makes programs easier to debug.

Errors can also be redirected to a file:

```bash
./program 2> errors.txt
```

- `2` → standard error
- `>` → redirect
- `errors.txt` → destination file

`cout` output is unaffected.

</div>

</div>

---

# `cout` vs `cerr`

<div class="normal-text compact-stream-table" style="font-size: 19px; margin-top: 15px;">

| Feature | `cout` — Standard Output | `cerr` — Standard Error |
|---|---|---|
| **Purpose** | Display normal program output | Report problems |
| **Stream** | Standard output (`stdout`) | Standard error (`stderr`) |
| **Examples** | Results, prompts, messages | Errors, warnings, diagnostics |
| **Redirection** | `> output.txt` | `2> errors.txt` |

</div>

<div class="grid grid-cols-2 gap-8" style="margin-top: 15px;">

<div>

<div class="code-title">Normal Output</div>

```cpp
cout << "Total: " << total << '\n';
```

</div>

<div>

<div class="code-title">Error Output</div>

```cpp
cerr << "Error: invalid input\n";
```

</div>

</div>

<div class="definition-box" style="font-size: 18px; margin-top: 15px;">
<strong>Remember:</strong> <code>cout</code> is for normal output; <code>cerr</code> is for errors.
</div>

---

# Switch Statements

<div class="definition-box" style="margin-top: -12px !important; font-size: 19px;">
A <code>switch</code> statement selects one of several branches based on the value of an expression.
</div>

<div class="grid grid-cols-2 gap-8" style="margin-top: 8px;">

<div class="normal-text switch-info" style="font-size: 18px;">

### Key Parts

- `switch` → value to examine
- `case` → possible matching value
- `break` → exits the `switch`
- `default` → handles no match

### Important

- `case` labels must be constant values
- Without `break`, execution continues into the next case
- Multiple cases can intentionally share the same code


</div>

<div style="transform: translateY(-5px);">

<div class="code-title">Grading with switch</div>

<div style="height: 300px; overflow-y: auto;">

```cpp
#include <iostream>
using namespace std;

int main() {
    char grade{};

    cout << "Enter grade: ";
    cin >> grade;

    switch (grade) {
        case 'A':
        case 'B':
            cout << "Great job!\n";
            break;

        case 'C':
            cout << "Solid.\n";
            break;

        case 'D':
        case 'F':
            cout << "Let's review.\n";
            break;

        default:
            cout << "Invalid grade\n";
    }

    return 0;
}
```

</div>
</div>
</div>

---

# `switch` with `enum class`

<div class="definition-box" style="margin-top: -12px !important; font-size: 20px !important; padding: 7px 12px !important;">
An <code>enum class</code> gives meaningful names to a fixed set of values, making a <code>switch</code> easier to read.
</div>

<div class="grid grid-cols-2 gap-8" style="margin-top: 5px;">

<div class="normal-text enum-info" style="font-size: 16px;">

### Define the Choices

```cpp
enum class Menu {
    New = 1,
    Open = 2,
    Save = 3,
    Quit = 9
};
```

### Why Use an Enum?

Instead of using numbers such as `1`, `2`, and `3`, we use meaningful names:

- `Menu::New`
- `Menu::Open`
- `Menu::Save`
- `Menu::Quit`

This makes the code easier to read and maintain.

</div>

<div style="transform: translateY(-5px);">

<div class="code-title">Menu Selection</div>

<div style="height: 340px; overflow-y: auto;">

```cpp
int choice{};
cin >> choice;

switch (static_cast<Menu>(choice)) {
    case Menu::New:
        cout << "New file\n";
        break;

    case Menu::Open:
        cout << "Open file\n";
        break;

    case Menu::Save:
        cout << "Save file\n";
        break;

    case Menu::Quit:
        cout << "Quit\n";
        break;

    default:
        cout << "Invalid choice\n";
}
```

</div>

</div>

</div>

<style>
.enum-info h3 {
  margin-top: 3px !important;
  margin-bottom: 3px !important;
}

.enum-info p,
.enum-info ul {
  margin-top: 2px !important;
  margin-bottom: 4px !important;
}

.enum-info li {
  margin: 0 !important;
  line-height: 1.1 !important;
}
</style>

---

# Common Pitfalls & How to Avoid Them

<div class="normal-text compact-content" style="font-size: 20px; margin-top: 20px;">

- **Accidental assignment:** use `==` for comparison, not `=`

- **Missing braces:** use `{ }` to avoid a dangling `else`

- **Incorrect `else if` ranges:** check boundary values carefully

- **Missing `break` in `switch`:** prevents unintended fall-through

- **Incorrect logical operators:** check whether you need `&&`, `||`, or `!`

</div>

<div class="definition-box" style="font-size: 26px !important; margin-top: 28px !important;">
Plan your decision logic before coding, especially when conditions involve multiple branches.
</div>

---

# Debugging Tips

<div class="normal-text compact-content" style="font-size: 19px; transform: translateY(16px);">

- <strong>Print key values</strong> before a decision to verify what the program sees

  ```cpp
  cout << "x = " << x << '\n';
  ```

- <strong>Test boundary values</strong> — for example, `59`, `60`, and `61` for a cutoff of `60`

- <strong>Simplify complex conditions</strong> temporarily to isolate the problem

- <strong>Check <code>switch</code> statements</strong> for missing `break` statements and unexpected values


</div>

---

# GCC Warning Options

<div class="normal-text compact-content" style="font-size: 17px; margin-top: 8px;">

<div class="grid grid-cols-3 gap-8">

<div>

### `-Wall`

- Enables many commonly useful warnings
- Helps catch common programming mistakes

</div>

<div>

### `-Wextra`

- Enables additional warnings
- Example: unused function parameters

</div>

<div>

### `-Wconversion`

- Warns when an implicit conversion may change a value

```cpp
int number = 3.9;
```

`3.9` becomes `3`.

</div>

</div>

### Compile with All Three

```bash
g++ -Wall -Wextra -Wconversion main.cpp -o main
```

<div class="definition-box" style="font-size: 20px !important; line-height: 1.3 !important; margin-top: 20px !important; padding-left: 14px !important;">
<strong>Good practice:</strong> Read compiler warnings carefully. A program may compile successfully and still contain potential problems.
</div>

</div>

---

# Lecture Summary

<div class="normal-text-small">

- **Decision Statements** → Allow a program to choose which code executes based on a condition.

- **Comparison Operators** → `==`, `!=`, `<`, `>`, `<=`, and `>=` compare values and produce a Boolean result.

- **Logical Operators** → `&&`, `||`, and `!` combine or modify conditions.

- **`if`, `else if`, `else`** → Select between alternative paths based on one or more conditions.

- **Nested Decisions** → Place one decision inside another when additional conditions must be checked.

- **Short-Circuit Evaluation** → `&&` and `||` may stop evaluating as soon as the final result is known.

</div>

---

# Lecture Summary (contd.)

<div class="normal-text-small">

- **Ternary Operator `?:`** → Provides a compact alternative to `if`/`else` for simple two-way choices.

- **`switch` Statements** → Use `case`, `break`, and `default` to select among specific values.

- **`enum class`** → Provides meaningful names for fixed choices and works well with `switch`.

- **Input Validation** → Verify that input is the correct type and within an acceptable range before using it.

- **Error Handling & Debugging** → Use `cerr`, boundary testing, and compiler warnings to identify potential problems.

- **Key Idea** → Choose the simplest decision structure that clearly represents the program's logic.

</div>


---

<div class="definition-box">
The power of a program lies not only in what it can do, but in how it decides what to do next.
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
    'Grade: A',
    'Grade: B',
    'Grade: C',
    'Grade: F'
  ]"
  correct="Grade: B"
  explanation="Conditions are checked from top to bottom. `score >= 90` is false, but `score >= 80` is true. That branch executes and the remaining branches are skipped."
>

```cpp
int score = 85;

if (score >= 90) {
    cout << "Grade: A";
}
else if (score >= 80) {
    cout << "Grade: B";
}
else if (score >= 70) {
    cout << "Grade: C";
}
else {
    cout << "Grade: F";
}
```

</QuizQuestion>

---

<QuizQuestion
  question="2. What does this code display?"
  :options="[
    'Entry allowed',
    'ID required',
    'Must be 18 or older',
    'Nothing'
  ]"
  correct="Must be 18 or older"
  explanation="The outer condition `age >= 18` is false when age is 17. Therefore, the nested decision is never reached and the outer `else` executes."
>

```cpp
int age = 17;
bool hasID = true;

if (age >= 18) {
    if (hasID) {
        cout << "Entry allowed";
    }
    else {
        cout << "ID required";
    }
}
else {
    cout << "Must be 18 or older";
}
```

</QuizQuestion>

---

<QuizQuestion
  question="3. Which value of `age` makes this entire condition false?"
  :options="[
    '18',
    '25',
    '65',
    '70'
  ]"
  correct="70"
  explanation="The `&&` operator requires both conditions to be true. For age 70, `age >= 18` is true but `age <= 65` is false, making the entire condition false."
>

```cpp
if (age >= 18 && age <= 65) {
    cout << "Accepted";
}
```

</QuizQuestion>

---

<QuizQuestion
  question="4. When `x` is 0, what happens to the expression `10 / x > 2`?"
  :options="[
    'It is evaluated and causes division by zero',
    'It is skipped',
    'It evaluates to false',
    'C++ changes x to 1 before evaluating it'
  ]"
  correct="It is skipped"
  explanation="With `&&`, C++ uses short-circuit evaluation. Since `x != 0` is false, the entire condition must be false, so the second expression is not evaluated."
>

```cpp
int x = 0;

if (x != 0 && 10 / x > 2) {
    cout << "True";
}
```

</QuizQuestion>

---

<QuizQuestion
  question="5. What value is stored in `status`?"
  :options="[
    'Adult',
    'Minor',
    'true',
    'false'
  ]"
  correct="Adult"
  explanation="The condition `age >= 18` is true when age is 20, so the ternary operator selects the first value, `Adult`."
>

```cpp
int age = 20;

string status =
    (age >= 18) ? "Adult" : "Minor";
```

</QuizQuestion>

---

<QuizQuestion
  question="6. The user enters `-5`. Which validation check detects the problem?"
  :options="[
    '!(cin >> number)',
    'number <= 0',
    'Both checks fail',
    'Neither check detects it'
  ]"
  correct="number <= 0"
  explanation="`-5` is a valid integer, so `cin >> number` succeeds. However, the value is not positive, so `number <= 0` is true."
>

```cpp
int number{};

if (!(cin >> number)) {
    cerr << "Invalid input\n";
    return 1;
}

if (number <= 0) {
    cerr << "Number must be positive\n";
    return 1;
}
```

</QuizQuestion>

---

<QuizQuestion
  question="7. What does this `switch` display when `grade` is `'B'`?"
  :options="[
    'Great job!',
    'Solid.',
    'Invalid grade',
    'Nothing'
  ]"
  correct="Great job!"
  explanation="The `A` and `B` cases intentionally share the same statements. When grade is `B`, execution reaches `Great job!`, and `break` then exits the switch."
>

```cpp
char grade = 'B';
switch (grade) {
    case 'A':
    case 'B':
        cout << "Great job!\n";
        break;
    case 'C':
        cout << "Solid.\n";
        break;
    default:
        cout << "Invalid grade\n";
}
```

</QuizQuestion>

---

<QuizQuestion
  question="8. What does this code display?"
  :options="[
    'New',
    'Open',
    'New followed by Open',
    'Invalid'
  ]"
  correct="New followed by Open"
  explanation="The first case has no `break`, so execution falls through into case 2. The program therefore displays both `New` and `Open`."
>

```cpp
int choice = 1;

switch (choice) {
    case 1:
        cout << "New\n";

    case 2:
        cout << "Open\n";
        break;

    default:
        cout << "Invalid\n";
}
```

</QuizQuestion>

---

<QuizQuestion
  question="9. Which case executes when `choice` is `Menu::Save`?"
  :options="[
    'Menu::New',
    'Menu::Open',
    'Menu::Save',
    'default'
  ]"
  correct="Menu::Save"
  explanation="An `enum class` provides scoped, meaningful names for its values. Since `choice` contains `Menu::Save`, the matching `Menu::Save` case executes."
>

<div class="scroll-code" style="--code-height: 250px;">

```cpp
enum class Menu {
    New = 1,
    Open = 2,
    Save = 3,
    Quit = 9
};

Menu choice = Menu::Save;

switch (choice) {
    case Menu::New:
        cout << "New";
        break;

    case Menu::Open:
        cout << "Open";
        break;

    case Menu::Save:
        cout << "Save";
        break;

    default:
        cout << "Other";
}
```

</div>

</QuizQuestion>

---

<QuizQuestion
  question="10. Which change correctly fixes the condition?"
  :options="[
    'Change `x = 10` to `x == 10`',
    'Change `x = 10` to `x != 10`',
    'Change `if` to `switch`',
    'Declare x as bool'
  ]"
  correct="Change `x = 10` to `x == 10`"
  explanation="The `=` operator performs assignment. To test whether `x` is equal to 10, use the comparison operator `==`."
>

```cpp
int x = 5;

if (x = 10) {
    cout << "Equal";
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