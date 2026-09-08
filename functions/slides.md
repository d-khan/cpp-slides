---
theme: dracula
background: https://cover.sli.dev
title: Functions
author: Dr Danish Khan
transition: fade-out
mdc: true

---

# Functions


Dr. Danish Khan | dkhan@sdccd.edu


Press Space for next page

---

# Learning Outcomes

::div{class="normal-text-small" style="font-size:1.15rem; line-height:1.45;"}
By the end of this lecture, you should be able to:

- **Explain** how functions improve program organization, reuse, and readability.
- **Declare, define, and call** `void` and value-returning functions.
- **Use** parameters and arguments to exchange data between functions.
- **Apply** pass by value and pass by reference appropriately.
- **Analyze** variable scope and lifetime within a C++ program.
- **Use** function overloading and default parameters correctly.
- **Organize** function declarations and definitions across program files.
- **Identify and debug** common function-related problems.
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

# Functions

<div class="definition-box">
In C++, a <strong>function</strong> is a named block of code designed to perform a specific task. Functions allow us to divide a large program into smaller, reusable, and manageable pieces.
</div>

---

# Why Functions?

<div class="normal-text-small">

### 1. Code Organization (Modularity)

Functions divide a program into smaller sections. Each function focuses on one well-defined task, making the program easier to understand.

### 2. Reusability

Write a function once and call it whenever the same operation is needed.

### 3. Abstraction

Functions hide implementation details. You mainly need to know what a function does, what information it needs, and what it returns.

</div>

---

# Why Functions?

<div class="normal-text-small">

### 4. Debugging & Testing

Functions make errors easier to isolate because individual parts of a program can be tested separately.

### 5. Avoiding Redundancy

Functions reduce duplicated code. Instead of repeating the same statements, call the function whenever the operation is needed.

</div>

---

# Benefits of Functions

<div class="normal-text-small">

### 1. Readability

Well-named functions make programs easier to read and understand.

### 2. Maintainability

Changes can be made inside one function instead of everywhere the same logic is used.

### 3. Manageability & Scalability

Breaking large programs into smaller functions makes them easier to develop, test, modify, and manage.

</div>


---

<div class="flex justify-center mt-4">
  <img
    src="/images/use-of-functions.png"
    alt="Real-world uses of functions in C++"
    class="max-h-[450px] rounded-lg"
  />
</div>


---


# Predefined Functions

<div class="normal-text-small">

C++ provides many **predefined functions** through its Standard Library.

<div class="mt-3 leading-snug">

- These functions have already been written and tested for us.
- We use them by including the appropriate **header file**.
- For example, `sqrt()` is provided by the `<cmath>` header.
- Think of a function as a **black box**: provide input, perform a task, and possibly return a result.

</div>

### Example

```cpp
#include <cmath>

double result = sqrt(25.0);
```

</div>


---

# Value-Returning Functions with No Arguments

<div class="normal-text-small">

A value-returning function with no arguments **takes no input from the caller** but **returns a value**.

```cpp
return_type functionName() {
    // function body
    return value;
}
```

<div class="code-title !mt-1">Example</div>

<div class="scroll-code" style="--code-height: 200px;">

```cpp {all|4-6|9|all}
#include <iostream>
using namespace std;

int add() {
    return 5 + 10;
}

int main() {
    int result = add();

    cout << "Result: " << result << endl;

    return 0;
}
```

</div>

`add()` takes **no arguments** and returns the integer value `15`.

</div>


---

# Value-Returning Functions with Arguments

<div class="normal-text-small">

A value-returning function with arguments **receives data from the caller** and **returns a value**.

```cpp
return_type functionName(data_type parameter1, data_type parameter2) {
    // function body
    return value;
}
```

<div class="code-title !mt-0">Example</div>

<div class="scroll-code" style="--code-height: 200px;">

```cpp
#include <iostream>
using namespace std;

int add(int x, int y) {
    return x + y;
}

int main() {
    int result = add(5, 10);
    cout << "Result: " << result << endl;
    return 0;
}
```

</div>

`x` and `y` are **parameters**. The values `5` and `10` passed to `add()` are **arguments**.

</div>


---

# Void Functions with No Arguments

<div class="normal-text-small">

A `void` function with no arguments **takes no input from the caller** and **does not return a value**. It performs an action instead.

```cpp
void functionName() {
    // function body
}
```

<div class="code-title !mt-0">Example</div>

<div class="scroll-code" style="--code-height: 210px;">

```cpp
#include <iostream>
using namespace std;

void displaySum() {
    int x = 5;
    int y = 10;

    cout << "Sum: " << x + y << endl;
}

int main() {
    displaySum();

    return 0;
}
```

</div>

`displaySum()` takes **no arguments** and returns **no value**. It performs an action by displaying the sum.

</div>



---

# Void Functions with Parameters

<div class="normal-text-small">

A `void` function can **receive data from the caller** but **does not return a value**.

```cpp
void functionName(data_type parameter1, data_type parameter2) {
    // function body
}
```

<div class="code-title !mt-0">Example</div>

<div class="scroll-code" style="--code-height: 190px;">

```cpp
#include <iostream>
using namespace std;

void displaySum(int x, int y) {
    cout << "Sum: " << x + y << endl;
}

int main() {
    displaySum(5, 10);

    return 0;
}
```

</div>

`x` and `y` are **parameters**. `5` and `10` are **arguments** passed to the function.

`displaySum()` performs an action but returns **no value**.

</div>



---

# Functions Summary

<div class="normal-text-small">

| **Function Type** | **With Parameters** | **Without Parameters** |
|---|---|---|
| **Value-Returning** | Receives input and returns a value<br><br>`int add(int x, int y)` | No input, but returns a value<br><br>`int getNumber()` |
| **Void (Non-returning)** | Receives input and performs an action<br><br>`void displaySum(int x, int y)` | No input and performs an action<br><br>`void displayMessage()` |

</div>

---

# Function Declaration

<div class="definition-box">
A function declaration tells the compiler about a function before it is used.
</div>

<div class="normal-text-small">

- Also called a **function prototype**.
- Specifies the function's **return type**, **name**, and **parameters**.
- Does **not** contain the function body.
- Ends with a semicolon (`;`).

</div>

<div class="code-title">General syntax</div>

```cpp
return_type functionName(parameter_list);
```

<div class="code-title">Example</div>

```cpp
int add(int a, int b);
```

---

# Function Declaration

<div class="normal-text-small">

A declaration is needed when a function is **called before its definition appears**.

</div>

<div class="code-title" style="margin-top:8px;">Declaration → Call → Definition</div>


```cpp
#include <iostream>
using namespace std;

int add(int a, int b);        // declaration

int main() {
    int result = add(5, 10);  // function call
    cout << result;

    return 0;
}

int add(int a, int b) {       // definition
    return a + b;
}
```


---

# Function Definition

<div class="normal-text-small">

- Contains the **function body** — the statements that perform the task.
- The body is enclosed in curly braces `{ }`.
- A value-returning function uses `return` to send a value back to the caller.
- The definition must agree with its declaration in **return type, name, and parameter types/order**.

</div>

<div class="code-title" style="margin-top:8px;">Function definition</div>

```cpp
int add(int a, int b) {       // function header
    int sum = a + b;          // function body
    return sum;               // return value
}
```
---

# Function Declaration vs. Definition

<div class="normal-text-small" style="line-height:1.0;">

| **Aspect** | **Declaration (Prototype)** | **Definition (Implementation)** |
|---|---|---|
| **Purpose** | Tells the compiler about the function | Tells the compiler what the function does |
| **Function Body** | No function body | Contains the function body `{ ... }` |
| **Ending** | Ends with a semicolon `;` | Does not end with a semicolon after `}` |
| **Contains** | Return type, name, and parameter types | Return type, name, parameters, and statements |
| **Example** | `int add(int, int);` | `int add(int a, int b) { return a + b; }` |

</div>

<div class="normal-text-small" style="margin-top:14px; text-align:center;">

**Declaration → describes the function <br>Definition → implements the function**

</div>

---

<div class="flex justify-center mt-4">
  <img
    src="/images/function-declaration.png"
    alt="Real-world uses of functions in C++"
    class="max-h-[450px] rounded-lg"
  />
</div>


---

# Where to Define Functions in C++

<div class="normal-text-small">

### Choice 1: Define Before `main()`

- Define the function **before** `main()`.
- No separate function declaration (prototype) is needed.
- The compiler sees the function definition before the function is called.

</div>

<div class="code-title !mt-0">Function Defined Before main()</div>

```cpp
#include <iostream>
using namespace std;

int add(int a, int b) {
    return a + b;
}

int main() {
    cout << add(5, 3);
    return 0;
}
```

---

# Where to Define Functions in C++

<div class="normal-text-small">

### Choice 2: Define After `main()`

- Define the function **after** `main()`.
- Place a **function declaration (prototype)** before `main()`.
- The declaration tells the compiler about the function before it is called.

</div>

<div class="code-title !mt-0">Declaration Before main(), Definition After main()</div>

<div class="scroll-code" style="--code-height: 200px;">

```cpp
#include <iostream>
using namespace std;

int add(int a, int b);       // function declaration

int main() {
    cout << add(5, 3);
    return 0;
}

int add(int a, int b) {      // function definition
    return a + b;
}
```
</div>

---

# Best Practices for Organizing Functions

<div class="normal-text-small" style="font-size:1.3rem;">

### Small Programs

- Defining functions **before `main()`** is simple and easy to follow.
- A separate function declaration is not required.
- Using a function declaration before `main()` and defining the function afterward is also valid.
- Either approach works well for small, single-file programs.

</div>

---

# Best Practices for Organizing Functions

<div class="normal-text-small">

### Larger Programs

- Place function **declarations** in header files (`.h`).
- Place function **definitions** in source files (`.cpp`).
- Keep `main()` concise by delegating specific tasks to functions.
- This structure makes larger programs easier to organize and maintain.

</div>

<div class="code-title !mt-0">Typical Project Structure</div>

```cpp
// math.h
int add(int a, int b); // Function declaration

// math.cpp
int add(int a, int b) {  // Function definition
    return a + b;
}
```

---

# Project Layout: Simple Projects

<div class="normal-text-small">

For **small programs**, keeping all files in the same folder is perfectly fine.

</div>

<div class="code-title" style="margin-top:8px;">Simple project structure</div>

```text
project/
├── main.cpp
├── mathutils.cpp
└── mathutils.h
```

<div class="normal-text-small" style="margin-top:14px;">

- `main.cpp` — contains `main()` and uses the functions.
- `mathutils.cpp` — contains the function definitions.
- `mathutils.h` — contains the function declarations (prototypes).

In `main.cpp`, include the header:

`#include "mathutils.h"`

</div>


---

# Project Layout: Larger Projects

<div class="normal-text-small">

For **larger programs**, header files and source files are often organized into separate directories.

</div>

<div class="code-title" style="margin-top:4px;">Larger project structure</div>

```text
project/
├── include/
│   └── mathutils.h
└── src/
    ├── main.cpp
    └── mathutils.cpp
```

<div class="normal-text-small" style="margin-top:10px;">

- `include/` — stores header files (`.h`).
- `src/` — stores source files (`.cpp`).
- This organization makes larger projects easier to maintain.

The build system can be configured to search the `include/` directory, allowing:

`#include "mathutils.h"`

</div>

---

# Build Systems

<div class="normal-text-small">

A **build system** automates the process of turning C++ source files into an executable program.

- **Compile** — converts each `.cpp` file into an object file.
- **Link** — combines object files and libraries into the final executable.
- **Track dependencies** — rebuilds affected files when the source code changes.
- **Manage configuration** — handles compiler options and libraries.

</div>

<div class="code-title" style="margin-top:12px;">Without a build system</div>

```bash
g++ main.cpp mathutils.cpp -o app
```

<div class="normal-text-small" style="margin-top:12px;">

For a small program, compiling manually is easy.

As a project grows, a **build system manages these commands automatically**.

Common C++ build tools include **CMake** and **Make**.

</div>


---

# Build System Configuration

<div class="definition-box">
A build system needs <strong>instructions</strong> that describe how the project should be built.

</div>

<div class="normal-text-small" style="margin-top:20px;">

- Which `.cpp` files should be compiled
- Which libraries should be linked
- Where header files are located
- What executable should be created

These instructions are usually stored in a **configuration file**.

</div>

---

# Build System Configuration: CMake

<div class="normal-text-small">

**CMake** is a commonly used build system for C++ projects.

Its build instructions are typically stored in a file named `CMakeLists.txt`.

</div>

<div class="code-title" style="margin-top:10px;">Example: CMakeLists.txt</div>

```cmake
cmake_minimum_required(VERSION 3.20)

project(MyProgram)

add_executable(MyProgram
    main.cpp
    mathutils.cpp
)
```

<div class="normal-text-small" style="margin-top:10px;">

CMake reads `CMakeLists.txt` and uses it to configure the project.

**CLion uses CMake** when you build and run a C++ project.

</div>

---

<div class="flex justify-center mt-4">
  <img
    src="/images/build-systems.png"
    alt="Real-world uses of functions in C++"
    class="max-h-[450px] rounded-lg"
  />
</div>


---

# Run C++ Programs Without a Build System

<div class="normal-text-small">

For a multi-file C++ project, we can manually **compile, link, and run** the program.

</div>

<div class="code-title" style="margin-top:8px;">Project structure</div>

```text
project/
├── include/
│   └── mathutils.h
└── src/
    ├── main.cpp
    └── add.cpp
```

<div class="normal-text-small" style="margin-top:8px;">

### Step 1: Compile → Create Object Files

Each `.cpp` file is compiled separately into an **object file**.

</div>

```bash
g++ -c src/main.cpp -I include -o main.o
g++ -c src/add.cpp  -I include -o add.o
```

<div class="normal-text-small" style="margin-top:5px;">

- `-c` → compile without linking
- `-I include` → search `include/` for header files
- Creates → `main.o` and `add.o`

**After compilation:** `.cpp` → `.o`

</div>

---

# Link and Run the Program

<div class="normal-text-small">

After compilation, the object files must be **linked** together to create the executable.

### Step 2: Link → Create Executable

</div>

```bash
g++ main.o add.o -o app
```

<div class="normal-text-small" style="margin-top:6px;">

- `main.o` and `add.o` are the object files
- `-o app` names the executable `app`

### Step 3: Run the Program

</div>

```bash
./app
```

<div class="normal-text-small" style="margin-top:8px;">

### Complete Build Process

`.cpp` files → `.o` files → executable → run

A **build tool automates the compile and link steps** so we do not have to enter each command manually.

</div>

---

# Why Use Multi-Step Compilation?

<div class="normal-text-small compact">

Large C++ projects may contain **hundreds of `.cpp` files**.

- Each `.cpp` file can be compiled separately into an **object file (`.o`)**.
- If only `add.cpp` changes, we can recompile just that source file.

</div>

```bash
g++ -c src/add.cpp -I include -o add.o
```

<div class="normal-text-small compact">

- The unchanged object files do **not** need to be recompiled.
- The object files are then linked again to create the executable.

</div>

```bash
g++ main.o add.o -o app
```

<div class="normal-text-small compact">

**Benefit:** For large projects, rebuilding only what changed can make compilation much faster.

Build tools automate this process by tracking **dependencies** and rebuilding what is necessary.

</div>


---


# Function Documentation

<div class="normal-text-small compact">

Function documentation explains **what a function does** and how it should be used.

**<span v-tooltip="'You can find more information at https://www.doxygen.nl'">Doxygen 💬</span>** is a tool that can generate documentation from specially formatted comments in C++ source code.

Common Doxygen commands include:

- `@brief` → provides a short description of the function
- `@param` → describes a function parameter
- `@return` → describes the value returned by the function

Good documentation helps programmers understand and maintain code without examining every detail of the implementation.

</div>

---

# Documenting a Function with Doxygen

<div class="code-title" style="margin-top:8px;">Documentation of a function</div>

```cpp
/**
 * @brief Adds two integers.
 *
 * Adds two integer values and returns their sum.
 *
 * @param a First integer.
 * @param b Second integer.
 * @return The sum of a and b.
 */
int add(int a, int b) {
    return a + b;
}
```

<div class="normal-text-small compact" style="margin-top:10px;">

- `@param a` documents the parameter `a`
- `@param b` documents the parameter `b`
- `@return` documents the value returned by `return a + b`

Doxygen can process these comments and generate formatted documentation such as **HTML pages**.

</div>


---

# Function documentation output

<div class="flex justify-center mt-4">
  <img
    src="/images/documentation.png"
    alt="Real-world uses of functions in C++"
    class="max-h-[450px] rounded-lg"
  />
</div>

---

# How Doxygen Works

<div class="normal-text-small compact">

**Doxygen** is a stand-alone documentation generator and does not depend on a specific IDE.

- Reads specially formatted comments from C++ source files.
- Extracts information about functions, parameters, and return values.
- Generates organized documentation, commonly as **HTML**.

</div>

<div class="code-title" style="margin-top:8px;">Documentation workflow</div>

```text
C++ Source Code  →  Doxygen  →  Generated Documentation
```

<div class="normal-text-small compact" style="margin-top:8px;">

Some IDEs provide **Doxygen integration**, but Doxygen itself works independently.


</div>

---

# Communication b/w Functions

<div class="normal-text-small compact">

When one function calls another function, data can be passed from the **calling function** to the **called function**.

### Calling Function

The function that makes the function call.

```cpp
int result = add(a, b);
```

- `main()` may be the **calling function**.
- `add(a, b)` is the **function call**.
- `a` and `b` are **arguments** passed to the called function.

### Called Function

The function that receives the call and performs the task.

```cpp
int add(int x, int y)
```

- `add()` is the **called function**.
- `x` and `y` are **parameters** that receive the arguments.

</div>

---

# Communication b/w Functions: Returning a Result

<div class="normal-text-small compact">

The called function can perform a task and send a value back to the **calling function**.

```cpp
int add(int x, int y) {
    return x + y;
}
```

The statement ```return x + y;``` sends the result back to the calling function.

The value returned by ```add(a, b)``` is stored in ```result```.    

### Communication Flow

**Calling Function → Arguments → Called Function → Return Value → Calling Function**

Arguments can be passed to parameters in two common ways:

- **Pass by Value**
- **Pass by Reference**

</div>



---

# Passing Arguments by Value

<div class="normal-text-small compact">

In **pass by value**, the value of each argument is **copied** into the corresponding parameter.

### Calling Function

```cpp
int x = 10;
int y = 5;
int result = add(x, y);
```

- `x` and `y` are **arguments**. Their values are passed to the called function.

### Called Function

```cpp
int add(int a, int b) {
    return a + b;
}
```

- `a` and `b` are **parameters**.
- `a` receives a copy of `x` → `10`
- `b` receives a copy of `y` → `5`

</div>

---

# Pass by Value: What Gets Copied?

<div class="normal-text-small compact">

With **pass by value**, the value of each argument is copied into a separate parameter.

```cpp
int x = 10;
int y = 5;

changeValues(x, y);
```

When the function is called:

`x = 10` → **copy** → `a = 10`

`y = 5` → **copy** → `b = 5`

The parameters `a` and `b` are **separate variables** from the arguments `x` and `y`.

**Key Point:** The function works with copies of the original values.

</div>

---

# Pass by Value: Changing the Parameters

<div class="normal-text-small compact">

Changing the parameters affects only the **copies**.

```cpp
void changeValues(int a, int b) {
    a = 20;
    b = 30;
}
int main() {
    int x = 10;
    int y = 5;
    changeValues(x, y);
    cout << x << " " << y;
    return 0;
}
```

### Output

```text
10 5
```

Although `a` and `b` changed inside the function, `x` and `y` remain unchanged.

**Key Point:** Pass by value does **not** allow the function to modify the original arguments.

</div>


---

# Passing Arguments by Value

<div class="grid grid-cols-2 gap-6">

<div>

<div class="code-title" style="margin-top:4px;">Pass by value</div>
<div class="scroll-code" style="--code-height:380px;">

```cpp
#include <iostream>
using namespace std;

int add(int a, int b);

int main() {
    int result{}, x{10}, y{15};

    result = add(x, y);

    cout << "The address of x is "
         << &x << endl;
    cout << "The address of y is "
         << &y << endl;
    cout << "The result is "
         << result << endl;
    return 0;
}

int add(int a, int b) {
    cout << "The address of a is "
         << &a << endl;
    cout << "The address of b is "
         << &b << endl;

    return a + b;
}
```

</div>
</div>

<div>

<div class="code-title" style="margin-top:4px;">Example Output</div>

```text
The address of a is 0x7ffee16238cc
The address of b is 0x7ffee16238c8
The address of x is 0x7ffee16238e4
The address of y is 0x7ffee16238e0
The result is 25
```

<div class="normal-text-small compact" style="margin-top:0px; font-size:0.9rem;">

When `add(x, y)` is called:

- The **value** of `x` (`10`) is copied into `a`.
- The **value** of `y` (`15`) is copied into `b`.
- `a` and `b` are separate variables from `x` and `y`.

**Same values → different variables → different memory locations**

</div>

<div class="definition-box" style="margin-top:12px !important; font-size:0.9rem !important; line-height:1.35 !important;">

Memory addresses shown here are examples. The actual addresses may be different each time the program runs.

</div>

</div>

</div>


---

# Passing Arguments by Value — Benefits

<div class="normal-text-small compact">

- The function receives a **copy** of the argument's value.
- Changes to the parameter do **not** affect the original variable.
- Simple and efficient for small types such as `int`, `double`, `char`, and `bool`.

</div>

<div class="definition-box" style="margin-top:16px !important; font-size:1.6rem !important;">
<strong>Benefit:</strong> The function can work with the value without modifying the caller's variable.
</div>

---

# Passing Arguments by Value — When to Use It

<div class="normal-text-small compact">

Use **pass by value** when:

- The function should **not modify** the original variable.
- The value is **small and inexpensive to copy**.

### Example

```cpp
int square(int number) {
    return number * number;
}

int x = 5;
int result = square(x);
```

After the call:

`x = 5` &nbsp;&nbsp;&nbsp; `result = 25`

</div>

<div class="definition-box" style="margin-top:20px !important; font-size:1.6rem !important;">
Think of it like a <strong>photocopy</strong>: changing the copy does not change the original.
</div>

---

# Passing Arguments by Reference

<div class="definition-box" style="margin-top:12px !important; font-size:1.5rem !important;">

<p style="line-height:1.6 !important; margin:0 !important;">
When an argument is passed by reference, the parameter becomes an <strong>alias</strong> for the original variable rather than receiving a copy.
</p>

</div>

<div class="normal-text-small compact" style="margin-top:18px;">

### How does C++ indicate a reference parameter?

The ampersand (`&`) in the parameter declaration indicates that the parameter is a **reference**.

</div>

<div class="grid grid-cols-2 gap-8" style="margin-top:10px;">

<div>

<div class="code-title" style="margin-top:0;">Reference parameters</div>

```cpp
int add(int &a, int &b);  // declaration

int add(int &a, int &b) { // definition
    return a + b;
}
```

</div>

<div class="normal-text-small compact" style="font-size:1.15rem !important; margin-top:8px;">

- `a` refers to the original argument.
- `b` refers to the original argument.
- No separate parameter copy is created as with pass by value.
- Changes to `a` or `b` can change the caller's variables.

</div>

</div>



---

# Passing Arguments by Reference — Verification

<div class="normal-text-small compact">

Reference parameters are **aliases** for the original arguments.

We can verify this by comparing their memory addresses.

</div>

<div class="code-title" style="margin-top:8px;">Passing arguments by reference</div>

<div class="scroll-code" style="--code-height:300px;">

```cpp
#include <iostream>
using namespace std;

int add(int &a, int &b);

int main() {
    int result{}, x{10}, y{15};

    result = add(x, y);

    cout << "The address of x is "
         << &x << endl;
    cout << "The address of y is "
         << &y << endl;
    cout << "The result is "
         << result << endl;

    return 0;
}

int add(int &a, int &b) {
    cout << "The address of a is "
         << &a << endl;
    cout << "The address of b is "
         << &b << endl;

    return a + b;
}
```

</div>

---


# Pass by Reference — What Does the Output Show?

<div class="grid grid-cols-2 gap-8">

<div>

<div class="code-title" style="margin-top:4px;">Example Output</div>

```text
The address of a is 0x7ffee772f8e4
The address of b is 0x7ffee772f8e0
The address of x is 0x7ffee772f8e4
The address of y is 0x7ffee772f8e0
The result is 25
```

<div class="definition-box" style="margin-top:12px !important; font-size:1.4rem !important;">

<p style="line-height:1.5 !important; margin:0 !important;">
Memory addresses shown are examples. The actual addresses may differ each time the program runs.
</p>

</div>

</div>

<div class="normal-text-small compact" style="font-size:1.15rem !important; margin-top:8px;">

When `add(x, y)` is called:

- `a` becomes an **alias for `x`**.
- `b` becomes an **alias for `y`**.

Therefore:

`&a == &x`

`&b == &y`

The matching addresses show that each reference parameter refers to the **same object** as its corresponding argument.

</div>

</div>


---

# Passing Arguments by Reference — Benefits

<div class="normal-text-small compact">

### Modify the Original Variable

- The function can directly modify the caller's variable.
- Useful when changes must remain after the function returns.

### Avoid Expensive Copies

- A reference provides access to the original object without copying it.
- Useful for larger objects such as `string`, `vector`, and class objects.

### Output Through Parameters

- A function can modify multiple reference parameters.
- This allows several results to be sent back through **output parameters**.

</div>

<div class="definition-box" style="margin-top:16px !important; font-size:1.4rem !important;">

<p style="line-height:1.6 !important; margin:0 !important;">
Think of it as working with the <strong>original document</strong>: changes made through the reference affect the original.
</p>

</div>


---

# C++ Reference Syntax — Important Note

<div class="normal-text-small compact">

Both styles are valid and mean exactly the same thing:

</div>

<div class="grid grid-cols-2 gap-8" style="margin-top:8px;">

<div>

<div class="code-title" style="margin-top:0;">Style 1</div>

```cpp
int& a = x;
```

<div class="normal-text-small compact" style="font-size:1.1rem !important;">

`a` is a reference to an `int`.

</div>

</div>

<div>

<div class="code-title" style="margin-top:0;">Style 2</div>

```cpp
int &a = x;
```

<div class="normal-text-small compact" style="font-size:1.1rem !important;">

`a` is also a reference to an `int`.

</div>

</div>

</div>

<div class="definition-box" style="margin-top:10px !important; font-size:1.2rem !important;">

<p style="line-height:1.4 !important; margin:0 !important;">
Spacing around <code>&</code> does not change the meaning.
</p>

</div>

<div class="code-title" style="margin-top:12px;">Be careful with multiple declarations</div>

```cpp
int &a = x, b = y;     // a is a reference, b is an int

int &a = x, &b = y;    // both a and b are references
```

<div class="normal-text-small compact" style="margin-top:8px;">

**Best practice:** Declare one variable per line when using references or pointers.

```cpp
int &a = x;
int &b = y;
```

</div>

---

# Variable Scope

<div class="normal-text-small compact">

**Scope** determines where a variable name can be used. C++ begins looking for a name in the **current scope**.

</div>

<div style="display:grid; grid-template-columns:1.2fr 0.8fr; gap:24px; margin-top:10px;">

<div>

<div class="code-title" style="margin-top:0;">1. Local scope</div>

```cpp
#include <iostream>
using namespace std;

int x = 100;          // global x

int main() {
    int x = 50;       // local x

    cout << x;        // prints 50
    return 0;
}
```

</div>

<div>

<div class="code-title" style="margin-top:0;">What happens?</div>

<div class="normal-text-small compact" style="font-size:1.1rem !important;">

- Two variables are named `x`.
- C++ first finds `x` inside `main()`.
- `cout << x` therefore uses the **local `x`**.
- The local `x` **shadows** the global `x`.

</div>

<div class="definition-box" style="margin-top:14px !important; font-size:1.2rem !important;">
The closest visible declaration is used.
</div>

</div>

</div>

---

# Variable Scope — Enclosing Scope

<div class="normal-text-small compact">

If a name is not found in the current block, C++ continues searching in the **enclosing (outer) scope**.

</div>

<div style="display:grid; grid-template-columns:1.2fr 0.8fr; gap:24px; margin-top:10px;">

<div>

<div class="code-title" style="margin-top:0;">2. Enclosing scope</div>

```cpp
#include <iostream>
using namespace std;

int main() {
    int x = 50;          // enclosing scope

    {
        int y = 20;      // current scope

        cout << x << endl;
        cout << y << endl;
    }

    return 0;
}
```

</div>

<div>

<div class="code-title" style="margin-top:0;">Inside the inner block</div>

<div class="normal-text-small compact" style="font-size:1.1rem !important;">

- `y` is declared in the **current block**.
- `x` is not declared in the current block.
- C++ searches outward.
- `x` is found in the **enclosing scope** of `main()`.

</div>

<div class="definition-box" style="margin-top:14px !important; font-size:1.2rem !important;">
Name lookup proceeds outward one scope at a time.
</div>

</div>

</div>

---

# Variable Scope — Global Scope

<div class="normal-text-small compact">

A variable declared outside all functions has **global scope** and may be used where it is visible.

</div>

<div style="display:grid; grid-template-columns:1.2fr 0.8fr; gap:24px; margin-top:10px;">

<div>

<div class="code-title" style="margin-top:0;">3. Global scope</div>

```cpp
#include <iostream>
using namespace std;

int x = 100;           // global x

void showValue() {
    cout << x << endl;
}

int main() {
    showValue();
    cout << x << endl;

    return 0;
}
```

</div>

<div>

<div class="code-title" style="margin-top:0;">What happens?</div>

<div class="normal-text-small compact" style="font-size:1.1rem !important;">

- `x` is declared outside all functions.
- `showValue()` has no local `x`.
- `main()` also has no local `x`.
- Both therefore use the **global `x`**.

</div>

<div class="definition-box" style="margin-top:14px !important; font-size:1.2rem !important;">
Current scope → enclosing scope(s) → global scope
</div>

</div>

</div>

---

# The `extern` Keyword

<div class="normal-text-small-compact">

- A global variable should have **one definition** in the program.
- Another `.cpp` file can access the same variable using an `extern` declaration.
- `extern` **does not create a new variable** — both files refer to the same object.

</div>

<div class="definition-box" style="margin-top:14px !important; font-size:1.3rem !important; line-height:1.4 !important;">
<code>extern</code> declares a variable that is defined elsewhere in the program.
</div>

<div class="code-title" style="margin-top:12px;">
Sharing a global variable between source files
</div>

<style>
.slidev-code-group pre {
  max-height: 180px !important;
}

</style>
::code-group

```cpp [main.cpp]
#include <iostream>
using namespace std;

extern int counter; // counter is defined in test.cpp
void test();        // test() is defined in test.cpp

int main() {
    cout << counter << endl;
    counter++;

    cout << counter << endl;
    cout << "Memory address of counter: "
         << &counter << endl;

    test();

    return 0;
}
```

```cpp [test.cpp]
#include <iostream>
using namespace std;

int counter = 10;

void test() {
    cout << "Memory address of counter: "
         << &counter << endl;
}
```

```text [Output]
10
11
Memory address of counter: 0x10bd900c0
Memory address of counter: 0x10bd900c0

Process finished with exit code 0
```

::

---

# ℹ️ `extern` and Functions

<div class="definition-box" style="margin-top:18px !important; font-size:1.4rem !important; line-height:1.45 !important;">
Functions normally have external linkage in C++, so the <code>extern</code> keyword is usually unnecessary in a function declaration.
</div>

<div class="normal-text-small" style="line-height:1.3; margin-top:18px;">

- A function can be **defined in one `.cpp` file** and called from another.
- Only the function **declaration** is needed before the call.
- Writing `extern` is valid, but normally redundant.

</div>

::code-group

```cpp [main.cpp]
#include <iostream>
using namespace std;

extern int add(int, int);  // not necessary, but valid

int main() {
    cout << add(3, 4) << endl;
    return 0;
}
```

```cpp [file1.cpp]
int add(int a, int b) {
    return a + b;
}
```

::

---

# Life of a Variable

<div class="normal-text-small" style="line-height:1.3;">

Every variable has two important characteristics:

- **Scope** — where the variable can be accessed.
- **Lifetime** — how long the variable exists.

</div>

<div class="definition-box" style="margin-top:20px !important; font-size:1.35rem !important; line-height:1.4 !important;">
Scope tells us <strong>where</strong> a variable can be used. Lifetime tells us <strong>how long</strong> it exists.
</div>

<div class="normal-text-small" style="line-height:1.3; margin-top:22px;">

For local variables, we will compare:

- **Automatic local variables** — start fresh each time.
- **Static local variables** — remember their value.

</div>

---

# Automatic Local Variables

<div class="normal-text-small" style="line-height:1.3;">

An ordinary local variable normally has **automatic storage duration**.

- Created when execution reaches its declaration.
- Destroyed when execution leaves its block.
- Scope is limited to its block.
- A new variable is created each time the declaration is executed.

</div>

<div class="code-title" style="margin-top:16px;">Automatic Variable</div>

```cpp
void foo() {
    int x = 0;
    x++;
    cout << x << endl;
}
```

<div class="definition-box" style="margin-top:18px !important; font-size:1.3rem !important; line-height:1.4 !important;">
When <code>foo()</code> ends, <code>x</code> is destroyed. The next call creates a new <code>x</code>.
</div>

---

# Automatic Variables — Example

<div class="normal-text-small" style="line-height:1.3;">

Calling `foo()` three times creates a new `x` on every call.

</div>

::code-group

```cpp [Program]
#include <iostream>
using namespace std;

void foo() {
    int x = 0;
    x++;
    cout << x << endl;
}

int main() {
    foo();
    foo();
    foo();

    return 0;
}
```

```text [Output]
1
1
1
```

::

<div class="definition-box" style="margin-top:14px !important; font-size:1.3rem !important; line-height:1.4 !important;">
Each call starts with a new <code>x = 0</code>, so the output is always <code>1</code>.
</div>

---

# Static Local Variables

<div class="normal-text-small" style="line-height:1.3;">

A local variable declared with `static` behaves differently.

- Its scope is still **local** to the block.
- It is initialized only **once**.
- It exists until the program ends.
- Its value is preserved between executions of the block.

</div>

<div class="code-title" style="margin-top:16px;">Static Variable</div>

```cpp
void foo() {
    static int x = 0;
    x++;
    cout << x << endl;
}
```

::div{class="definition-box" style="margin-top:18px !important; font-size:1.3rem !important; line-height:1.4 !important;"}
`static` changes the lifetime of `x`, but `x` still has local scope.
::
---

# Static Variables — Example

<div class="normal-text-small" style="line-height:1.3;">

Calling `foo()` again uses the **same `x`** from the previous call.

</div>

::code-group

```cpp [Program]
#include <iostream>
using namespace std;

void foo() {
    static int x = 0;
    x++;
    cout << x << endl;
}

int main() {
    foo();
    foo();
    foo();

    return 0;
}
```

```text [Output]
1
2
3
```

::

::div{class="definition-box" style="margin-top:14px !important; font-size:1.3rem !important; line-height:1.4 !important;"}
`x` remembers its previous value: `0 → 1 → 2 → 3`.
::

---

# Automatic vs. Static Variables

<table class="memory-table" style="margin-top:20px;">
  <thead>
    <tr>
      <th>Property</th>
      <th>Automatic Local</th>
      <th>Static Local</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Declaration</td>
      <td><code>int x = 0;</code></td>
      <td><code>static int x = 0;</code></td>
    </tr>
    <tr>
      <td>Scope</td>
      <td>Local</td>
      <td>Local</td>
    </tr>
    <tr>
      <td>Initialization</td>
      <td>Each execution</td>
      <td>Once</td>
    </tr>
    <tr>
      <td>Lifetime</td>
      <td>Until block exits</td>
      <td>Until program ends</td>
    </tr>
    <tr>
      <td>Value preserved?</td>
      <td>No</td>
      <td>Yes</td>
    </tr>
  </tbody>
</table>

<div class="definition-box" style="margin-top:20px !important; font-size:1.35rem !important; line-height:1.4 !important;">
Automatic → <strong>starts fresh</strong> &nbsp;&nbsp; | &nbsp;&nbsp; Static → <strong>remembers</strong>
</div>

---

# A Note About `auto`

<div class="normal-text-small" style="line-height:1.3;">

The term **automatic variable** does not mean that we normally use the `auto` keyword.

In modern C++, `auto` is primarily used for **type deduction**:

</div>

```cpp
int x = 10;       // x is an int

auto y = 10;      // compiler deduces int
auto price = 9.5; // compiler deduces double
```

::div{class="definition-box" style="margin-top:14px !important; font-size:1.4rem !important; line-height:1.4 !important;"}
`auto` determines a variable's type. It does not mean “make this an automatic local variable.”
::


---

# Memory Layout of a C++ Program

::div{class="definition-box" style="margin-top:14px !important; font-size:1.3rem !important; line-height:1.4 !important;"}
A running program commonly uses different memory regions for different types of data and program activity.
::

<div class="code-title" style="margin-top:20px;">Simplified Memory Layout</div>

```text
+--------------------------------------------------+
|                 CODE / TEXT                      |
|          Compiled program instructions           |
+--------------------------------------------------+
|              INITIALIZED DATA                    |
|       Initialized global/static objects          |
+--------------------------------------------------+
|                     BSS                          |
|     Zero-initialized global/static objects       |
+--------------------------------------------------+
|                     HEAP                         |
|            Dynamically allocated objects         |
|                       ↑                          |
|                                                  |
|                       ↓                          |
|                     STACK                        |
|       Function calls and many local variables    |
+--------------------------------------------------+
```

::div{class="definition-box" style="margin-top:14px !important; font-size:1.05rem !important; line-height:1.3 !important;"}
This is a simplified conceptual model. The exact memory layout depends on the platform and implementation.
::

---

# C++ Memory Regions

::div{class="normal-text-small compact" style="line-height:1.3;"}
- **Code / Text** — contains the compiled program instructions.
- **Initialized Data** — typically contains initialized global and static objects.
- **BSS** — typically contains zero-initialized global and static objects.
- **Heap** — commonly used for dynamically allocated objects.
- **Stack** — commonly used for function calls and many local variables.
::

::div{class="code-title" style="margin-top:5px;"}
Example
::

::div{class="scroll-code" style="--code-height:150px;"}
```cpp
int globalCount = 10;      // initialized data
static int total;          // typically BSS

int main() {
    int score = 90;        // typically stack
    int* ptr = new int(5); // dynamically allocated object
                             // typically heap
    delete ptr;
    return 0;
}
```
::
::div{class="definition-box" style="margin-top:14px !important; font-size:1.2rem !important; line-height:1.35 !important;"}
C++ defines **storage duration and object lifetime**; it does not require these objects to occupy specific physical memory regions.
::



---

# Heap vs. Stack

::div{class="normal-text-small" style="line-height:1.3;"}
The key difference is **how the memory is obtained and how its lifetime is managed**.
::

<table class="memory-table" style="margin-top:18px;">
  <thead>
    <tr>
      <th>Stack</th>
      <th>Heap</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Associated with function execution</td>
      <td>Used for dynamic allocation</td>
    </tr>
    <tr>
      <td>Many local variables</td>
      <td>Dynamically created objects</td>
    </tr>
    <tr>
      <td>Managed automatically</td>
      <td>Lifetime controlled explicitly</td>
    </tr>
    <tr>
      <td>Typically released when a function returns</td>
      <td>Released with <code>delete</code> when using <code>new</code></td>
    </tr>
  </tbody>
</table>

::div{class="definition-box" style="margin-top:18px !important; font-size:1.2rem !important; line-height:1.3 !important;"}
A local variable may disappear when its function returns, while a dynamically allocated object can continue to exist until it is explicitly destroyed.
::

---

# Memory Layout — Putting It Together

::div{class="normal-text-small" style="line-height:1.3;"}
Use the program below to connect each C++ declaration with its typical memory region: **Code/Text, Data, BSS, Stack, or Heap**.
::

::div{class="code-title" style="margin-top:10px;"}
Typical Storage Locations
::

::div{class="scroll-code" style="--code-height:300px;"}

```cpp
#include <iostream>
using namespace std;

int globalValue = 10;       // Initialized Data
static int globalCount;     // BSS

void hello() {              // Code / Text
    int local = 5;          // typically Stack
    static int count = 30;  // Initialized Data

    int* ptr = new int(40);
    // ptr  → typically Stack
    // *ptr → typically Heap

    cout << globalValue << " "
         << globalCount << " "
         << local << " "
         << count << " "
         << *ptr << endl;

    delete ptr;
}

int main() {                // Code / Text
    hello();
    return 0;
}
```

::

::div{class="definition-box" style="margin-top:12px !important; font-size:1.15rem !important; line-height:1.3 !important;"}
`ptr` and `*ptr` are not the same object: `ptr` is the local pointer variable, while `*ptr` refers to the dynamically allocated `int`.
::



---

# Function Overloading

::div{class="definition-box" style="margin-top:18px !important; font-size:1.35rem !important; line-height:1.4 !important;"}
**Function overloading** allows several functions to share the **same name** as long as their parameter lists are different.
::

::div{class="normal-text-small" style="line-height:1.3; margin-top:15px;"}
**Why use function overloading?**

When several functions perform the **same general task**, we can give them the same meaningful name instead of creating a different name for every data type.
::

<div class="grid grid-cols-2 gap-6" style="margin-top:12px;">

<div>

::div{class="code-title" style="margin-top:0px;"}
Without Overloading
::

```cpp
void displayInt(int value);
void displayDouble(double value);
void displayString(string value);
```

</div>

<div>

::div{class="code-title" style="margin-top:0px;"}
With Overloading
::

```cpp
void display(int value);
void display(double value);
void display(string value);
```

</div>

</div>

::div{class="definition-box" style="margin-top:14px !important; font-size:1.4rem !important; line-height:1.3 !important;"}
One operation → one meaningful function name → multiple parameter lists.
::


---

# Selecting an Overloaded Function

::div{class="normal-text-small" style="line-height:1.3;"}
When an overloaded function is called, the compiler examines the **arguments** and selects the best matching function.
::

<div class="grid grid-cols-2 gap-6" style="margin-top:16px;">

<div>

::div{class="code-title" style="margin-top:0px;"}
Available Functions
::

```cpp
void display(int value);
void display(double value);
void display(const string& value);
```

</div>

<div>

::div{class="code-title" style="margin-top:0px;"}
Function Calls
::

```cpp
display(10);              // display(int)

display(3.14);            // display(double)

display(string("Hello")); // display(string)
```

</div>

</div>

::div{class="definition-box" style="margin-top:16px !important; font-size:1.4rem !important; line-height:1.35 !important;"}
The compiler determines which overloaded function to call during **compilation**.
::

---

# Function Overloading — Example

::div{class="normal-text-small" style="line-height:1.3;"}
Here, `display()` performs the same general task for different types of values.
::

::div{class="code-title" style="margin-top:10px;"}
Displaying Different Data Types
::

::div{class="scroll-code" style="--code-height:290px;"}

```cpp
#include <iostream>
#include <string>
using namespace std;

void display(int value) {
    cout << "Integer: " << value << endl;
}

void display(double value) {
    cout << "Double: " << value << endl;
}

void display(const string& value) {
    cout << "String: " << value << endl;
}

int main() {
    display(10);
    display(3.14);
    display(string("Hello"));

    return 0;
}
```

::

::div{class="definition-box" style="margin-top:12px !important; font-size:1.4rem !important; line-height:1.3 !important;"}
The function name remains `display()`. The **argument type** determines which version is selected.
::

---

# Rules of Function Overloading

::div{class="normal-text-small" style="line-height:1.25;"}
Functions with the same name can be overloaded by changing their **parameter lists**.
::

::div{class="code-title" style="margin-top:14px;"}
Different Number of Parameters
::

```cpp
void calculate(int x);
void calculate(int x, int y);
```

::div{class="code-title" style="margin-top:12px;"}
Different Parameter Types
::

```cpp
void calculate(int x);
void calculate(double x);
```

::div{class="code-title" style="margin-top:12px;"}
Different Order of Parameter Types
::

```cpp
void calculate(int x, double y);
void calculate(double x, int y);
```

::div{class="definition-box" style="margin-top:14px !important; font-size:1.4rem !important; line-height:1.3 !important;"}
The compiler must be able to distinguish the functions from their **parameter lists**.
::

---

# What Cannot Be Overloaded?

::div{class="normal-text-small" style="line-height:1.3;"}
The **return type alone** cannot distinguish overloaded functions.
::

::div{class="code-title" style="margin-top:16px;"}
Invalid
::

```cpp
int calculate(int x);

double calculate(int x);   // ERROR
```

::div{class="normal-text-small" style="line-height:1.3; margin-top:18px;"}
Both functions have exactly the same parameter list:

`calculate(int)`

Consider this call:
::

```cpp
calculate(10);
```

::div{class="normal-text-small" style="line-height:1.3; margin-top:14px;"}
The argument `10` does not tell the compiler which return type the programmer wants.
::

::div{class="definition-box" style="margin-top:14px !important; font-size:1.2rem !important; line-height:1.35 !important;"}
**Same name + different parameter list = valid overloading.**
::


---

# Rules of Function Overloading

::div{class="normal-text-small" style="line-height:1.35;"}
Overloaded functions have the **same name** but different parameter lists.

Functions can be overloaded by changing:

- **Number of parameters**
- **Types of parameters**
- **Order of parameter types**
::

::div{class="definition-box" style="margin-top:22px !important; font-size:1.25rem !important; line-height:1.4 !important;"}
The compiler must be able to distinguish overloaded functions from their **parameter lists**.
::

---

# Overloading — Number of Parameters

::div{class="normal-text-small" style="line-height:1.3;"}
Functions can have the same name when they accept a **different number of parameters**.
::

::div{class="code-title" style="margin-top:14px;"}
Example
::

::div{class="scroll-code" style="--code-height:290px;"}

```cpp
#include <iostream>
using namespace std;

void print(int x) {
    cout << "One value: " << x << endl;
}

void print(int x, int y) {
    cout << "Two values: "
         << x << ", " << y << endl;
}

int main() {
    print(5);        // calls print(int)
    print(10, 20);   // calls print(int, int)

    return 0;
}
```
::
::div{class="definition-box" style="margin-top:14px !important; font-size:1.15rem !important; line-height:1.3 !important;"}
`print(5)` has one argument, while `print(10, 20)` has two. The compiler selects the matching overload.
::

---

# Overloading — Parameter Types

::div{class="normal-text-small" style="line-height:1.3;"}
Functions can also be overloaded when their parameters have **different types**.
::

::div{class="code-title" style="margin-top:14px;"}
Example
::

```cpp
#include <iostream>
using namespace std;

void print(int x) {
    cout << "Integer: " << x << endl;
}
void print(double x) {
    cout << "Double: " << x << endl;
}

int main() {
    print(42);      // calls print(int)
    print(3.14);    // calls print(double)
    return 0;
}
```

::div{class="definition-box" style="margin-top:14px !important; font-size:1.15rem !important; line-height:1.3 !important;"}
The argument type helps determine which overload is the best match.
::

---

# Overloading — Order of Parameter Types

::div{class="normal-text-small" style="line-height:1.3;"}
Functions can be overloaded when the **sequence of parameter types** is different.
::

::div{class="code-title" style="margin-top:14px;"}
Example
::

```cpp
#include <iostream>
using namespace std;

void print(int x, char y) {
    cout << "Int, Char: "
         << x << ", " << y << endl;
}
void print(char x, int y) {
    cout << "Char, Int: "
         << x << ", " << y << endl;
}
int main() {
    print(5, 'A');    // calls print(int, char)
    print('B', 10);   // calls print(char, int)
    return 0;
}
```

::div{class="definition-box" style="margin-top:14px !important; font-size:1.15rem !important; line-height:1.3 !important;"}
`(int, char)` and `(char, int)` are different parameter lists.
::

---

# Return Type and Function Overloading

::div{class="normal-text-small" style="line-height:1.3;"}
The **return type alone** cannot be used to overload a function.
::

::div{class="code-title" style="margin-top:16px;"}
Invalid
::

```cpp
int calculate(int x);

double calculate(int x);   // ERROR
```

::div{class="normal-text-small" style="line-height:1.3; margin-top:18px;"}
Both functions have exactly the same parameter list:

`calculate(int)`

Consider this call:
::

```cpp
calculate(10);
```

::div{class="normal-text-small" style="line-height:1.3; margin-top:14px;"}
The argument provides no information that would allow the compiler to choose between the two return types.
::

::div{class="definition-box" style="margin-top:14px !important; font-size:1.2rem !important; line-height:1.35 !important;"}
**Return type alone does not create a different overload.**
::


---

# Ambiguity in Function Overloading

::div{class="definition-box" style="margin-top:16px !important; font-size:1.3rem !important; line-height:1.4 !important;"}
An overloaded function call is **ambiguous** when the compiler finds multiple valid overloads but cannot select one as the **best match**.
::

<div class="grid grid-cols-2 gap-8" style="margin-top:18px;">

<div>

::div{class="code-title" style="margin-top:0px;"}
Example
::

```cpp
void test(int x);
void test(float x);

int main() {
    test(5.0);    // ERROR: ambiguous

    return 0;
}
```

</div>

<div>

::div{class="code-title" style="margin-top:0px;"}
Why Is It Ambiguous?
::

::div{class="normal-text-small" style="font-size:1.05rem; line-height:1.3;"}
`5.0` is a `double`, but there is no `test(double)` overload.

The compiler considers both overloads:

- `test(int)` → requires `double` → `int`
- `test(float)` → requires `double` → `float`

Both are valid **standard conversions**, and neither overload is a better match.
::

</div>

</div>

::div{class="definition-box" style="margin-top:18px !important; font-size:1.15rem !important; line-height:1.3 !important;"}
No single best match → **ambiguous call → compilation error**
::

---

# Resolving the Ambiguity

::div{class="normal-text-small" style="line-height:2;"}
We can resolve the ambiguity by giving the compiler a clear **best match**.
::

::code-group

```cpp [1 - Match the Parameter Type]
void test(int x);
void test(double x);

int main() {
    test(5.0);    // calls test(double)

    return 0;
}
```

```cpp [2 - Match the Argument Type]
void test(int x);
void test(float x);

int main() {
    test(5.0f);   // calls test(float)

    return 0;
}
```

```cpp [3 - Explicit Conversion]
void test(int x);
void test(float x);

int main() {
    test(static_cast<float>(5.0));
    // calls test(float)

    return 0;
}
```

::

::div{class="normal-text-small" style="line-height:1.3; margin-top:18px;"}
**Solution 1:** Change the overload to accept `double`.

**Solution 2:** Use `5.0f` so the argument is a `float`.

**Solution 3:** Explicitly convert the argument to `float`.
::

::div{class="definition-box" style="margin-top:14px !important; font-size:1.4rem !important; line-height:1.3 !important;"}
In each solution, the compiler can identify **one best matching overload**.
::



---

# Functions with Default Parameters

::div{class="definition-box" style="margin-top:16px !important; font-size:1.3rem !important; line-height:1.4 !important;"}
A **default parameter** has a default value that is used when the caller does not provide the corresponding argument.
::

::div{class="normal-text-small" style="font-size:1.1rem; line-height:1.3; margin-top:18px;"}
Default values allow the same function to be called with **different numbers of arguments**.
::

::div{class="code-title" style="margin-top:18px;"}
Example
::

```cpp
void greet(string name = "Guest", int times = 1);
```

::div{class="normal-text-small" style="font-size:1.1rem; line-height:1.3; margin-top:18px;"}
All of these calls are valid:
::

```cpp
greet();                     // use both defaults

greet("Miramar College");    // use default times = 1

greet("San Diego, CA", 3);   // provide both arguments
```

::div{class="definition-box" style="margin-top:16px !important; font-size:1.15rem !important; line-height:1.3 !important;"}
An explicitly supplied argument **replaces the default** for that parameter.
::

---

# How Default Parameters Work

::div{class="normal-text-small" style="font-size:1.1rem; line-height:1.3;"}
Arguments correspond to parameters **from left to right**. Omitted trailing arguments use their default values.
::

<div class="grid grid-cols-2 gap-8" style="margin-top:18px;">

<div>

::div{class="code-title" style="margin-top:0px;"}
Function Declaration
::

```cpp
void greet(
    string name = "Guest",
    int times = 1
);
```

</div>

<div>

::div{class="code-title" style="margin-top:0px;"}
Function Calls
::

```cpp
greet();
// name  = "Guest"
// times = 1
```

```cpp
greet("Miramar");
// name  = "Miramar"
// times = 1
```

```cpp
greet("San Diego", 3);
// name  = "San Diego"
// times = 3
```

</div>

</div>

::div{class="definition-box" style="margin-top:16px !important; font-size:1.4rem !important; line-height:1.3 !important;"}
Only **trailing arguments** can be omitted.
::

---

# Default Parameters — Complete Example

::div{class="normal-text-small" style="font-size:1.05rem; line-height:1.3;"}
One function can support several calling patterns by providing default values.
::

::code-group

```cpp [Program]
#include <iostream>
#include <string>
using namespace std;

void greet(string name = "Guest", int times = 1) {
    for (int i = 0; i < times; i++) {
        cout << "Hello, " << name << "!" << endl;
    }
}

int main() {
    greet();
    greet("Miramar College");
    greet("San Diego, CA", 3);

    return 0;
}
```

```text [Output]
Hello, Guest!
Hello, Miramar College!
Hello, San Diego, CA!
Hello, San Diego, CA!
Hello, San Diego, CA!
```

::

::div{class="definition-box" style="margin-top:14px !important; font-size:1.3rem !important; line-height:1.3 !important;"}
Default parameters provide **optional arguments** without requiring a separate function for each calling pattern.
::

---

# Rules for Default Parameters

::div{class="normal-text-small" style="font-size:1.05rem; line-height:1.25;"}
Once a parameter has a default value, every parameter to its **right must also have a default value**.
::

<div class="grid grid-cols-2 gap-6" style="margin-top:8px;">

<div>

::div{class="code-title" style="margin-top:0px;"}
Valid
::

```cpp
// Only the last parameter has a default
void greet(string name, int times = 1);

// Both parameters have defaults
void greet(string name = "Guest",
           int times = 1);
```

</div>

<div>

::div{class="code-title" style="margin-top:0px;"}
Invalid
::

```cpp
// A required parameter cannot
// follow a default parameter
void greet(string name = "Guest",
           int times);   // ERROR
```

</div>

</div>

::div{class="code-title" style="margin-top:8px;"}
Using the Defaults
::

```cpp
greet();                 // "Guest", 1
greet("Danish");         // "Danish", 1
greet("Danish", 3);      // "Danish", 3
```

::div{class="normal-text-small" style="font-size:1rem; line-height:1.2; margin-top:8px;"}
You can omit arguments only from the **right side** of the argument list. You cannot skip `name` and provide only `times`.
::

::div{class="definition-box" style="margin-top:10px !important; font-size:1.4rem !important; line-height:1.25 !important;"}
Default parameters must form a **contiguous group at the end** of the parameter list.
::

---

# Where Should Default Values Be Specified?

::div{class="normal-text-small" style="font-size:1.1rem; line-height:1.3;"}
When a function has a separate declaration and definition, default values are typically placed in the **function declaration**.
::

<div class="grid grid-cols-2 gap-8" style="margin-top:18px;">

<div>

::div{class="code-title" style="margin-top:0px;"}
Function Declaration
::

```cpp
void greet(
    string name = "Guest",
    int times = 1
);
```

</div>

<div>

::div{class="code-title" style="margin-top:0px;"}
Function Definition
::

```cpp
void greet(
    string name,
    int times
) {
    // function body
}
```

</div>

</div>

::div{class="normal-text-small" style="font-size:1.05rem; line-height:1.3; margin-top:18px;"}
Do **not** repeat the same default values in both places:
::

```cpp
void greet(string name = "Guest", int times = 1);

// ERROR: defaults repeated
void greet(string name = "Guest", int times = 1) {
    // function body
}
```

::div{class="definition-box" style="margin-top:14px !important; font-size:1.15rem !important; line-height:1.3 !important;"}
Specify a default argument **once** where it is visible to the caller—commonly in the function declaration.
::



---

# ⚠️ Default Parameters — Declaration Rules

::div{class="normal-text" style="font-size:1.2rem; line-height:1.25; margin-bottom:25px;"}
Default arguments must follow specific rules when a function is declared.
::

::code-group

```cpp [Rule 1 - Defaults on the Right]
// Once a parameter has a default,
// all parameters to its right must
// also have defaults.

void foo(int x, int y = 10);      // OK

void foo(int x = 5, int y);       // ERROR

void foo(int x = 5, int y = 10);  // OK
```

```cpp [Rule 2 - Do Not Repeat]
// Default specified in the declaration

void foo(int x = 10);

// Do not repeat it in the definition
void foo(int x) {
    // function body
}
```

```cpp [Rule 2 - Incorrect]
// ERROR: the default for x
// has already been specified

void foo(int x = 10);

void foo(int x = 10) {
    // function body
}
```

::

::div{class="definition-box" style="margin-top:18px !important; font-size:1.1rem !important; line-height:1.3 !important;"}
**Rule 1:** Defaults must form a group on the right.  
**Rule 2:** Do not repeat a default argument that has already been specified.
::

---

# ⚠️ Default Parameters — No Skipping

::div{class="normal-text-small" style="font-size:1.05rem; line-height:1.25; margin-bottom:18px;"}
Arguments correspond to parameters **from left to right**. You may omit only **trailing arguments** that have default values.
::

<div class="grid grid-cols-2 gap-8">

<div>

::div{class="code-title" style="margin-top:0px;"}
Function Declaration
::

```cpp
void bookTicket(
    string name,
    string seat = "Middle",
    string meal = "Veg"
);
```

::div{class="code-title" style="margin-top:12px;"}
Valid Calls
::

```cpp
bookTicket("Tiger");
// seat = "Middle"
// meal = "Veg"

bookTicket("Tiger", "Window");
// meal = "Veg"

bookTicket("Tiger", "Window", "Vegan");
// all arguments supplied
```

</div>

<div>

::div{class="code-title" style="margin-top:0px;"}
Invalid Call
::

```cpp
bookTicket(
    "Tiger",
    ,
    "Vegan"
);  // ERROR
```

::div{class="normal-text-small" style="font-size:1rem; line-height:1.25; margin-top:16px;"}
Here, the programmer is trying to:

- provide `name`
- skip `seat`
- provide `meal`

C++ does **not** allow an argument to be skipped in the middle of the argument list.
::

::div{class="definition-box" style="margin-top:20px !important; font-size:1.05rem !important; line-height:1.25 !important;"}
❌ You cannot create a **hole** in the argument list.
::

</div>

</div>

::div{class="definition-box" style="margin-top:16px !important; font-size:1.1rem !important; line-height:1.25 !important;"}
Default arguments may be omitted only from the **right end** of the argument list.
::

---

# Default Parameters — Omitting Arguments

::div{class="normal-text-small" style="font-size:1.05rem; line-height:1.25; margin-bottom:20px;"}
Arguments correspond to parameters **from left to right**. Trailing arguments with default values may be omitted.
::

<div class="grid grid-cols-2 gap-8">

<div>

::div{class="code-title" style="margin-top:0px;"}
Function Declaration
::

```cpp
void bookTicket(
    string name,
    string seat = "Middle",
    string meal = "Veg"
);
```

::div{class="normal-text-small" style="font-size:1rem; line-height:1.25; margin-top:18px;"}
`name` is **required**.

`seat` and `meal` are **optional** because they have default values.
::

</div>

<div>

::div{class="code-title" style="margin-top:0px;"}
Use Both Defaults
::

```cpp
bookTicket("Tiger");
```

::div{class="normal-text-small" style="font-size:1rem; line-height:1.25; margin-top:16px;"}
The call provides only `name`.

Therefore:

`name` → `"Tiger"`  
`seat` → `"Middle"`  
`meal` → `"Veg"`
::

</div>

</div>

::div{class="definition-box" style="margin-top:20px !important; font-size:1.4rem !important; line-height:1.25 !important;"}
A parameter without a default value is **required**. Trailing parameters with defaults are **optional**.
::

---

# Default Parameters — Overriding Defaults

::div{class="normal-text-small" style="font-size:1.05rem; line-height:1.25; margin-bottom:20px;"}
Providing an argument **overrides the default value** for the corresponding parameter.
::

<div class="grid grid-cols-2 gap-8">

<div>

::div{class="code-title" style="margin-top:0px;"}
Override One Default
::

```cpp
bookTicket(
    "Tiger",
    "Window"
);
```

::div{class="normal-text-small" style="font-size:1rem; line-height:1.25; margin-top:16px;"}
`name` → `"Tiger"`  
`seat` → `"Window"`  
`meal` → `"Veg"`

Only `meal` uses its default.
::

</div>

<div>

::div{class="code-title" style="margin-top:0px;"}
Override Both Defaults
::

```cpp
bookTicket(
    "Tiger",
    "Window",
    "Vegan"
);
```

::div{class="normal-text-small" style="font-size:1rem; line-height:1.25; margin-top:16px;"}
`name` → `"Tiger"`  
`seat` → `"Window"`  
`meal` → `"Vegan"`

No default values are used.
::

</div>

</div>

::div{class="definition-box" style="margin-top:20px !important; font-size:1.4rem !important; line-height:1.25 !important;"}
Default values are used only when the corresponding **trailing arguments are omitted**.
::


---

# 🔍 Debugging Functions

::div{class="normal-text" style="font-size:1.15rem; line-height:1.2; margin-bottom:16px;"}
When a function does not work as expected, debug it **step by step**.
::

<div class="grid grid-cols-2 gap-8">

<div>

::div{class="code-title" style="margin-top:0px;"}
1 — Check the Function Call
::

::div{class="normal-text-small" style="font-size:1rem; line-height:1.25;"}
- Correct function name?
- Correct arguments?
- Correct overload selected?
::

::div{class="code-title" style="margin-top:14px;"}
2 — Check the Declaration
::

::div{class="normal-text-small" style="font-size:1rem; line-height:1.25;"}
- Declared before the call?
- Signature matches the definition?
::

</div>

<div>

::div{class="code-title" style="margin-top:0px;"}
3 — Check the Function Body
::

::div{class="normal-text-small" style="font-size:1rem; line-height:1.25;"}
- Parameters used correctly?
- Logic produces the expected result?
::

::div{class="code-title" style="margin-top:14px;"}
4 — Check the Return
::

::div{class="normal-text-small" style="font-size:1rem; line-height:1.25;"}
- Correct value returned?
- Return type correct?
::

</div>

</div>

::div{class="definition-box" style="margin-top:16px !important; font-size:1.4rem !important; line-height:1.25 !important;"}
Debug systematically:

**Function Call → Declaration → Function Body → Return**
::


---

# Lecture Summary — Function Fundamentals

::div{class="normal-text" style="font-size:1.15rem; line-height:1.25; margin-bottom:18px;"}
Functions divide a program into **smaller, focused, and reusable tasks**.
::

<div class="grid grid-cols-2 gap-8">

<div>

::div{class="code-title" style="margin-top:0px;"}
Creating Functions
::

::div{class="normal-text-small" style="font-size:1.05rem; line-height:1.35;"}
- A **declaration** introduces a function.
- A **definition** provides its implementation.
- Parameters receive values from arguments.
- Functions can return a value or use `void`.
::

</div>

<div>

::div{class="code-title" style="margin-top:0px;"}
Passing Data
::

::div{class="normal-text-small" style="font-size:1.05rem; line-height:1.35;"}
- **Pass by value** gives the function a copy.
- **Pass by reference** gives access to the original object.
- Use references when modification or avoiding a copy is appropriate.
::

</div>

</div>

::div{class="definition-box" style="margin-top:22px !important; font-size:1.4rem !important; line-height:1.3 !important;"}
A function should have a **clear purpose, clear inputs, and a predictable result**.
::

---

# Lecture Summary — Scope & Lifetime

::div{class="normal-text" style="font-size:1.15rem; line-height:1.25; margin-bottom:18px;"}
Variables used by functions differ in **where they can be accessed** and **how long they exist**.
::

<div class="grid grid-cols-2 gap-8">

<div>

::div{class="code-title" style="margin-top:0px;"}
Scope
::

::div{class="normal-text-small" style="font-size:1.05rem; line-height:1.35;"}
- Local names are visible within their scope.
- A local variable can **shadow** a global variable.
- `::` can explicitly access a global name when it is shadowed.
- `extern` can declare an object defined in another source file.
::

</div>

<div>

::div{class="code-title" style="margin-top:0px;"}
Lifetime
::

::div{class="normal-text-small" style="font-size:1.05rem; line-height:1.35;"}
- Ordinary local variables are recreated when their block is entered.
- Static local variables preserve their values between function calls.
- Global and static objects have program-long storage duration.
::

</div>

</div>

::div{class="definition-box" style="margin-top:22px !important; font-size:1.4rem !important; line-height:1.3 !important;"}
**Scope** determines where a name can be used; **lifetime** determines how long an object exists.
::

---

# Lecture Summary — Flexible & Reliable Functions

::div{class="normal-text" style="font-size:1.15rem; line-height:1.25; margin-bottom:18px;"}
C++ provides several features for making functions more flexible while keeping their interfaces clear.
::

<div class="grid grid-cols-2 gap-8">

<div>

::div{class="code-title" style="margin-top:0px;"}
Function Overloading
::

::div{class="normal-text-small" style="font-size:1.05rem; line-height:1.35;"}
- Functions may share a name when their parameter lists differ.
- The compiler selects the **best matching overload**.
- Ambiguous calls result in compilation errors.
- Return type alone cannot distinguish overloads.
::

</div>

<div>

::div{class="code-title" style="margin-top:0px;"}
Default Parameters
::

::div{class="normal-text-small" style="font-size:1.05rem; line-height:1.35;"}
- Default values allow trailing arguments to be omitted.
- Explicit arguments override their defaults.
- Required parameters must appear before defaulted parameters.
- Arguments cannot be skipped in the middle.
::

</div>

</div>

::div{class="definition-box" style="margin-top:22px !important; font-size:1.4rem !important; line-height:1.3 !important;"}
Well-designed functions make programs easier to **read, reuse, test, debug, and maintain**.
::

---

<div class="definition-box">
Design each function to perform one clear task, with well-defined inputs and a predictable result.
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
  question="Q1. Which statement best describes a function in C++?"
  :options="[
    'A named block of code designed to perform a specific task',
    'A variable that stores several related values',
    'A file that contains only variable declarations',
    'A command used to compile a C++ program'
  ]"
  correct="A named block of code designed to perform a specific task"
  explanation="A function is a named block of code designed to perform a specific task. Functions help divide programs into smaller, reusable, and manageable pieces."
/>

---

<QuizQuestion
  question="Q2. In the function call `add(5, 10)`, what are 5 and 10?"
  :options="[
    'Parameters',
    'Arguments',
    'Return values',
    'Function declarations'
  ]"
  correct="Arguments"
  explanation="Arguments are the actual values supplied when a function is called. Parameters are the variables that receive those values."
/>

---

<QuizQuestion
  question="Q3. Why is a function declaration placed before a call when the function definition appears later?"
  :options="[
    'To tell the compiler about the function before it is used',
    'To execute the function before main()',
    'To create the function parameters in memory',
    'To automatically generate the function definition'
  ]"
  correct="To tell the compiler about the function before it is used"
  explanation="When a function is called before its definition appears, a declaration tells the compiler the function's return type, name, and parameter types."
/>

---

<QuizQuestion
  question="Q4. What is the main difference between a void function and a value-returning function?"
  :options="[
    'A void function does not return a value to the caller',
    'A void function cannot have parameters',
    'A value-returning function cannot have arguments',
    'A value-returning function cannot display output'
  ]"
  correct="A void function does not return a value to the caller"
  explanation="A void function performs an action without returning a value. A value-returning function sends a value back to its caller."
/>

---

<QuizQuestion
  question="Q5. What happens when an argument is passed by value?"
  :options="[
    'The argument value is copied into a separate parameter',
    'The parameter becomes an alias for the original variable',
    'The parameter and argument refer to the same object',
    'Changes to the parameter must change the original variable'
  ]"
  correct="The argument value is copied into a separate parameter"
  explanation="With pass by value, the function receives a copy of the argument's value. Changes to the parameter do not change the caller's original variable."
/>

---

<QuizQuestion
  question="Q6. What does the `&` indicate in the parameter `int &value`?"
  :options="[
    'value is a reference parameter',
    'value is an automatic local variable',
    'value is a global variable',
    'value is passed by value'
  ]"
  correct="value is a reference parameter"
  explanation="The & indicates that value is a reference parameter. It becomes an alias for the caller's original variable rather than receiving a separate copy."
/>

---

<QuizQuestion
  question="Q7. Which statement correctly distinguishes scope from lifetime?"
  :options="[
    'Scope describes where a name can be used; lifetime describes how long the object exists',
    'Scope describes how long an object exists; lifetime describes where its name can be used',
    'Scope applies only to local variables; lifetime applies only to global variables',
    'Scope and lifetime describe the same property'
  ]"
  correct="Scope describes where a name can be used; lifetime describes how long the object exists"
  explanation="Scope determines where a variable name can be accessed. Lifetime determines how long the corresponding object exists."
/>

---

<QuizQuestion
  question="Q8. Which pair represents valid function overloading?"
  :options="[
    '`void print(int x); and void print(double x);`',
    '`int print(int x); and double print(int x);`',
    '`void print(int x); and void print(int value);`',
    '`int print(double x); and void print(double x);`'
  ]"
  correct="`void print(int x); and void print(double x);`"
  explanation="Overloaded functions have the same name but different parameter lists. Changing the parameter type creates a valid overload. Return type or parameter names alone cannot distinguish overloads."
/>

---

<QuizQuestion
  question="Q9. Why is `test(5.0)` ambiguous when the available overloads are `test(int)` and `test(float)`?"
  :options="[
    '5.0 is a double and neither overload is a better match',
    'A function cannot be overloaded using int and float parameters',
    '5.0 is an integer literal',
    'Overloaded functions cannot perform type conversions'
  ]"
  correct="5.0 is a double and neither overload is a better match"
  explanation="The literal 5.0 is a double. Both double-to-int and double-to-float conversions are possible, but neither overload provides a single best match."
/>

---

<QuizQuestion
  question="Q10. Given `void greet(string name = &quot;Guest&quot;, int times = 1)`, what happens when `greet(&quot;Miramar&quot;)` is called?"
  :options="[
    'name becomes Miramar and times uses its default value of 1',
    'name uses Guest and times becomes Miramar',
    'Both parameters use their default values',
    'The call is invalid because both arguments are required'
  ]"
  correct="name becomes Miramar and times uses its default value of 1"
  explanation="Arguments correspond to parameters from left to right. Miramar replaces the default for name, while the omitted trailing argument causes times to use its default value of 1."
/>

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

