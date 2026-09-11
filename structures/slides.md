---
theme: dracula
background: https://cover.sli.dev
title: Structures
author: Dr Danish Khan
transition: fade-out
mdc: true

---

# Structures


Dr. Danish Khan | dkhan@sdccd.edu


Press Space for next page

---

# Learning Outcomes

::div{class="normal-text-small" style="font-size:1.1rem; line-height:1.6;"}

By the end of this lecture, you should be able to:
- **Define and create** structures and structure objects.

- **Access and modify** structure members using the `.` operator.

- **Initialize and assign** values to structure objects.

- Use structures with **arrays and functions**.

- Create and access **nested structures**.

- Explain the basic difference between **`struct` and `class`**.

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

# What Are Structures?

::div{class="normal-text-small" style="font-size:1.18rem !important; line-height:1.55 !important;"}

In C++, a **structure (`struct`)** is a user-defined type that groups **related data members** under a single type name.

The members of a structure can have **different data types**.

Structures are commonly used to represent records or entities that contain several related attributes.

::

```cpp
struct Student {
    string name;
    int age;
    double gpa;
};
```

::div{class="definition-box" style="margin-top:22px !important;"}

A `Student` groups a student's `name`, `age`, and `gpa` into **one meaningful type**.

::

---

# Why Structures?

::div{class="normal-text-small"}

### 1. Group related data logically

Without structures, related information may be stored in separate variables or arrays.

With a structure, the information describing one entity can be grouped together.

::

::code-group

```cpp [With struct]
struct Student {
    string name;
    int age;
    double gpa;
};

Student s1 = {"Kim", 20, 3.8};
```

```cpp [Without struct]
string names[50];
int ages[50];
double gpas[50];
```

::

::div{class="definition-box" style="margin-top:20px !important;"}

A structure keeps **related data together** as one logical unit.

::

---

# Why Structures?

::div{class="normal-text-small"}

### 2. Improve readability and organization

A structure allows the program to use meaningful expressions that describe the relationship between an object and its data.

::

```cpp
struct Student {
    string name;
    int age;
    double gpa;
};
Student s1 = {"Kim", 20, 3.8};
cout << s1.name << " has GPA " << s1.gpa;
```

::div{class="normal-text-small" style="margin-top:18px !important;"}

The expression:

```cpp
s1.gpa
```

**means the `gpa` belonging to `s1`**

::

::div{class="definition-box" style="margin-top:0px !important; font-size:1.3rem !important;"}

Structures make related data easier to **identify, organize, and use**.

::

---

# Why Structures?

::div{class="normal-text-small"}

### 3. Represent related data as one type

Once `Student` has been defined, we can create objects that represent complete student records.

```cpp
Student s1;
```

Instead of thinking about separate variables such as:

```cpp
name
age
gpa
```

we can work with one object:

```cpp
s1
```

::

::div{class="definition-box" style="margin-top:0px !important; font-size:1.3rem !important;"}
A structure combines several related attributes into a **single user-defined type**.
::

---

# Why Structures?

::div{class="normal-text-small"}

### 4. Pass related data to functions

Without a structure, a function might require several separate parameters:

::

```cpp
void printStudent(string name, int age, double gpa);
```

::div{class="normal-text-small" style="margin-top:16px !important;"}

With a structure, the complete student record can be passed as one object:

::

```cpp
void printStudent(const Student& s) {
    cout << s.name
         << " (" << s.age << ")"
         << " - GPA: " << s.gpa;
}
```

::div{class="definition-box" style="margin-top:18px !important;"}

`const Student&` allows the function to read the complete student record **without copying or modifying it**.

::

---

# Why Structures?

::div{class="grid grid-cols-2 gap-6" style="margin-top:-8px !important;"}

::div{class="normal-text-small-compact"}

### 5. Foundation for Classes

Structures provide an introduction to **classes and objects**.

Both `struct` and `class` can contain:

- Data members
- Member functions
- Objects of other types

**Key difference:**

- `struct` → members are **public by default**
- `class` → members are **private by default**

::

::div{style="font-size:0.9rem !important;"}

```cpp
// struct
struct Student {
    string name;   // public
    int age;       // public
};

// class
class Student {
    string name;   // private
    int age;       // private
};
```

::

::

::div{class="definition-box" style="margin-top:10px !important; font-size:1.3rem !important;"}
A `struct` and a `class` are very similar in C++; an important difference is their **default access level**.
::

---

# Struct Definition

::div{class="normal-text-small"}

A structure definition creates a **new type**.

It specifies the members that objects of that type will contain.

::

```cpp
#include <iostream>
#include <string>

using namespace std;

struct Student {
    string name;
    int age;
    double gpa;
};
```

::div{class="normal-text-small" style="margin-top:18px !important;"}

Here:

- `Student` is the **type name**
- `name`, `age`, and `gpa` are **data members**

::

::div{class="definition-box" style="margin-top:10px !important; font-size:1.3rem !important;"}

Defining `Student` creates a **type**. It does not create a `Student` object.

::

---

# Creating a Structure Object

::div{class="normal-text-small"}

After defining the type, we can declare an object of that type.

::

```cpp
Student s1;
```

::div{class="normal-text-small" style="margin-top:20px !important;"}

Now `s1` is an object of type `Student`.

It contains its own:

```text
name
age
gpa
```

We access these members using the **member-access operator (`.`)**:

```cpp
s1.name
s1.age
s1.gpa
```

::

::div{class="definition-box" style="margin-top:18px !important;"}

**`Student` is the type. `s1` is an object of that type.**

::

---

# Declare and Initialize

::div{class="normal-text-small"}

An object can be **declared and initialized** in one statement.

::

```cpp
#include <iostream>
#include <string>

using namespace std;

struct Student {
    string name;
    int age;
    double gpa;
};

int main() {
    Student s1 = {"Kim", 20, 3.8};
    cout << s1.name << " has GPA " << s1.gpa;
    return 0;
}
```

::div{class="definition-box" style="margin-top:18px !important; font-size:1.1rem !important;"}

The initializer values correspond to the members in their **declaration order**:<br>
`name` → `"Kim"` &nbsp;&nbsp; `age` → `20` &nbsp;&nbsp; `gpa` → `3.8`

::

---

# Declare First, Assign Later

::div{class="normal-text-small"}

An object can also be declared first and its members assigned individually.

::

::div{style="max-height:300px; overflow-y:auto; font-size:0.9rem !important;"}

```cpp
#include <iostream>
#include <string>

using namespace std;

struct Student {
    string name;
    int age;
    double gpa;
};

int main() {
    Student s1;

    s1.name = "Kim";
    s1.age = 40;
    s1.gpa = 3.8;
    cout << s1.name << " has GPA " << s1.gpa;
    return 0;
}
```

::

::div{class="definition-box" style="margin-top:18px !important; font-size:1.1rem !important;"}

Use the **`.` operator** to access an individual member:<br>
`object.member`

::

---

# Initialization vs Assignment

::div{class="grid grid-cols-2 gap-8 normal-text-small"}

::div

### Initialization

Values are provided when the object is created.

```cpp
Student s1 = {
    "Kim",
    20,
    3.8
};
```

The values follow the order of the members in the structure definition.

::

::div

### Assignment

The object already exists.

```cpp
Student s1;

s1.name = "Kim";
s1.age = 20;
s1.gpa = 3.8;
```

Individual members are assigned using `.` (dot).

::

::

::div{class="definition-box" style="margin-top:20px !important;"}

**Initialization gives an object its initial values; assignment changes values after the object exists.**

::

---

# Declaring Objects in Different Scopes

::div{class="normal-text-small"}

Structure objects can be declared in different scopes.

::

::code-group

```cpp [Inside main()]
struct Student {
    string name;
    int age;
    double gpa;
};

int main() {
    Student s1;

    s1.name = "Kim";
    s1.age = 40;
    s1.gpa = 3.8;
}
```

```cpp [Outside main()]
struct Student {
    string name;
    int age;
    double gpa;
};

Student s1;

int main() {
    s1.name = "Kim";
    s1.age = 40;
    s1.gpa = 3.8;
}
```

::

::div{class="definition-box" style="margin-top:18px !important;"}

Inside `main()` → **local object**  
Outside all functions → **global object**

::

---

# Definition and Declaration Together

::div{class="normal-text-small"}

C++ also allows an object to be declared at the end of the structure definition.

::

```cpp
struct Student {
    string name;
    int age;
    double gpa;
} s1;
```

::div{class="normal-text-small" style="margin-top:20px !important;"}

This statement does two things:

1. Defines the type `Student`
2. Declares an object named `s1`

::

::div{class="definition-box" style="margin-top:20px !important;"}

This syntax is valid, but separating the **type definition** and **object declaration** often makes the code easier to understand.

::

---

# Multiple Structure Objects

::div{class="normal-text-small"}

A structure definition acts as a blueprint for creating multiple objects.

Each object contains its **own values**.

::

::div{style="max-height:300px; overflow-y:auto; font-size:0.9rem !important;"}

```cpp
#include <iostream>
#include <string>

using namespace std;

struct Student {
    string name;
    int age;
    double gpa;
};

int main() {
    Student s1 = {"Kim", 40, 3.8};
    Student s2 = {"Sarah", 35, 3.5};

    cout << s1.name << " has GPA " << s1.gpa << '\n';
    cout << s2.name << " has GPA " << s2.gpa << '\n';

    return 0;
}
```

::

::div{class="definition-box" style="margin-top:18px !important; font-size:1.1rem !important;"}

`s1` and `s2` have the same type, but they are **separate objects with independent data**.

::
---

# Array of Structures

::div{class="normal-text-small"}

If we need several objects of the same structure type, they can be stored in an array.

::

::div{style="max-height:300px; overflow-y:auto; font-size:0.9rem !important;"}

```cpp
#include <array>
#include <iostream>
#include <string>

using namespace std;

struct Student {
    int id;
    string name;
    double gpa;
};

int main() {
    array<Student, 3> students = {{
        {21001, "Alice", 3.75},
        {21002, "Bob",   3.40},
        {21003, "Diana", 3.92}
    }};

    for (const auto& student : students) {
        cout << student.id << " "
             << student.name << " "
             << student.gpa << '\n';
    }

    return 0;
}
```
::
::div{class="definition-box" style="margin-top:18px !important;"}

`array<Student, 3>` contains **three `Student` objects**.

::

---

# Accessing an Array of Structures

::div{class="normal-text-small"}

To access a member of an object stored in an array:

1. Select the object using an **index**
2. Select its member using **`.`**

::

```cpp
cout << students[0].name;
cout << students[1].gpa;
cout << students[2].id;
```

::div{class="normal-text-small" style="margin-top:24px !important;"}

For example:

```cpp
students[1].gpa
```

can be read from left to right:

**`students[1]` → second Student object → `gpa`**

::

::div{class="definition-box" style="margin-top:18px !important; font-size:1.3rem !important;"}

Array indexing selects the **object**; the `.` operator selects a **member of that object**.

::

---

# Structures Within Structures

::div{class="normal-text-small"}

A structure can contain objects of other structure types.

This allows related information to be organized into larger records.

::

::div{style="max-height:300px; overflow-y:auto; font-size:0.9rem !important;"}

```cpp
struct Student {
    string firstName;
    string lastName;
};

struct Course {
    int courseID;
    string courseName;
};

struct Professor {
    string firstName;
    string lastName;
};

struct ClassSection {
    Student student;
    Course course;
    Professor professor;
};
```
::
---

# Accessing Nested Structures

::div{class="grid grid-cols-2 gap-8"}

::div{class="normal-text-small"}

### Accessing Members

Create an object of the outer structure:

```cpp
ClassSection fall2026;
```

Then access members one level at a time:

```cpp
fall2026.student.firstName = "Kim";

fall2026.course.courseID = 192;
fall2026.course.courseName = "C++ Programming";

fall2026.professor.firstName = "Danish";
```

::

::div{class="normal-text-small"}

### Reading Nested Access

```cpp
cout << fall2026.course.courseName;
```

Read:

```cpp
fall2026.course.courseName
```

from left to right:

- `fall2026` → outer object
- `course` → nested `Course` object
- `courseName` → member of `Course`

::div{class="definition-box" style="margin-top:18px !important; font-size:1.1rem !important;"}

Each `.` moves **one level deeper** into the nested structure.

::

::

::

---

# Structures — Summary

::div{class="normal-text-small" style="font-size:1.1rem !important; line-height:1.5 !important;"}

- A `struct` defines a **user-defined type**.
- A structure groups **related data members**, which may have different types.
- Defining a structure creates a type; declaring a structure variable creates an **object**.
- Objects can be initialized when created or their members can be assigned later.
- Members are accessed using the **`.` operator**.
- Multiple independent objects can be created from the same structure type.
- Structure objects can be stored in **arrays**.
- Structures can contain **other structures**.
- Complete structure objects can be passed to **functions**.

::

::div{class="definition-box" style="margin-top:18px !important; font-size:1.3rem !important;"}

**Structures group related data into meaningful user-defined types, allowing several attributes to be managed as one logical object.**

::

---

<div class="definition-box">
Structures group related data of different types into a single meaningful object, with members accessed using the <code>.</code> operator.
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
  question="Q1. What is a structure (struct) in C++?"
  :options="[
    'A built-in container that stores only integers',
    'A user-defined type that groups related data members',
    'A function used to create multiple variables',
    'A dynamically sized array of different data types'
  ]"
  correct="A user-defined type that groups related data members"
  explanation="A struct defines a user-defined type that groups related data members, which may have different data types, under one type name."
/>

---

<QuizQuestion
  question="Q2. After defining a struct named Student, which statement creates an object of that type?"
  :options="[
    '`struct Student;`',
    '`Student.name;`',
    '`Student s1;`',
    '`s1 Student;`'
  ]"
  correct="`Student s1;`"
  explanation="Student is the type name, while s1 is an object declared from that type."
/>

---

<QuizQuestion
  question="Q3. Which expression correctly accesses the gpa member of a Student object named s1?"
  :options="[
    '`s1.gpa`',
    '`s1::gpa`',
    '`s1[gpa]`',
    '`Student.gpa`'
  ]"
  correct="`s1.gpa`"
  explanation="The dot (.) operator is the member-access operator used to access a member of a structure object."
/>

---

<QuizQuestion
  question="Q4. Given Student `s1 = {&quot;Kim&quot;, 20, 3.8};`, what determines which member receives each value?"
  :options="[
    'The alphabetical order of the member names',
    'The size of each member data type',
    'The order in which the values are used later',
    'The declaration order of the structure members'
  ]"
  correct="The declaration order of the structure members"
  explanation="The initializer values correspond to the structure members in declaration order. For name, age, and gpa, the values are therefore Kim, 20, and 3.8 respectively."
/>

---

<QuizQuestion
  question="Q5. Which statement describes assignment to a structure member?"
  :options="[
    'Values are provided only while the struct type is being defined',
    'A value is given to a member after the object already exists',
    'A new structure type is created from an existing object',
    'All members must receive new values at the same time'
  ]"
  correct="A value is given to a member after the object already exists"
  explanation="Assignment occurs after an object exists. For example, s1.gpa = 3.8; assigns a value to the gpa member of s1."
/>

---

<QuizQuestion
  question="Q6. Where is Student `s1` declared if it appears inside `main()`?"
  :options="[
    'As a global object',
    'As a structure definition',
    'As a local object',
    'As a nested structure'
  ]"
  correct="As a local object"
  explanation="An object declared inside main() has local scope. An object declared outside all functions has global scope."
/>

---

<QuizQuestion
  question="Q7. What is an important default-access difference between struct and class in C++?"
  :options="[
    'struct members are public by default, while class members are private by default',
    'struct members are private by default, while class members are public by default',
    'A struct can contain only data members, while a class can contain only functions',
    'A class can contain objects, while a struct cannot'
  ]"
  correct="struct members are public by default, while class members are private by default"
  explanation="Both struct and class can contain data members and member functions. The lecture emphasizes that struct members are public by default, while class members are private by default."
/>

---

<QuizQuestion
  question="Q8. What does array&lt;Student, 3&gt; students represent?"
  :options="[
    'One Student object containing three members',
    'A dynamic array that can grow beyond three students',
    'Three different Student structure definitions',
    'A fixed-size array containing three Student objects'
  ]"
  correct="A fixed-size array containing three Student objects"
  explanation="`array<Student, 3>` creates a `std::array` containing three elements, and each element is a complete Student object."
/>

---

<QuizQuestion
  question="Q9. In `students[1].gpa`, what does `students[1]` select?"
  :options="[
    'The gpa member of every Student',
    'The Student object at index 1',
    'The second member declared inside Student',
    'The entire students array'
  ]"
  correct="The Student object at index 1"
  explanation="`students[1]` first selects the Student object at index 1. The `.gpa` portion then accesses the gpa member of that object."
/>

---

<QuizQuestion
  question="Q10. What is the purpose of passing a Student object as `const Student&` to a function?"
  :options="[
    'To create a new Student type inside the function',
    'To allow the function to permanently delete the object',
    'To read the Student object without copying or modifying it',
    'To convert the Student object into an array'
  ]"
  correct="To read the Student object without copying or modifying it"
  explanation="Passing the object as const Student& allows the function to access the original Student without making a copy, while const prevents the function from modifying it."
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

