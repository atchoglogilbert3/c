
# C-000 — Unit Converter

**Language:** C  
**Level:** Beginner  
**Repository:** `c-000-unit-converter`

## Project

Build a command-line unit converter in C.

Start with a simple calculation, then add user input, conversion choices, a menu, history, and reusable functions.

Each task introduces a new programming chapter. Code snippets show only what's new or changed, rather than repeating the whole program.

## Chapters

| Task | Chapter | New Concepts |
|---|---|---|
| 1 | Variables & Data Types | `int`, `double`, `char`, declarations, initialization |
| 2 | Constants | `const`, `#define` |
| 3 | Operators | Arithmetic, assignment, compound assignment, modulo |
| 4 | Input & Output | `printf`, `scanf`, format specifiers |
| 5 | Conditional Statements | `if`, `else if`, `else`, `switch`, comparison and logical operators |
| 6 | Loops | `for`, `while`, `do...while`, `break`, `continue` |
| 7 | Arrays & Strings | Arrays, indexing, `strlen`, `strcmp`, `strcpy` |
| 8 | Functions | Function declarations, definitions, parameters, return values, scope |

---

## Task 1

**Chapter:** Variables & Data Types

### Feature / Mission

Create a measurement record that stores the information needed for a conversion.

### Assignments

- [ ] Store the original measurement as a decimal number.
- [ ] Store the converted result as a decimal number.
- [ ] Give the conversion a numeric ID.
- [ ] Store a one-character unit symbol.
- [ ] Store the measurement name as text.

### Code

```c
int id = 1;
double value = 5.0, result = 500.0;
char unit = 'm';
char measurement[] = "Length";
```

### Explanation

- `int` stores whole numbers.
- `double` stores decimal numbers.
- `char` stores one character.
- `char[]` stores a string.
- Variables can be declared and initialized in the same statement.
- Multiple variables of the same type can share a declaration.

---

## Task 2

**Chapter:** Constants

### Feature / Mission

Add fixed conversion settings that shouldn't change while the program runs.

### Assignments

- [ ] Create a constant for converting meters to centimeters.
- [ ] Define the maximum number of conversions the program can save.
- [ ] Define a name for the application.
- [ ] Use the conversion factor instead of a hardcoded result.

### Code

```c
#define MAX_HISTORY 100
#define APP_NAME "Unit Converter"

const double CM_PER_METER = 100.0;
```

### Explanation

- `const` creates a read-only variable.
- `#define` creates a preprocessor macro.
- Named constants make values easier to reuse.

---

## Task 3

**Chapter:** Operators

### Feature / Mission

Turn the measurement record into a working calculator.

The program should calculate the converted value instead of storing a manually calculated answer.

### Assignments

- [ ] Calculate centimeters from meters using multiplication.
- [ ] Calculate meters from centimeters using division.
- [ ] Add an offset to convert Celsius into Kelvin.
- [ ] Use compound assignment to update a measurement.
- [ ] Split a whole number of centimeters into meters and leftover centimeters using integer division and modulo.
- [ ] Store the final result.

### Code

```c
double result = value * CM_PER_METER;

result /= CM_PER_METER;

double kelvin = 25.0 + 273.15;

int centimeters = 257;
int meters = centimeters / 100;
int remainder = centimeters % 100;
```

### Explanation

- `*` multiplies values.
- `/` divides values.
- `+` adds values.
- `=` assigns a value.
- `/=` updates a variable by dividing its current value.
- `%` gives the remainder of integer division.
- Integer division and floating-point division behave differently.

---

## Task 4

**Chapter:** Input & Output

### Feature / Mission

Let the user enter a measurement and see its converted value.

### Assignments

- [ ] Ask the user for a measurement.
- [ ] Read a decimal number from the keyboard.
- [ ] Check whether reading the number succeeded.
- [ ] Calculate the conversion.
- [ ] Display the result with two decimal places.

### Code

```c
#include <stdio.h>

double value;

printf("Meters: ");

if (scanf("%lf", &value) != 1) {
    return 1;
}

printf("Centimeters: %.2f\n", value * CM_PER_METER);
```

### Explanation

- `#include <stdio.h>` provides standard input/output functions.
- `printf()` displays text and values.
- `scanf()` reads user input.
- `%lf` reads a `double`.
- `&` passes the address where input should be stored.
- `%.2f` displays two decimal places.
- `\n` adds a new line.
- `scanf()` returns the number of successfully assigned input values.

---

## Task 5

**Chapter:** Conditional Statements

### Feature / Mission

Let the user choose between different conversions.

The program should run the selected calculation and reject invalid choices.

### Assignments

- [ ] Ask the user to select a conversion.
- [ ] Use `switch` to choose the correct calculation.
- [ ] Add meters-to-centimeters conversion.
- [ ] Add centimeters-to-meters conversion.
- [ ] Add Celsius-to-Kelvin conversion.
- [ ] Use `if` to reject temperatures below absolute zero.
- [ ] Use `else if` and `else` to classify Celsius temperatures.
- [ ] Use logical operators to check whether a menu choice is valid.

### Code

```c
int choice;
double result;

scanf("%d", &choice);

if (choice < 1 || choice > 3) {
    return 1;
}

switch (choice) {
    case 1:
        result = value * CM_PER_METER;
        break;

    case 2:
        result = value / CM_PER_METER;
        break;

    case 3:
        if (value < -273.15) {
            return 1;
        }

        result = value + 273.15;
        break;

    default:
        return 1;
}

printf("%.2f\n", result);
```

### Explanation

- `if` runs code when a condition is true.
- `||` means OR.
- `switch` selects a branch based on a value.
- `case` identifies a possible value.
- `break` prevents execution from continuing into the next case.
- `default` handles unmatched values.
- `<` and `>` compare numbers.

---

## Task 6

**Chapter:** Loops

### Feature / Mission

Keep the converter running until the user chooses to exit.

Users should be able to make several conversions without restarting the program.

### Assignments

- [ ] Put the conversion menu inside a `do...while` loop.
- [ ] Add an option to exit.
- [ ] Use `break` to stop the application.
- [ ] Use `continue` to skip invalid choices.
- [ ] Use `while` to retry invalid numeric input.
- [ ] Use `for` to count completed conversions.
- [ ] Display the number of completed conversions when exiting.

### Code

```c
int count = 0;
int choice;

do {
    printf("1. Convert\n2. Exit\n");

    while (scanf("%d", &choice) != 1) {
        int ch;

        while ((ch = getchar()) != '\n' && ch != EOF) {
        }

        printf("Enter a number: ");
    }

    if (choice == 2) {
        break;
    }

    if (choice != 1) {
        continue;
    }

    count++;

} while (choice != 2);

for (int i = 0; i < count; i++) {
    /* Process each completed conversion. */
}
```

### Explanation

- `do...while` runs at least once.
- `while` repeats while its condition is true.
- `break` exits the nearest loop.
- `continue` skips to the next iteration.
- `for` is useful when processing a known number of items.
- `++` increments a variable.
- `!=` means not equal.

---

## Task 7

**Chapter:** Arrays & Strings

### Feature / Mission

Save conversion history so users can look up earlier results.

### Assignments

- [ ] Store up to 100 original values.
- [ ] Store their converted results.
- [ ] Store the name of each conversion.
- [ ] Add new conversions at the next free array index.
- [ ] Prevent the history from exceeding its capacity.
- [ ] Use `strlen()` to check conversion names.
- [ ] Use `strcpy()` to save conversion names.
- [ ] Use `strcmp()` to search history.
- [ ] Use a loop to process saved records.

### Code

```c
#include <string.h>

double originals[MAX_HISTORY];
double results[MAX_HISTORY];
char names[MAX_HISTORY][40];

int count = 0;

if (count < MAX_HISTORY && strlen("Meters to cm") < 40) {
    originals[count] = value;
    results[count] = result;
    strcpy(names[count], "Meters to cm");
    count++;
}

for (int i = 0; i < count; i++) {
    if (strcmp(names[i], "Meters to cm") == 0) {
        printf("%.2f -> %.2f\n", originals[i], results[i]);
    }
}
```

### Explanation

- Arrays store multiple values of the same type.
- `[]` accesses elements by index.
- Two-dimensional character arrays store multiple strings.
- `strlen()` finds the length of a string.
- `strcpy()` copies a string.
- `strcmp()` compares two strings.
- Array indexes start at zero.
- Array bounds must be checked before adding new records.

---

## Task 8

**Chapter:** Functions

### Feature / Mission

Split the converter into reusable functions.

The program should keep the same features, but the conversion calculations and history operations should no longer be mixed together inside `main()`.

### Assignments

- [ ] Create a function to convert a measurement.
- [ ] Pass the measurement value and conversion type as parameters.
- [ ] Return the converted value.
- [ ] Create a function that displays the menu.
- [ ] Create a function that adds a conversion to history.
- [ ] Create a function that searches conversion history.
- [ ] Use function prototypes.
- [ ] Use local variables inside functions.
- [ ] Call the functions from `main()`.
- [ ] Make sure the complete program still works.

### Code

```c
double convert(double value, int type);

double convert(double value, int type) {
    switch (type) {
        case 1:
            return value * 100.0;

        case 2:
            return value / 100.0;

        case 3:
            return value + 273.15;

        default:
            return value;
    }
}
```

### Explanation

- A function groups reusable code.
- Function prototypes tell the compiler about functions before their definitions.
- Parameters pass information into functions.
- `return` sends a result back.
- `void` is used when a function doesn't return a value.
- Local variables are only accessible inside their scope.
- Functions help separate different parts of the program.

---

## Final Application Checklist

- [ ] Convert meters to centimeters.
- [ ] Convert centimeters to meters.
- [ ] Convert Celsius to Kelvin.
- [ ] Accept measurements from the user.
- [ ] Let users choose a conversion.
- [ ] Reject invalid input.
- [ ] Repeat conversions until the user exits.
- [ ] Save conversion history.
- [ ] Search conversion history.
- [ ] Use functions to organize the application.

## Repository Structure

```text
c-000-unit-converter/
├── README.md
└── main.c
```

## Next Project

**C-001 — Student Management System**

**Repository:** `c-001-student-management`

New chapters:

- Structures
- Enumerations
- Typedef
- Data Modeling
- Modular Programming
- Header Files
