---
theme: dracula
background: https://cover.sli.dev
title: User-defined data types, namespaces & strings
author: Dr Danish Khan
transition: fade-out
mdc: true

---

# User-defined data types, namespaces & strings


Dr. Danish Khan | dkhan@sdccd.edu


Press Space for next page

---

# Learning Outcomes

::div{class="normal-text-small" style="font-size:1.3rem; line-height:1.6;"}

By the end of this lecture, you should be able to:

- Define and use **enumerations (`enum`)** and **type aliases**.
- Use **namespaces** and the scope resolution operator `::`.
- Explain and use **C-style strings** and **`std::string`**.
- Compare C-style strings with `std::string`.
- Use common **`std::string` operations and member functions**.

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

# Why User-Defined Data Types?

::div{class="definition-box" style="margin-top:14px !important; font-size:1.2rem !important; line-height:1.35 !important;"}
User-defined data types (UDTs) allow programmers to create meaningful types that model concepts beyond C++'s built-in types.
::

::div{class="normal-text-small" style="font-size:1.15rem; line-height:1.45; margin-top:20px;"}

C++ provides built-in types such as `int`, `char`, `float`, and `double`. However, these types alone may not clearly represent the **meaning and structure** of data in a program.

User-defined data types allow us to:

- **Represent** real-world concepts more naturally.
- **Group** related data and values.
- **Improve** code readability and organization.
- **Reduce** errors by giving data a clear meaning and structure.

::

::div{class="definition-box" style="margin-top:20px !important; font-size:1.15rem !important; line-height:1.35 !important;"}
Instead of working only with raw values, we can create types that describe what those values represent.
::
---

# User-Defined Data Types in C++

::div{class="normal-text-small" style="font-size:1.1rem; line-height:1.4;"}

| Type | Purpose | Example |
|---|---|---|
| `struct` | Group related data into one type | `struct Student { ... };` |
| `class` | Combine data and behavior with controlled access | `class BankAccount { ... };` |
| `enum` | Represent a fixed set of named values | `enum Color { RED, GREEN, BLUE };` |
| `union` | Store different members in the same memory location | `union Data { int i; float f; };` |

::

::div{class="definition-box" style="margin-top:18px !important; font-size:1.1rem !important; line-height:1.35 !important;"}
`struct`, `class`, `enum`, and `union` can define new types. `typedef` and `using` give existing types alternative names.
::

---

# Enumeration Type

::div{class="normal-text-small" style="font-size:1.15rem; line-height:1.45;"}

::div{class="definition-box" style="margin-top:14px !important; font-size:1.2rem !important; line-height:1.35 !important;"}
An enumeration (`enum`) is a user-defined data type that represents a fixed set of named values.
::

```cpp
enum TypeName {
    value1,
    value2,
    value3
};
```

- `TypeName` is the name of the new enumeration type.
- `value1`, `value2`, and `value3` are identifiers called **enumerators**.
- Each enumerator is associated with an **integral value**.
- By default, the first enumerator has the value `0`, and each subsequent value increases by `1`.

::div{class="definition-box" style="margin-top:14px !important; font-size:1.2rem !important; line-height:1.35 !important;"}
Enums make code easier to **read, understand, and maintain** by replacing unexplained numeric values with meaningful names.
::
::

---

# Basic Enum and Default Values

::div{class="normal-text-small" style="font-size:1.1rem; line-height:1.4;"}

An enum defines a new type with a fixed set of named values.

::div{style="max-height:250px; overflow-y:auto;"}
```cpp
#include <iostream>
using namespace std;

enum Day {
    MON,
    TUE,
    WED,
    THU,
    FRI,
    SAT,
    SUN
};

int main() {
    Day weekDay = MON;

    cout << weekDay << endl;   // 0

    weekDay = WED;

    cout << weekDay << endl;   // 2

    return 0;
}
```
::

- By default, the first enumerator has the value `0`.
- Each following enumerator increases by `1`.
- Enumerator names are case-sensitive: `MON` and `mon` are different identifiers.

::

::div{class="definition-box" style="margin-top:14px !important; font-size:1.1rem !important; line-height:1.35 !important;"}
`MON`, `TUE`, and `WED` are meaningful names associated with integral values.
::

---

# Enumerator Names and Scope

::div{class="normal-text-small" style="font-size:1.1rem; line-height:1.4;"}

Traditional enums are unscoped, so their enumerator names become visible in the surrounding scope.

```cpp
enum MathStudent {
    JOHN,
    PATEL,
    KHAN,
    HUANG,
    KAI
};

enum StatStudent {
    JENNI,
    KAI,       // Error: KAI already exists
    SARAH,
    MATT
};
```

Both enums attempt to define `KAI` in the same scope, causing a naming conflict.

::

::div{class="definition-box" style="margin-top:14px !important; font-size:1.1rem !important; line-height:1.35 !important;"}
Enumerator names in an unscoped `enum` must be unique within the surrounding scope.
::

---

# Declaring Enum Variables

::div{class="normal-text-small" style="font-size:1.1rem; line-height:1.4;"}

Enum variables can be declared after the enum definition, just like variables of other types.

::div{style="max-height:250px; overflow-y:auto;"}
```cpp
#include <iostream>
using namespace std;

enum MathStudent {
    JOHN,
    PATEL,
    KHAN,
    HUANG,
    KAI
};

int main() {
    MathStudent math = PATEL;

    cout << math << endl;   // 1

    math = KAI;

    cout << math << endl;   // 4

    return 0;
}
```
::

The variable `math` has type `MathStudent` and stores one of the values defined by that enum.

::

::div{class="definition-box" style="margin-top:14px !important; font-size:1.1rem !important; line-height:1.35 !important;"}
An enum variable represents one value from the set defined by its enumeration type.
::

---

# Assigning Custom Enum Values

::div{class="normal-text-small" style="font-size:1.1rem; line-height:1.4;"}

Enumerator values can be assigned explicitly.

::div{style="max-height:200px; overflow-y:auto;"}
```cpp
#include <iostream>
using namespace std;

enum Color {
    RED = 10,
    GREEN = 20,
    BLUE = 30
};

int main() {
    Color selected = GREEN;

    cout << selected << endl;   // 20

    return 0;
}
```
::

Values do not have to start at `0` or increase by `1`.

```cpp
enum Status {
    SUCCESS = 200,
    NOT_FOUND = 404,
    SERVER_ERROR = 500
};
```

::

::div{class="definition-box" style="margin-top:14px !important; font-size:1.1rem !important; line-height:1.35 !important;"}
Enum values can be assigned explicitly when the program requires specific integral values.
::


---

# Type Aliases: `typedef` and `using`

::div{class="definition-box" style="margin-top:14px !important; font-size:1.2rem !important; line-height:1.35 !important;"}
A type alias gives an existing data type another name. It does not create a new data type.
::

<div class="grid grid-cols-2 gap-8 mt-5">

::div{class="normal-text-small" style="font-size:1.1rem; line-height:1.4;"}

### `typedef`

Traditional C++ syntax for creating a type alias.

```cpp
typedef ExistingType AliasName;
```

Example:

```cpp
typedef int Integer;

Integer age = 25;
```

`Integer` is another name for `int`.

::

::div{class="normal-text-small" style="font-size:1.1rem; line-height:1.4;"}

### `using`

Modern C++ syntax for creating a type alias.

```cpp
using AliasName = ExistingType;
```

Example:

```cpp
using Integer = int;

Integer age = 25;
```

`Integer` is another name for `int`.

::

</div>

::div{class="definition-box" style="margin-top:14px !important; font-size:1.2rem !important; line-height:1.35 !important;"}
Both forms create the same kind of alias. In modern C++, **`using` is generally preferred** because its syntax is clearer and works more naturally with templates.
::

---

# Namespaces

::div{class="definition-box" style="margin-top:14px !important; font-size:1.2rem !important; line-height:1.35 !important;"}
A namespace groups related identifiers—such as variables, functions, classes, and enums—under a named scope and helps prevent naming conflicts.
::

::div{class="grid grid-cols-2 gap-8 mt-5"}

::div{class="normal-text-small" style="font-size:1.1rem; line-height:1.4;"}

### Why Use Namespaces?

Large programs may contain identifiers with the **same name**.

Namespaces allow those identifiers to coexist by placing them in different named scopes.

Common uses include:

- **Organizing** related code
- **Preventing** naming conflicts
- **Separating** components or libraries

::

::div{class="normal-text-small" style="font-size:1.1rem; line-height:1.4;"}

### Example

```cpp
namespace Student {
    void display();
}

namespace Faculty {
    void display();
}
```

Both namespaces contain a function named `display()`, but they do not conflict because they belong to different namespaces.

::

::

::div{class="definition-box" style="margin-top:16px !important; font-size:1.1rem !important; line-height:1.35 !important;"}
Namespaces allow the same identifier to exist in different named scopes without causing a conflict.
::

---

# Accessing Namespaces with `::`

::div{class="definition-box" style="margin-top:14px !important; font-size:1.2rem !important; line-height:1.35 !important;"}
The scope resolution operator `::` is used to access an identifier inside a namespace.
::

::div{class="grid grid-cols-2 gap-8 mt-5"}

::div{class="normal-text-small" style="font-size:0.9rem; line-height:1.4;"}

### Accessing Names

```cpp
Student::display();
Faculty::display();
```

The namespace name appears before `::`.

```text
namespace :: identifier
```

This tells C++ exactly which identifier to use.

For example:

- `Student::display()` → `display()` in `Student`
- `Faculty::display()` → `display()` in `Faculty`

::

::div{class="normal-text-small" style="font-size:1.1rem; line-height:1.4;"}

### Complete Example

::div{style="max-height:300px; overflow-y:auto;"}
```cpp
#include <iostream>

namespace Student {
    void display() {
        std::cout << "Student\n";
    }
}

namespace Faculty {
    void display() {
        std::cout << "Faculty\n";
    }
}

int main() {
    Student::display();
    Faculty::display();

    return 0;
}
```
::

::

::

::div{class="definition-box" style="margin-top:16px !important; font-size:1.1rem !important; line-height:1.35 !important;"}
`Student::display()` and `Faculty::display()` are different functions even though they have the same function name.
::

---

# The `std` Namespace

::div{class="definition-box" style="margin-top:14px !important; font-size:1.2rem !important; line-height:1.35 !important;"}
The C++ Standard Library places its identifiers inside the `std` namespace.
::

::div{class="grid grid-cols-2 gap-8 mt-1"}

::div{class="normal-text-small" style="font-size:1.1rem; line-height:1.4;"}

### Using `std::`

You have already used many identifiers from `std`:

```cpp
std::cout
std::cin
std::string
std::endl
```

Example:

```cpp
std::string name;
std::cout << "Enter name: ";
std::cin >> name;
```

Using `std::` clearly shows where an identifier comes from.

::

::div{class="normal-text-small" style="font-size:1.1rem; line-height:1.4;"}

### Using `using namespace std`

Instead of repeatedly writing `std::`:

```cpp
using namespace std;
string name;
cout << "Enter name: ";
cin >> name;
```

This makes all names from `std` directly accessible.

In larger programs, explicitly using `std::` is generally preferred because it helps **avoid naming conflicts**.

::div{class="definition-box" style="margin-top:16px !important; font-size:1.1rem !important; line-height:1.35 !important;"}
`std::cout` means `cout` from the `std` namespace. The `::` operator is the scope resolution operator.
::

::

---

# Namespace Example

::div{class="normal-text-small-compact"}

- Two functions with the **same name and parameter list** cannot be defined in the same scope.
- Namespaces place identifiers into separate **named scopes**.
- The scope resolution operator `::` identifies which namespace contains the function.

::

::div{class="definition-box" style="margin-top:14px !important; margin-bottom:20px !important; font-size:1.3rem !important; line-height:1.4 !important;"}
Namespaces allow the same identifier to be used in different scopes without causing a naming conflict.
::


<style>
.slidev-code-group pre {
  max-height: 200px !important;
}
</style>

::code-group

```cpp [Without a Namespace]
#include <iostream>

int draw() {
    return 1;
}

int draw() {       // Error: redefinition of draw()
    return 2;
}

int main() {
    std::cout << draw() << '\n';

    return 0;
}
```

```cpp [With a Namespace]
#include <iostream>

namespace graphics {
    int draw() {
        return 1;
    }
}

namespace printer {
    int draw() {
        return 2;
    }
}

int main() {
    std::cout << graphics::draw() << '\n';
    std::cout << printer::draw() << '\n';

    return 0;
}
```

::

---

# Strings

::div{class="definition-box" style="margin-top:14px !important; font-size:1.2rem !important; line-height:1.4 !important;"}
A string is a sequence of characters used to represent text, such as names, words, sentences, and messages.
::

::div{class="grid grid-cols-2 gap-8 mt-6"}

::div{class="normal-text-small" style="font-size:1.1rem; line-height:1.4;"}

### Sequence of Characters

A string contains individual characters arranged in a specific order.

For example:

```text
"Hello"
```

Each character has a **position (index)**, starting at `0`.

```text
Character: H  e  l  l  o
Index:     0  1  2  3  4
```

::

::div{class="normal-text-small" style="font-size:1.1rem; line-height:1.4;"}

### Strings in C++

C++ provides two common ways to work with strings:

**C-style strings**

```cpp
char name[] = "Alice";
```

C++ **`std::string`**

```cpp
std::string name = "Alice";
```

We will examine how these two approaches represent and manipulate text.

::

::

::div{class="definition-box" style="margin-top:20px !important; font-size:1.1rem !important; line-height:1.35 !important;"}
String indexing starts at `0`, so the first character is at index `0`.
::

---

# C-Style Strings

::div{class="definition-box" style="margin-top:14px !important; font-size:1.2rem !important; line-height:1.4 !important;"}
A C-style string is a character array terminated by a special null character `'\0'`.
::

::div{class="grid grid-cols-2 gap-8 mt-2"}

::div{class="normal-text-small" style="font-size:1.0rem; line-height:1.4;"}

### Character Array

A C-style string can be declared using a `char` array:

```cpp
char name[] = "Alice";
```

The array contains six characters:

```text
Character: A  l  i  c  e  \0
Index:     0  1  2  3  4   5
```

The null character `'\0'` marks the **end of the string**.

::

::div{class="normal-text-small" style="font-size:1.0rem; line-height:1.4;"}

### Things to Consider

When working with C-style strings, the programmer must pay attention to:

- **Array size**
- **Null termination**
- **Buffer boundaries**

For example:

```cpp
char name[6] = "Alice";
```

The array needs space for the five visible characters **plus `'\0'`**.

::

::

::div{class="definition-box" style="margin-top:0px !important; font-size:1.1rem !important; line-height:1.35 !important;"}
The null character `'\0'` occupies space in the array but is not part of the visible text.
::

---

# C++ `std::string`

::div{class="definition-box" style="margin-top:14px !important; font-size:1.2rem !important; line-height:1.4 !important;"}
`std::string` is a class provided by the C++ Standard Library for storing and manipulating sequences of characters.
::

::div{class="grid grid-cols-2 gap-8 mt-6"}

::div{class="normal-text-small" style="font-size:1.1rem; line-height:1.4;"}

### Creating and Accessing

Include the `<string>` header:

```cpp
#include <string>

std::string name = "Alice";
```

Characters can be accessed by index:

```cpp
std::cout << name[0];  // A
std::cout << name[1];  // l
```

`std::string` manages its storage automatically as its contents change.

::

::div{class="normal-text-small" style="font-size:1.1rem; line-height:1.4;"}

### Built-In Operations

`std::string` provides many operations for working with text:

```cpp
name.length();
```

```cpp
name.append(" Smith");
```

```cpp
name.insert(0, "Dr. ");
```

```cpp
name.erase(0, 4);
```

These operations allow strings to be manipulated without manually managing character arrays.

::

::

::div{class="definition-box" style="margin-top:20px !important; font-size:1.1rem !important; line-height:1.35 !important;"}
`std::string` provides a higher-level interface for creating, accessing, modifying, and managing text in C++.
::

---

# Common String Operations

::div{class="normal-text-small" style="font-size:1.1rem; line-height:1.4;"}

C-style strings use functions from `<cstring>`, while `std::string` uses operators and member functions.

<table style="width:100%; margin-top:20px; font-size:1.05rem;">
  <thead>
    <tr>
      <th style="text-align:left; padding:10px;">Operation</th>
      <th style="text-align:left; padding:10px;">C-Style String</th>
      <th style="text-align:left; padding:10px;">C++ <code>std::string</code></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="padding:10px;">Copy</td>
      <td style="padding:10px;"><code>strcpy(dest, src)</code></td>
      <td style="padding:10px;"><code>b = a</code></td>
    </tr>
    <tr>
      <td style="padding:10px;">Concatenate</td>
      <td style="padding:10px;"><code>strcat(a, b)</code></td>
      <td style="padding:10px;"><code>a += b</code></td>
    </tr>
    <tr>
      <td style="padding:10px;">Compare</td>
      <td style="padding:10px;"><code>strcmp(a, b)</code></td>
      <td style="padding:10px;"><code>a == b</code></td>
    </tr>
    <tr>
      <td style="padding:10px;">Length</td>
      <td style="padding:10px;"><code>strlen(a)</code></td>
      <td style="padding:10px;"><code>a.length()</code></td>
    </tr>
    <tr>
      <td style="padding:10px;">Find character</td>
      <td style="padding:10px;"><code>strchr(a, 'x')</code></td>
      <td style="padding:10px;"><code>a.find('x')</code></td>
    </tr>
  </tbody>
</table>

::

::div{class="definition-box" style="margin-top:20px !important; font-size:1.2rem !important; line-height:1.4 !important;"}
C-style strings rely mainly on functions from `<cstring>`, while `std::string` provides operators and member functions for working with text.
::

---

# Memory & Safety

::div{class="grid grid-cols-2 gap-8 mt-4"}

::div{class="normal-text-small" style="font-size:1.0rem !important; line-height:1.40 !important;"}

### C-Style Strings

- Characters are stored **contiguously** in a `char` array
- The array has a **fixed capacity**
- Must have enough room for the text and `'\0'`
- The programmer must track the available space
- Writing beyond the array boundary can cause a **buffer overflow**

```cpp
char name[10] = "Hello";
strcat(name, "!");
```

::

::div{class="normal-text-small" style="font-size:1.0rem; line-height:1.45;"}

### C++ `std::string`

- Characters are also stored **contiguously**
- The string **manages its own storage**
- Can grow as more characters are added
- No manual null-termination is required
- Reduces common buffer-management errors

```cpp
string name = "Hello";
name += "!";
```

::

::

::div{class="definition-box" style="margin-top:10px !important; font-size:1.2rem !important; line-height:1.4 !important;"}
Both C-style strings and `std::string` store their characters contiguously. The key difference is storage management: a character array has a fixed capacity, while `std::string` manages its capacity and can grow as needed.
::

---

# Summary of String Differences

::div{class="normal-text-small"}

<table style="width:100%; margin-top:12px; font-size:1.02rem; line-height:1.55; border-collapse:collapse;">
  <thead>
    <tr>
      <th style="text-align:left; padding:5px 10px;">Feature</th>
      <th style="text-align:left; padding:5px 10px;">C-Style String</th>
      <th style="text-align:left; padding:5px 10px;">C++ <code>std::string</code></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="padding:5px 10px;">Representation</td>
      <td style="padding:5px 10px;"><code>char</code> array</td>
      <td style="padding:5px 10px;"><code>std::string</code> class</td>
    </tr>
    <tr>
      <td style="padding:5px 10px;">Character storage</td>
      <td style="padding:5px 10px;">Contiguous</td>
      <td style="padding:5px 10px;">Contiguous</td>
    </tr>
    <tr>
      <td style="padding:5px 10px;">Capacity</td>
      <td style="padding:5px 10px;">Fixed for a declared array</td>
      <td style="padding:5px 10px;">Managed automatically</td>
    </tr>
    <tr>
      <td style="padding:5px 10px;">Resizing</td>
      <td style="padding:5px 10px;">Requires managing/replacing the buffer</td>
      <td style="padding:5px 10px;">Grows automatically as needed</td>
    </tr>
    <tr>
      <td style="padding:5px 10px;">Concatenation</td>
      <td style="padding:5px 10px;"><code>strcat()</code></td>
      <td style="padding:5px 10px;"><code>+</code> or <code>+=</code></td>
    </tr>
    <tr>
      <td style="padding:5px 10px;">Comparison</td>
      <td style="padding:5px 10px;"><code>strcmp()</code></td>
      <td style="padding:5px 10px;"><code>==</code>, <code>!=</code>, <code>&lt;</code>, etc.</td>
    </tr>
    <tr>
      <td style="padding:5px 10px;">Length</td>
      <td style="padding:5px 10px;"><code>strlen()</code></td>
      <td style="padding:5px 10px;"><code>.size()</code> or <code>.length()</code></td>
    </tr>
    <tr>
      <td style="padding:5px 10px;">Null terminator</td>
      <td style="padding:5px 10px;">Programmer must account for <code>'\0'</code></td>
      <td style="padding:5px 10px;">Managed automatically</td>
    </tr>
  </tbody>
</table>

::


---

# Where Does a `std::string` Live?

::div{class="normal-text-small-compact"}

A local `std::string` object has **automatic storage duration** and is typically stored in the function's **stack frame**.

```cpp
std::string name = "Hello";
```

The `std::string` **object** and the **characters it manages** are not necessarily stored in the same place.

::

::div{class="grid grid-cols-2 gap-12" style="margin-top:16px;"}

::div

### `std::string` Object

```text
Stack Frame

┌─────────────────────────┐
│                         │
│    std::string name     │
│                         │
└─────────────────────────┘
```

The object itself is typically stored in the function's stack frame.

::

::div

### Character Storage

```text
std::string name
       │
       │ manages
       ▼
  H  e  l  l  o
```

The characters are stored **contiguously**, but exactly where that storage resides depends on the implementation and the string's size.

::

::

::div{class="definition-box" style="margin-top:2px !important; font-size:1.0rem !important; line-height:1.2 !important;"}
**Key idea:** The `std::string` **object** and its **character storage** are related, but they are not the same thing.
::

---

# Where Are the Characters Stored?

::div{class="normal-text-small-compact"}

The characters in a `std::string` are stored **contiguously**, but the string manages where that storage comes from.

Many implementations use **Small String Optimization (SSO)** to avoid a separate memory allocation for short strings.

::

::div{class="grid grid-cols-2 gap-8" style="margin-top:18px;"}

::div

### Short String — SSO

**STACK**

<div style="border:2px solid #aaa; border-radius:4px; padding:18px 22px; height:145px; font-family:monospace;">

<p style="margin:0; font-size:1.05rem;">std::string name</p>

<p style="margin:26px 0 0 0; font-size:1.05rem;">H&nbsp;&nbsp;e&nbsp;&nbsp;l&nbsp;&nbsp;l&nbsp;&nbsp;o&nbsp;&nbsp;\0</p>

<p style="margin:4px 0 0 0; font-size:0.9rem;">character data</p>

</div>

::div{style="font-size:1.05rem; line-height:1.3; margin-top:12px;"}
With SSO, the characters are stored **inside the `std::string` object**. No separate dynamic allocation is needed.
::

::

::div

### When More Space Is Needed

::div{class="grid items-end" style="grid-template-columns:1fr 45px 1fr;"}

::div

**STACK**

<div style="border:2px solid #aaa; border-radius:4px; padding:18px; height:145px; font-family:monospace;">

<p style="margin:0; font-size:1rem;">std::string name</p>

<p style="margin:50px 0 0 0; font-size:0.82rem;">storage reference</p>

</div>

::

::div{style="height:145px; display:flex; align-items:center; justify-content:center; font-size:2rem;"}
→
::

::div

**HEAP**

<div style="border:2px solid #aaa; border-radius:4px; padding:18px; height:145px; font-family:monospace;">

<p style="margin:0; font-size:0.95rem;">H&nbsp;e&nbsp;l&nbsp;l&nbsp;o&nbsp;...&nbsp;\0</p>

<p style="margin:50px 0 0 0; font-size:0.82rem;">character data</p>

</div>

::

::

::div{style="font-size:1.05rem; line-height:1.3; margin-top:12px;"}
When more space is needed, the characters are typically stored in **heap (dynamic) storage**.
::

::

::


---

# Verifying Contiguous Memory

::div{class="normal-text-small-compact"}

Each character in a `std::string` occupies the next memory location. We can verify this by printing the **address of each character**.

::

<style>
.slidev-code-group pre {
  max-height: 285px !important;
}
</style>

::code-group

```cpp [Code]
#include <iostream>
#include <string>

int main() {
    std::string text = "Hello World";

    for (std::size_t i = 0; i < text.size(); ++i) {
        std::cout << "text[" << i << "] = '"
                  << text[i] << "'  Address: "
                  << static_cast<const void*>(&text[i])
                  << '\n';
    }

    return 0;
}
```

```text [Output]
text[0] = 'H'  Address: 0x7ffeec22a921
text[1] = 'e'  Address: 0x7ffeec22a922
text[2] = 'l'  Address: 0x7ffeec22a923
text[3] = 'l'  Address: 0x7ffeec22a924
text[4] = 'o'  Address: 0x7ffeec22a925
text[5] = ' '  Address: 0x7ffeec22a926
text[6] = 'W'  Address: 0x7ffeec22a927
text[7] = 'o'  Address: 0x7ffeec22a928
text[8] = 'r'  Address: 0x7ffeec22a929
text[9] = 'l'  Address: 0x7ffeec22a92a
text[10] = 'd' Address: 0x7ffeec22a92b
```

::

::div{class="definition-box" style="margin-top:16px !important; font-size:1.1rem !important; line-height:1.2 !important;"}
**Notice:** Each address increases by **1 byte** because a `char` occupies one byte. This demonstrates that the characters in a `std::string` are stored **contiguously**.
::

---

# Common `std::string` Member Functions

::div{class="normal-text-small-compact"}

Assume `std::string s = "Hello";`

::

::div{style="max-height:300px; overflow-y:auto; margin-top:12px;"}

<table style="width:100%; font-size:1.02rem; line-height:1.15; border-collapse:collapse;">
<thead>
<tr>
<th style="text-align:left; padding:7px 10px;">Function</th>
<th style="text-align:left; padding:7px 10px;">Purpose</th>
<th style="text-align:left; padding:7px 10px;">Example</th>
<th style="text-align:left; padding:7px 10px;">Result</th>
</tr>
</thead>
<tbody>
<tr>
<td style="padding:7px 10px;"><code>length()</code></td>
<td style="padding:7px 10px;">Number of characters</td>
<td style="padding:7px 10px;"><code>s.length()</code></td>
<td style="padding:7px 10px;"><code>5</code></td>
</tr>
<tr>
<td style="padding:7px 10px;"><code>size()</code></td>
<td style="padding:7px 10px;">Same as <code>length()</code></td>
<td style="padding:7px 10px;"><code>s.size()</code></td>
<td style="padding:7px 10px;"><code>5</code></td>
</tr>
<tr>
<td style="padding:7px 10px;"><code>at()</code></td>
<td style="padding:7px 10px;">Bounds-checked character access</td>
<td style="padding:7px 10px;"><code>s.at(1)</code></td>
<td style="padding:7px 10px;"><code>'e'</code></td>
</tr>
<tr>
<td style="padding:7px 10px;"><code>append()</code></td>
<td style="padding:7px 10px;">Add text to the end</td>
<td style="padding:7px 10px;"><code>s.append(" World")</code></td>
<td style="padding:7px 10px;"><code>"Hello World"</code></td>
</tr>
<tr>
<td style="padding:7px 10px;"><code>insert()</code></td>
<td style="padding:7px 10px;">Insert characters</td>
<td style="padding:7px 10px;"><code>s.insert(0, "Hi ")</code></td>
<td style="padding:7px 10px;"><code>"Hi Hello"</code></td>
</tr>
<tr>
<td style="padding:7px 10px;"><code>erase()</code></td>
<td style="padding:7px 10px;">Remove characters</td>
<td style="padding:7px 10px;"><code>s.erase(1, 2)</code></td>
<td style="padding:7px 10px;"><code>"Hlo"</code></td>
</tr>
<tr>
<td style="padding:7px 10px;"><code>replace()</code></td>
<td style="padding:7px 10px;">Replace characters</td>
<td style="padding:7px 10px;"><code>s.replace(0, 2, "Y")</code></td>
<td style="padding:7px 10px;"><code>"Yllo"</code></td>
</tr>
<tr>
<td style="padding:7px 10px;"><code>find()</code></td>
<td style="padding:7px 10px;">Find text or character</td>
<td style="padding:7px 10px;"><code>s.find('l')</code></td>
<td style="padding:7px 10px;"><code>2</code></td>
</tr>
<tr>
<td style="padding:7px 10px;"><code>substr()</code></td>
<td style="padding:7px 10px;">Create a substring</td>
<td style="padding:7px 10px;"><code>s.substr(1, 3)</code></td>
<td style="padding:7px 10px;"><code>"ell"</code></td>
</tr>
<tr>
<td style="padding:7px 10px;"><code>compare()</code></td>
<td style="padding:7px 10px;">Compare strings</td>
<td style="padding:7px 10px;"><code>s.compare("Hello")</code></td>
<td style="padding:7px 10px;"><code>0</code></td>
</tr>
<tr>
<td style="padding:7px 10px;"><code>empty()</code></td>
<td style="padding:7px 10px;">Check whether empty</td>
<td style="padding:7px 10px;"><code>s.empty()</code></td>
<td style="padding:7px 10px;"><code>false</code></td>
</tr>
<tr>
<td style="padding:7px 10px;"><code>clear()</code></td>
<td style="padding:7px 10px;">Remove all characters</td>
<td style="padding:7px 10px;"><code>s.clear()</code></td>
<td style="padding:7px 10px;"><code>""</code></td>
</tr>
<tr>
<td style="padding:7px 10px;"><code>push_back()</code></td>
<td style="padding:7px 10px;">Add one character</td>
<td style="padding:7px 10px;"><code>s.push_back('!')</code></td>
<td style="padding:7px 10px;"><code>"Hello!"</code></td>
</tr>
<tr>
<td style="padding:7px 10px;"><code>pop_back()</code></td>
<td style="padding:7px 10px;">Remove last character</td>
<td style="padding:7px 10px;"><code>s.pop_back()</code></td>
<td style="padding:7px 10px;"><code>"Hell"</code></td>
</tr>
<tr>
<td style="padding:7px 10px;"><code>c_str()</code></td>
<td style="padding:7px 10px;">Get C-style string pointer</td>
<td style="padding:7px 10px;"><code>s.c_str()</code></td>
<td style="padding:7px 10px;"><code>const char*</code></td>
</tr>
</tbody>
</table>

::

::div{class="definition-box" style="margin-top:30px !important; font-size:1rem !important;"}
**Reference:** [`std::string` Member Functions](https://en.cppreference.com/w/cpp/string/basic_string)
::


---

# Lecture Summary — Types & Namespaces

::div{class="normal-text-small" style="font-size:1.15rem; line-height:1.5;"}

- **User-defined data types** allow programmers to create types that better represent program data.
- An **`enum`** defines a fixed set of named integral values.
- Enumerators can use **default values** or explicitly assigned values.
- `typedef` and `using` create **aliases for existing types**.
- **Namespaces** group related identifiers and help prevent naming conflicts.
- The scope resolution operator **`::`** accesses identifiers within a namespace.
- C++ Standard Library identifiers such as `cout`, `cin`, and `string` belong to the **`std` namespace**.

::

::div{class="definition-box" style="margin-top:20px !important; font-size:1.15rem !important;"}
**Key idea:** Types help represent data clearly, while namespaces help organize names and avoid conflicts.
::

---

# Lecture Summary — Strings

::div{class="normal-text-small" style="font-size:1.1rem; line-height:1.5;"}

- A **C-style string** is a character array terminated by the null character `'\0'`.
- **`std::string`** provides a more convenient interface for storing and manipulating text.
- Both C-style strings and `std::string` store characters **contiguously**.
- `std::string` manages its **storage and capacity automatically**.
- Many implementations use **Small String Optimization (SSO)** for short strings and dynamic storage when more capacity is needed.
- `std::string` supports operations such as **concatenation, comparison, searching, insertion, replacement, and removal**.
- Member functions such as `size()`, `find()`, `substr()`, `append()`, and `erase()` simplify common string operations.

::

::div{class="definition-box" style="margin-top:20px !important; font-size:1.15rem !important;"}
**Key idea:** Prefer `std::string` for most C++ text processing because it provides convenient operations and manages its own storage.
::

---

<div class="definition-box">
Choose meaningful types, organize identifiers with namespaces, and use <code>std::string</code> to manage text effectively.
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
  question="Q1. Which statement best describes an enumeration (`enum`) in C++?"
  :options="[
    'An alternative name for an existing data type',
    'A user-defined type containing a fixed set of named values',
    'A named scope used to organize identifiers',
    'A sequence of characters stored in an array'
  ]"
  correct="A user-defined type containing a fixed set of named values"
  explanation="An enumeration is a user-defined data type containing a fixed set of named values called enumerators."
/>

---

<QuizQuestion
  question="Q2. What values are assigned to `RED`, `GREEN`, and `BLUE` in `enum Color { RED, GREEN, BLUE };`?"
  :options="[
    'RED = 1, GREEN = 2, BLUE = 3',
    'All three have the value 0',
    'The compiler chooses unpredictable values',
    'RED = 0, GREEN = 1, BLUE = 2'
  ]"
  correct="RED = 0, GREEN = 1, BLUE = 2"
  explanation="By default, the first enumerator has the value 0 and each following enumerator increases by 1."
/>

---

<QuizQuestion
  question="Q3. What is the purpose of `typedef` and `using` in C++?"
  :options="[
    'To create alternative names for existing types',
    'To create namespaces',
    'To assign values to enumerators',
    'To create character arrays'
  ]"
  correct="To create alternative names for existing types"
  explanation="Both typedef and using create type aliases, allowing an existing type to be referred to by another name."
/>

---

<QuizQuestion
  question="Q4. What is the primary purpose of a namespace?"
  :options="[
    'To allocate memory for variables',
    'To convert between data types',
    'To group related identifiers and prevent naming conflicts',
    'To create aliases for existing types'
  ]"
  correct="To group related identifiers and prevent naming conflicts"
  explanation="Namespaces provide named scopes for identifiers. This allows the same identifier name to exist in different namespaces without conflict."
/>

---

<QuizQuestion
  question="Q5. What does the `::` operator do in `Student::display()`?"
  :options="[
    'Creates a Student object',
    'Accesses `display()` from the Student namespace',
    'Creates an alias for `display()`',
    'Declares `display()` as a global function'
  ]"
  correct="Accesses `display()` from the Student namespace"
  explanation="The :: operator is the scope resolution operator. `Student::display()` accesses `display()` from the Student namespace."
/>

---

<QuizQuestion
  question="Q6. What identifies the end of a C-style string?"
  :options="[
    'A space character',
    'A newline character',
    'The final visible character',
    'The null character `\\0`'
  ]"
  correct="The null character `\0`"
  explanation="A C-style string is stored as a sequence of characters followed by the null character `\0`, which marks the end of the string."
/>

---

<QuizQuestion
  question="Q7. Why does `char name[6] = &quot;Alice&quot;;` require six array elements?"
  :options="[
    'Five elements store Alice and one stores the null terminator',
    'Every character array requires one unused element',
    'The sixth element stores the length of the string',
    'Character arrays must contain an even number of elements'
  ]"
  correct="Five elements store Alice and one stores the null terminator"
  explanation="Alice contains five visible characters. A C-style string also requires one additional element for the null terminator `\0`."
/>

---

<QuizQuestion
  question="Q8. Which statement correctly compares C-style strings and `std::string`?"
  :options="[
    'Only C-style strings store characters contiguously',
    'Both require manual null termination',
    'Both store characters contiguously, but `std::string` manages its own storage',
    '`std::string` has a fixed capacity that cannot change'
  ]"
  correct="Both store characters contiguously, but `std::string` manages its own storage"
  explanation="Both store their characters contiguously. A major difference is that std::string manages its storage and can grow as needed."
/>

---

<QuizQuestion
  question="Q9. What is an important difference between `s.at(1)` and `s[1]`?"
  :options="[
    '`operator[]` performs bounds checking but `at()` does not',
    '`at()` performs bounds-checked access but `operator[]` does not',
    '`at()` can only access the first character',
    '`operator[]` works only with C-style strings'
  ]"
  correct="`at()` performs bounds-checked access but `operator[]` does not"
  explanation="Both can access a character by position, but `at()` performs bounds checking while `operator[]` does not."
/>

---

<QuizQuestion
  question="Q10. What is Small String Optimization (SSO)?"
  :options="[
    'A technique for converting `std::string` to a C-style string',
    'A technique that prevents strings from changing size',
    'A technique for automatically shortening long strings',
    'A technique that may store short-string characters inside the string object'
  ]"
  correct="A technique that may store short-string characters inside the string object"
  explanation="Many `std::string` implementations use Small String Optimization to store the characters of some short strings inside the string object, avoiding a separate dynamic allocation."
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

