---
theme: dracula
background: https://cover.sli.dev
title: Basic elements of C++
author: Dr Danish Khan
transition: fade-out
mdc: true

---

# Input and Output


Dr. Danish Khan | dkhan@sdccd.edu


Press Space for next page

---

# Outline

<div class="normal-text">

- What is Input & Output?
- What is IO stream?
- Pre-defined functions
- Formatting decimal output
- List of manipulators

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

# What is Input and Output?

<div class="definition-box">
A program has three basic functions: <strong>input, processing, and output</strong>.
</div>

<div class="h-4"></div> 

<div class="normal-text-small">

- <strong>Input:</strong> Data enters the program through a keyboard, file, or other input device.
- <strong>Processing:</strong> The program manipulates or transforms the data.
- <strong>Output:</strong> Results are sent to a screen, file, printer, or other output device.

</div>

<div class="flex justify-center items-center gap-4 mt-5 text-xl font-bold">

<div class="px-5 py-2 border-2 border-blue-500 rounded-lg">
Input
</div>

<span>→</span>

<div class="px-5 py-2 border-2 border-purple-500 rounded-lg">
Processing
</div>

<span>→</span>

<div class="px-5 py-2 border-2 border-green-500 rounded-lg">
Output
</div>

</div>

---

# What is an I/O Stream?

<div class="definition-box">
A <strong>stream</strong> represents a flow of data between a program and an input or output source.
</div>

<div class="normal-text-small">

- <strong>Input stream</strong> → data flows <strong>into</strong> the program.
  - Example: <code>cin</code> receives input from the keyboard.

- <strong>Output stream</strong> → data flows <strong>out of</strong> the program.
  - Example: <code>cout</code> sends output to the screen.

</div>

<div class="definition-box">
The <code>iostream</code> library provides a simple interface for performing input and output in C++.
</div>

---

# `iostream`

<div class="definition-box">
The <code>iostream</code> header provides the stream classes and objects used for standard input and output in C++.
</div>

<div class="normal-text-small">

### Input and Output Objects

```cpp
istream cin;
ostream cout;
```

<div style="margin-top: 8px;">
  <span style="display:inline-flex; align-items:center; gap:4px;">
    <code>cin</code>
    <VTooltip>
      <span style="cursor:help;">💬</span>
      <template #popper>
        cin is a predefined object of the istream class. By default, it reads input from the keyboard.
      </template>
    </VTooltip>
  </span>
  — standard input object
</div>

<div style="margin-top: 6px;">
  <span style="display:inline-flex; align-items:center; gap:4px;">
    <code>cout</code>
    <VTooltip>
      <span style="cursor:help;">💬</span>
      <template #popper>
        cout is a predefined object of the ostream class. By default, it sends output to the screen.
      </template>
    </VTooltip>
  </span>
  — standard output object
</div>

### Stream Classes

<div>
  <span style="display:inline-flex; align-items:center; gap:4px;">
    <code>istream</code>
    <VTooltip>
      <span style="cursor:help;">💬</span>
      <template #popper>
        istream is the stream class used for reading input.
      </template>
    </VTooltip>
  </span>
  — class for input streams
</div>

<div style="margin-top: 6px;">
  <span style="display:inline-flex; align-items:center; gap:4px;">
    <code>ostream</code>
    <VTooltip>
      <span style="cursor:help;">💬</span>
      <template #popper>
        ostream is the stream class used for writing output.
      </template>
    </VTooltip>
  </span>
  — class for output streams
</div>

</div>

---

# Extraction Operator `>>`

<div class="definition-box">
The extraction operator <code>>></code> reads data from an input stream and stores it in a variable.
</div>

<div class="code-title">How does the input buffer affect extraction?</div>

<div class="scroll-code" style="--code-height: 120px;">

```cpp
#include <iostream>
using namespace std;

int main() {
    char ch;
    int num1, num2;

    cin >> ch;             // User enters: A
    cout << ch << endl;    // Output: A

    cin >> ch;             // User enters: XY
    cout << ch << endl;    // Output: X

    cin >> ch;             // Reads Y already in the input buffer
    cout << ch << endl;    // Output: Y

    cin >> num1 >> num2;   // User enters: 10 20
    cout << num1 << " " << num2 << endl;

    return 0;
}
```

</div>

<div class="normal-text-small" style="margin-top: 8px;">

<strong>What happens when the user enters <code>XY</code>?</strong>

- <code>cin >> ch</code> extracts only <code>X</code> because <code>ch</code> stores one character.
- <code>Y</code> remains in the <strong>input buffer</strong>.
- The next <code>cin >> ch</code> reads <code>Y</code> without requiring new input.

</div>

---

# Important Notes About `cin`

<div class="definition-box">
Input should match the variable's data type. Otherwise, the extraction operation may fail.
</div>

<div class="normal-text-small" style="font-size: 1.05rem; line-height: 1.45;">

### Input Type Matters

- <code>25</code> → <code>int</code> ✓ valid input
- <code>3.14</code> → <code>double</code> ✓ valid input
- <code>Hello</code> → <code>int</code> ✗ extraction fails

### Whitespace and `>>`

- The extraction operator <code>>></code> normally skips leading spaces, tabs, and newlines.
- For more control over the input stream:
  - <code>get()</code> → reads the next character
  - <code>ignore()</code> → skips characters
  - <code>peek()</code> → views the next character without removing it
  - <code>putback()</code> → returns a character to the stream

</div>

---

# Predefined Functions

<div class="definition-box">
C++ provides many <strong>predefined functions</strong> that are already written and ready to use.
</div>

<div class="normal-text-small">

- You do not need to write the code for these functions — you simply <strong>call</strong> them when needed.

- Many predefined functions are provided through the <strong>C++ Standard Library</strong>.

- To use them, include the appropriate header file:
  - <code>&lt;cmath&gt;</code> → <code>sqrt()</code>, <code>pow()</code>
  - <code>&lt;cctype&gt;</code> → <code>toupper()</code>, <code>tolower()</code>

</div>

<div class="definition-box" style="margin-top: 8px !important;">
Later in the course, you will learn how to write and use your <strong>own functions</strong>.
</div>

---

# `cin.get()`

<div class="definition-box">
<code>cin.get()</code> reads the next character from the input stream <strong>without skipping whitespace</strong>.
</div>

<div class="normal-text-small" style="font-size: 1.05rem; line-height: 1.4;">

- <code>get()</code> is a member function of the <code>istream</code> class.
- Use the dot operator <code>.</code> to call it: <code>cin.get(ch)</code>
- The next character—including a space or newline—is stored in <code>ch</code>.

</div>

<div style="transform: translateY(-18px);">

<div class="code-title">Compare >> with get()</div>

<div class="scroll-code" style="height: 180px; margin: 0;">

```cpp
#include <iostream>
using namespace std;

int main() {
    char ch1, ch2;
    int num;

    // User enters: A 25

    cin >> ch1;       // Reads 'A'
    cin.get(ch2);     // Reads the space
    cin >> num;       // Reads 25

    cout << "ch1 = [" << ch1 << "]" << endl;
    cout << "ch2 = [" << ch2 << "]" << endl;
    cout << "num = " << num << endl;

    return 0;
}
```

</div>

<div class="normal-text-small"
     style="font-size: 1.05rem; line-height: 1.3; margin-top: 8px;">

<strong>Key difference:</strong> <code>>></code> skips leading whitespace; <code>get()</code> does not.

</div>

</div>


---

# `cin.ignore()`

<div class="definition-box">
<code>cin.ignore()</code> removes unwanted characters from the input buffer.
</div>

<div class="normal-text-small" style="font-size: 1.05rem; line-height: 1.45;">

### Common Forms

- <code>cin.ignore();</code>  
  → ignores the <strong>next character</strong>.

- <code>cin.ignore(100, '\n');</code>  
  → ignores characters until <code>\n</code> is reached or <strong>100 characters</strong> have been removed.

### Why use it?

It is commonly used to <strong>clear leftover input</strong> before the next input operation.

</div>

---

# `cin.ignore()` Example

<div class="definition-box" style="font-size: 1.5rem !important;">
Use <code>cin.ignore()</code> to discard unwanted characters from the input buffer.
</div>

<div class="code-title">Skipping the Rest of a Line</div>

<div class="scroll-code" style="height: 190px; margin: 0;">

```cpp
#include <iostream>
using namespace std;

int main() {
    int num1, num2;

    // User enters:
    // 1 2 3 4 5
    // 6 7 8 9 10

    cin >> num1;           // Reads 1
    cin.ignore(10, '\n');  // Discards: 2 3 4 5
    cin >> num2;           // Reads 6

    cout << "num1 = " << num1 << endl;
    cout << "num2 = " << num2 << endl;

    return 0;
}
```

</div>

<div class="code-title" style="margin-top: 6px;">Result</div>

<div class="scroll-code" style="height: 50px; margin: 0;">

```text
num1 = 1
num2 = 6
```

</div>

<div class="normal-text-small" style="font-size: 1.05rem; line-height: 1.3; margin-top: 5px;">

<strong>What happened?</strong> After reading <code>1</code>, <code>ignore(10, '\n')</code> discards the rest of the first line. The next <code>>></code> reads <code>6</code>.

</div>

---

# `cin.peek()` & `cin.putback()`

<div class="definition-box" style="font-size: 1.15rem !important; line-height: 1.35 !important;">
Both are member functions of <code>istream</code> used to examine or manage characters in the input stream.
</div>

<div class="normal-text-small" style="font-size: 1.05rem; line-height: 1.4;">

### `cin.peek()`

- Looks at the <strong>next character</strong> without removing it.
- The character remains available for the next input operation.

### `cin.putback(ch)`

- Places <code>ch</code> back into the input stream.
- The character can then be <strong>read again</strong>.

<br>

<strong>Remember:</strong>  
<code>peek()</code> → look ahead &nbsp;&nbsp; | &nbsp;&nbsp; <code>putback()</code> → put it back

</div>

---

# `cin.peek()` & `cin.putback()` Example

<div class="code-title" style="margin-top: -5px;">
Observe the Input Buffer
</div>

<div class="scroll-code" style="height: 250px; margin: 0;">

```cpp
#include <iostream>
using namespace std;

int main() {
    char ch;

    // User enters: Hello

    ch = cin.get();          // Reads and removes 'H'
    cout << ch;              // H

    ch = cin.get();          // Reads and removes 'e'
    cout << ch;              // e

    cin.putback(ch);         // Puts 'e' back into the stream

    ch = cin.get();          // Reads 'e' again
    cout << ch;              // e

    ch = cin.peek();         // Looks at next character: 'l'
    cout << ch;              // l remains in the stream

    ch = cin.get();          // Now reads and removes that 'l'
    cout << ch;              // l

    ch = cin.get();          // Reads next 'l'
    cout << ch;              // l

    return 0;
}
```

</div>

<div class="code-title" style="margin-top: 8px;">Output</div>

```text
User enters: Hello

Heelll
```

<div class="normal-text-small" style="font-size: 1.05rem; line-height: 1.3; margin-top: 5px;">

<strong>Key idea:</strong> <code>putback()</code> returns a character to the stream; <code>peek()</code> views the next character without removing it.

</div>

---

# `cin.clear()`

<div class="definition-box" style="font-size: 1.4rem !important; line-height: 1.4 !important;">
<code>cin.clear()</code> resets the error state of the input stream after an input operation fails.
</div>

<div class="normal-text-small" style="font-size: 1.05rem; line-height: 1.4; padding-top: 15px;">

- Suppose <code>cin</code> expects an <code>int</code>, but the user enters a character.
- The input operation fails and <code>cin</code> enters an <strong>error state</strong>.
- While in this state, further input operations will also fail.

### Recovering from an Input Error

```cpp
cin.clear();             // Reset the error state
cin.ignore(100, '\n');   // Discard the invalid input
```

<strong>Key difference:</strong>

<code>clear()</code> → resets the error state  
<code>ignore()</code> → removes unwanted characters from the input buffer

</div>

---

# Handling `cin` in a Fail State

<div class="code-title" style="margin-top: -5px;">Recovering from Invalid Input</div>

<div class="scroll-code" style="height: 230px; margin-top: 0;">

```cpp
#include <iostream>
using namespace std;

int main() {
    int a, b, c;

    cout << "Enter three integers: ";
    cin >> a >> b >> c;

    if (cin.fail()) {
        cout << "Invalid input!" << endl;

        cin.clear();              // Reset the fail state
        cin.ignore(100, '\n');    // Discard invalid input

        cout << "Try again: ";
        cin >> a >> b >> c;
    }

    cout << "Values: "
         << a << " " << b << " " << c << endl;

    return 0;
}
```

</div>

<div class="code-title" style="margin-top: 8px;">Output</div>

<div class="scroll-code" style="height: 90px; margin-top: 0;">

```text
Enter three integers: 1 3.5 9
Invalid input!
Try again: 9 5 3
Values: 9 5 3
```

</div>

<div class="normal-text-small" style="font-size: 1.05rem; line-height: 1.3; margin-top: 6px;">

<strong>Recovery:</strong> <code>clear()</code> resets the fail state → <code>ignore()</code> removes the invalid input → <code>cin</code> can read again.

</div>

---

# Formatting Decimal Output

<div class="definition-box" style="font-size: 1.15rem !important; line-height: 1.25 !important; margin-top: 10px !important;">
The <code>&lt;iomanip&gt;</code> header provides tools such as <code>fixed</code> and <code>setprecision()</code> to format numeric output.
</div>

<div class="code-title">Using fixed and setprecision()</div>

<div class="scroll-code" style="height: 170px; margin-top: 0;">

```cpp
#include <iostream>
#include <iomanip>
using namespace std;

int main() {
    double pi = 3.141592653589793;
    double value = 5.0;

    // By default: number of significant digits
    cout << setprecision(5) << pi << endl;

    // With fixed: number of digits after decimal point
    cout << fixed << setprecision(5);
    cout << pi << endl;
    cout << value << endl;

    // Change to 2 digits after decimal point
    cout << setprecision(2) << pi << endl;

    return 0;
}
```

</div>

<div class="code-title" style="margin-top: 0px;">Output</div>

<div class="scroll-code" style="height: 90px; margin-top: 0px;">

```text
3.1416
3.14159
5.00000
3.14
```

</div>

<div class="normal-text-small" style="font-size: 1.05rem; line-height: 1.3; margin-top: -12px;">

<strong>Key difference:</strong>  
<code>setprecision(n)</code> → <strong>significant digits</strong>  
<code>fixed + setprecision(n)</code> → <strong>digits after the decimal point</strong>

</div>

---

# List of Manipulators

<div class="scroll-code" style="height: 400px; margin-top: 4px; padding: 16px 24px;">

<div class="normal-text-small" style="font-size: 1.05rem; line-height: 1.35;">

### Basic I/O

- <code>endl</code> — newline and flush output
- <code>flush</code> — flush output buffer
- <code>ws</code> — skip leading whitespace

### Precision & Number Format

- <code>setprecision(n)</code> — control precision
- <code>fixed</code> — fixed-point notation
- <code>scientific</code> — scientific notation

### Display Formatting

- <code>showpoint</code> — show decimal point and trailing zeros
- <code>showpos</code> — show `+` for positive values
- <code>uppercase</code> — use uppercase letters

### Integer Bases

- <code>dec</code> — decimal
- <code>hex</code> — hexadecimal
- <code>oct</code> — octal

### Width & Alignment

- <code>setw(n)</code> — set width for the next value
- <code>setfill(ch)</code> — fill unused width
- <code>left</code> — left-align output
- <code>right</code> — right-align output
- <code>internal</code> — sign left, value right

### Boolean

- <code>boolalpha</code> — display `true` / `false`
- <code>noboolalpha</code> — display `1` / `0`

### Reset

- <code>resetiosflags(flag)</code> — reset a formatting flag

</div>
</div>

---

# Lecture Summary

<div class="normal-text-small">

- **I/O Streams** → Data flows into and out of a program through input and output streams.

- **`cin` & `cout`** → Use `cin` for standard input and `cout` for standard output.

- **Extraction Operator `>>`** → Reads formatted input and normally skips leading whitespace.

- **Input Buffer** → Unread characters remain in the stream and may affect the next input operation.

- **Character Input** → `get()`, `peek()`, and `putback()` provide more control when reading individual characters.

- **Managing Input** → `ignore()` removes unwanted input; `clear()` resets the stream after an input failure.
</div>

---

# Lecture Summary (contd.)

<div class="normal-text-small">

- **Stream Errors** → `cin.fail()` detects input failure, while `cin.clear()` resets the stream state.

- **Output Formatting** → `<iomanip>` manipulators such as `fixed`, `setprecision()`, `setw()`, and `setfill()` control how values are displayed.

- **Number Formats** → Manipulators such as `dec`, `hex`, `oct`, and `scientific` change how numeric values are represented.

- **Alignment & Display** → `left`, `right`, `showpos`, and `boolalpha` provide additional control over formatted output.

- **Key Idea** → C++ streams provide flexible tools for reading, validating, and formatting data.

</div>

---

<div class="definition-box">
Good programming is not just about getting input and producing output — it is about controlling how data flows through your program.
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
  question="1. After this code executes, what value is stored in `ch`?"
  :options="[
    'A',
    'A space character',
    'B',
    'The newline character'
  ]"
  correct="B"
  explanation="The extraction operator `>>` skips leading whitespace. After reading `A`, the next extraction skips the space and reads `B`."
>

```cpp
char ch1, ch;

cin >> ch1;
cin >> ch;

// User enters:
// A B
```

</QuizQuestion>

---

<QuizQuestion
  question="2. What character is stored in `ch2`?"
  :options="[
    'A',
    'A space character',
    'B',
    'No character'
  ]"
  correct="A space character"
  explanation="`cin.get()` does not skip whitespace. After `cin >> ch1` reads `A`, the next character in the input buffer is the space."
>

```cpp
char ch1, ch2;

cin >> ch1;
cin.get(ch2);

// User enters:
// A B
```

</QuizQuestion>

---

<QuizQuestion
  question="3. What value is stored in `num2`?"
  :options="[
    '2',
    '3',
    '5',
    '6'
  ]"
  correct="6"
  explanation="`cin.ignore(10, '\n')` discards the remaining characters on the first line. The next extraction reads `6` from the second line."
>

```cpp
int num1, num2;

cin >> num1;
cin.ignore(10, '\n');
cin >> num2;

// User enters:
// 1 2 3 4 5
// 6 7 8
```

</QuizQuestion>

---

<QuizQuestion
  question="4. What is stored in `ch` after `cin.peek()`?"
  :options="[
    'A',
    'B',
    'C',
    'A space character'
  ]"
  correct="B"
  explanation="`cin.get()` reads and removes `A`. Then `cin.peek()` examines the next character, `B`, without removing it."
>

```cpp
char ch;

ch = cin.get();
ch = cin.peek();

// User enters:
// ABC
```

</QuizQuestion>

---

<QuizQuestion
  question="5. Which statement about first and second is correct?"
  :options="[
    'first is A and second is B',
    'first is B and second is C',
    'Both contain A',
    'Both contain B'
  ]"
  correct="Both contain A"
  explanation="`cin.peek()` examines `A` without removing it. The following `cin.get()` therefore reads the same character, `A`."
>

```cpp
char first, second;

first = cin.peek();
second = cin.get();

// User enters:
// ABC
```

</QuizQuestion>

---

<QuizQuestion
  question="6. What character does the second `cin.get()` read?"
  :options="[
    'A',
    'B',
    'C',
    'A space character'
  ]"
  correct="A"
  explanation="The first `cin.get()` reads `A`. Then `cin.putback(ch)` places `A` back into the input stream, so the second `cin.get()` reads `A` again."
>

```cpp
char ch;

ch = cin.get();
cin.putback(ch);
ch = cin.get();

// User enters:
// ABC
```

</QuizQuestion>

---

<QuizQuestion
  question="7. What happens when the program processes this input?"
  :options="[
    'a = 1, b = 3, c = 9',
    'a = 1, b = 3, then reading c fails',
    'All three extractions fail',
    'b automatically becomes 3.5'
  ]"
  correct="a = 1, b = 3, then reading c fails"
  explanation="Reading `3.5` into integer `b` extracts `3` and leaves `.5` in the input stream. The next extraction into `c` encounters the decimal point and fails."
>

```cpp
int a, b, c;

cin >> a >> b >> c;

// User enters:
// 1 3.5 9
```

</QuizQuestion>

---

<QuizQuestion
  question="8. What does `cin.clear()` do after an input failure?"
  :options="[
    'Deletes all characters from the input buffer',
    'Resets the stream error state',
    'Reads the next valid value',
    'Closes and reopens the input stream'
  ]"
  correct="Resets the stream error state"
  explanation="`cin.clear()` resets the stream error flags. It does not remove invalid characters that may still remain in the input buffer."
>

```cpp
if (cin.fail()) {
    cin.clear();
}
```

</QuizQuestion>

---

<QuizQuestion
  question="9. Why are `clear()` and `ignore()` commonly used together after invalid input?"
  :options="[
    'Both perform exactly the same operation',
    'clear() removes input and ignore() resets errors',
    'clear() resets the error state and ignore() removes unwanted input',
    'They are required before every cin statement'
  ]"
  correct="clear() resets the error state and ignore() removes unwanted input"
  explanation="`cin.clear()` resets the error state, while `cin.ignore()` removes unwanted characters remaining in the input buffer."
>

```cpp
cin.clear();
cin.ignore(100, '\n');
```

</QuizQuestion>

---

<QuizQuestion
  question="10. How is value displayed?"
  :options="[
    '3.1',
    '3.14',
    '3.142',
    '3.14159'
  ]"
  correct="3.14"
  explanation="With `fixed`, `setprecision(2)` specifies two digits after the decimal point. Therefore, `3.14159` is displayed as `3.14`."
>

```cpp
double value = 3.14159;

cout << fixed << setprecision(2)
     << value;
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