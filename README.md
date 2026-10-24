
# C-000 — Unit Converter

**Language:** C  
**Level:** Beginner  
**Repository:** `c-000-unit-converter`

## Project

Build a command-line unit converter in C.

Start with a simple measurement, then add calculations, user input, conversion choices, a menu, conversion history, and reusable functions.

Each task introduces a new programming chapter and adds a feature to the same application.

**Rules:**
- Every task contains a complete, runnable C program.
- Each task builds on what you've already learned.
- Every new line should introduce a concept, add useful behavior, or be necessary for the program to work.
- Avoid repetitive calculations and unnecessary `printf()` statements.

## Chapters

| Task | Chapter | New Concepts |
|---|---|---|
| 1 | Variables & Data Types | `int`, `double`, `char`, declaration, initialization |
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

Create your first measurement record.

Store the measurement, its unit, and a conversion result. For now, the values can be hardcoded.

### Assignments

- [ ] Create an integer to identify the conversion.
- [ ] Create a decimal variable for the original value.
- [ ] Create another decimal variable for the result.
- [ ] Store a single-character unit symbol.
- [ ] Store the measurement name as a string.
- [ ] Display the measurement record.

### Code

```c
#include <stdio.h>

int main(void) {
    int id = 1;
    double value = 5.0;
    double result = 500.0;
    char unit = 'm';
    char name[] = "Length";

    printf("%d | %s | %.2f %c -> %.2f cm\n",
           id, name, value, unit, result);

    return 0;
}
```

### Explanation

- `int` stores whole numbers.
- `double` stores decimal numbers.
- `char` stores one character.
- `char[]` stores text.
- Declaration creates a variable.
- Initialization gives the variable its first value.
- `printf()` displays the record.

---

## Task 2

**Chapter:** Constants

### Feature / Mission

Add fixed settings to the converter.

Give the application a name and define the conversion factor that will be used in calculations.

### Assignments

- [ ] Define the application name using `#define`.
- [ ] Define the maximum history size using `#define`.
- [ ] Create a `const double` for centimeters per meter.
- [ ] Keep the existing measurement record.
- [ ] Display the measurement using the application name.

### Code

```c
#include <stdio.h>

#define APP_NAME "Unit Converter"
#define MAX_HISTORY 100

int main(void) {
    const double CM_PER_METER = 100.0;

    int id = 1;
    double value = 5.0;
    double result = 500.0;
    char unit = 'm';
    char name[] = "Length";

    printf("%s | %d | %s | %.2f %c -> %.2f cm\n",
           APP_NAME, id, name, value, unit, result);

    return 0;
}
```

### Explanation

- `#define` creates a preprocessor macro.
- `const` makes a variable read-only after initialization.
- `CM_PER_METER` stores the conversion factor.
- `MAX_HISTORY` will limit the number of saved conversions later.

---

## Task 3

**Chapter:** Operators

### Feature / Mission

Make the converter calculate its result instead of storing a hardcoded answer.

### Assignments

- [ ] Use multiplication to convert meters to centimeters.
- [ ] Store the calculated value in `result`.
- [ ] Use division to convert the result back to meters.
- [ ] Use compound assignment to update an existing variable.
- [ ] Display the calculated conversion.

### Code

```c
#include <stdio.h>

#define APP_NAME "Unit Converter"

int main(void) {
    const double CM_PER_METER = 100.0;

    double value = 5.0;
    double result = value * CM_PER_METER;

    printf("%s: %.2f m = %.2f cm\n",
           APP_NAME, value, result);

    result /= CM_PER_METER;

    printf("%.2f cm = %.2f m\n",
           value * CM_PER_METER, result);

    return 0;
}
```

### Explanation

- `=` assigns a value.
- `*` multiplies a measurement by its conversion factor.
- `/` divides one value by another.
- `/=` divides a variable's current value and saves the result.
- The converter now calculates results instead of hardcoding them.

---

## Task 4

**Chapter:** Input & Output

### Feature / Mission

Let the user enter a measurement instead of changing the source code every time.

### Assignments

- [ ] Ask the user to enter a value in meters.
- [ ] Read the value using `scanf()`.
- [ ] Check whether the input is a valid number.
- [ ] Convert the measurement into centimeters.
- [ ] Display the result with two decimal places.

### Code

```c
#include <stdio.h>

#define APP_NAME "Unit Converter"

int main(void) {
    const double CM_PER_METER = 100.0;

    double value;

    printf("%s\n", APP_NAME);
    printf("Meters: ");

    if (scanf("%lf", &value) != 1) {
        printf("Invalid number.\n");
        return 1;
    }

    double result = value * CM_PER_METER;

    printf("%.2f m = %.2f cm\n", value, result);

    return 0;
}
```

### Explanation

- `printf()` displays information.
- `scanf()` reads user input.
- `%lf` reads a `double`.
- `&value` passes the address of the variable.
- `%.2f` displays two decimal places.
- `\n` creates a new line.
- `scanf()` returns the number of successfully read values.

---

## Task 5

**Chapter:** Conditional Statements

### Feature / Mission

Let the user choose what to convert.

Add three conversion options and reject invalid choices or measurements.

### Assignments

- [ ] Add meters-to-centimeters conversion.
- [ ] Add centimeters-to-meters conversion.
- [ ] Add Celsius-to-Kelvin conversion.
- [ ] Ask the user to select an option.
- [ ] Use `switch` to run the selected conversion.
- [ ] Use `if` to check invalid measurements.
- [ ] Reject temperatures below absolute zero.
- [ ] Use logical operators to validate the selected option.
- [ ] Display the result.

### Code

```c
#include <stdio.h>

int main(void) {
    const double CM_PER_METER = 100.0;
    const double KELVIN_OFFSET = 273.15;

    int choice;
    double value;
    double result;

    printf("1. Meters to Centimeters\n");
    printf("2. Centimeters to Meters\n");
    printf("3. Celsius to Kelvin\n");

    printf("Choice: ");

    if (scanf("%d", &choice) != 1) {
        return 1;
    }

    if (choice < 1 || choice > 3) {
        printf("Invalid choice.\n");
        return 1;
    }

    printf("Value: ");

    if (scanf("%lf", &value) != 1) {
        return 1;
    }

    if (choice == 3 && value < -273.15) {
        printf("Temperature below absolute zero.\n");
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
            result = value + KELVIN_OFFSET;
            break;

        default:
            return 1;
    }

    printf("Result: %.2f\n", result);

    return 0;
}
```

### Explanation

- `if` checks a condition.
- `&&` means AND.
- `||` means OR.
- `switch` selects a block of code.
- `case` handles a specific choice.
- `break` exits the switch.
- `default` handles unmatched choices.
- `<`, `>`, and `==` compare values.

---

## Task 6

**Chapter:** Loops

### Feature / Mission

Keep the converter running until the user chooses to exit.

Users should be able to perform several conversions during one session.

### Assignments

- [ ] Put the conversion menu inside a `do...while` loop.
- [ ] Add an Exit option.
- [ ] Use `for` to display menu options.
- [ ] Use `while` to retry invalid menu input.
- [ ] Use `continue` to skip invalid choices.
- [ ] Use `break` to exit the application.
- [ ] Count successful conversions.
- [ ] Display the total count when the program closes.

### Code

```c
#include <stdio.h>

int main(void) {
    const double CM_PER_METER = 100.0;
    const double KELVIN_OFFSET = 273.15;

    const char *options[] = {
        "Meters to Centimeters",
        "Centimeters to Meters",
        "Celsius to Kelvin",
        "Exit"
    };

    int choice = 0;
    int count = 0;

    do {
        for (int i = 0; i < 4; i++) {
            printf("%d. %s\n", i + 1, options[i]);
        }

        printf("Choice: ");

        while (scanf("%d", &choice) != 1) {
            int ch;

            while ((ch = getchar()) != '\n' && ch != EOF) {
            }

            printf("Enter a number: ");
        }

        if (choice == 4) {
            break;
        }

        if (choice < 1 || choice > 3) {
            continue;
        }

        double value;
        double result;

        printf("Value: ");

        if (scanf("%lf", &value) != 1) {
            int ch;

            while ((ch = getchar()) != '\n' && ch != EOF) {
            }

            continue;
        }

        if (choice == 3 && value < -273.15) {
            continue;
        }

        switch (choice) {
            case 1:
                result = value * CM_PER_METER;
                break;

            case 2:
                result = value / CM_PER_METER;
                break;

            case 3:
                result = value + KELVIN_OFFSET;
                break;

            default:
                continue;
        }

        printf("Result: %.2f\n", result);
        count++;

    } while (choice != 4);

    printf("Completed conversions: %d\n", count);

    return 0;
}
```

### Explanation

- `for` repeats code with a counter.
- `while` repeats while a condition is true.
- `do...while` runs at least once.
- `break` exits the nearest loop.
- `continue` skips to the next iteration.
- `++` increases a variable by one.
- `!=` means not equal.

---

## Task 7

**Chapter:** Arrays & Strings

### Feature / Mission

Add conversion history.

The program should remember completed conversions, let the user list them, and search for a conversion by name.

### Assignments

- [ ] Create arrays for original values and converted results.
- [ ] Create a two-dimensional character array for conversion names.
- [ ] Store each successful conversion.
- [ ] Limit history to 100 records.
- [ ] Use `strlen()` to check conversion names.
- [ ] Use `strcpy()` to save names.
- [ ] Use `strcmp()` to search by name.
- [ ] Add a menu option to list history.
- [ ] Add a menu option to search history.

### Code

```c
#include <stdio.h>
#include <string.h>

#define MAX_HISTORY 100
#define NAME_SIZE 40

int main(void) {
    double originals[MAX_HISTORY];
    double results[MAX_HISTORY];
    char names[MAX_HISTORY][NAME_SIZE];

    const char *types[] = {
        "Meters to Centimeters",
        "Centimeters to Meters",
        "Celsius to Kelvin"
    };

    int count = 0;
    int choice = 0;

    do {
        printf("\n1. Convert\n2. List History\n3. Search\n4. Exit\n");
        printf("Choice: ");

        if (scanf("%d", &choice) != 1) {
            break;
        }

        if (choice == 1) {
            if (count == MAX_HISTORY) {
                printf("History is full.\n");
                continue;
            }

            int type;
            double value;
            double result;

            printf("Type (1-3): ");

            if (scanf("%d", &type) != 1) {
                break;
            }

            if (type < 1 || type > 3) {
                continue;
            }

            printf("Value: ");

            if (scanf("%lf", &value) != 1) {
                break;
            }

            if (type == 3 && value < -273.15) {
                continue;
            }

            switch (type) {
                case 1:
                    result = value * 100.0;
                    break;
                case 2:
                    result = value / 100.0;
                    break;
                case 3:
                    result = value + 273.15;
                    break;
                default:
                    continue;
            }

            if (strlen(types[type - 1]) >= NAME_SIZE) {
                continue;
            }

            originals[count] = value;
            results[count] = result;
            strcpy(names[count], types[type - 1]);
            count++;

        } else if (choice == 2) {
            for (int i = 0; i < count; i++) {
                printf("%s: %.2f -> %.2f\n",
                       names[i], originals[i], results[i]);
            }

        } else if (choice == 3) {
            char search[NAME_SIZE];

            printf("Conversion name: ");

            if (scanf(" %39[^\n]", search) != 1) {
                break;
            }

            for (int i = 0; i < count; i++) {
                if (strcmp(names[i], search) == 0) {
                    printf("%.2f -> %.2f\n",
                           originals[i], results[i]);
                }
            }
        }

    } while (choice != 4);

    return 0;
}
```

### Explanation

- Arrays store multiple values of the same type.
- `[]` accesses elements by index.
- Two-dimensional character arrays store multiple strings.
- `strlen()` gets a string's length.
- `strcpy()` copies a string.
- `strcmp()` compares strings.
- Array indexes start at zero.
- Bounds checks prevent writing beyond an array.

---

## Task 8

**Chapter:** Functions

### Feature / Mission

Turn the converter into a complete application organized around reusable functions.

Move conversion calculations, history storage, history listing, and searching out of `main()`.

### Assignments

- [ ] Create a function that displays the menu.
- [ ] Create a function that calculates conversions.
- [ ] Create a function that adds a conversion to history.
- [ ] Create a function that lists conversion history.
- [ ] Create a function that searches history.
- [ ] Use function prototypes.
- [ ] Pass values and arrays through parameters.
- [ ] Use `return` to send results back.
- [ ] Use `void` for functions that don't return a value.
- [ ] Keep `main()` focused on controlling the application.

### Code

```c
#include <stdio.h>
#include <string.h>

#define MAX_HISTORY 100
#define NAME_SIZE 40

void showMenu(void);
double convert(double value, int type);
void addHistory(
    double originals[],
    double results[],
    char names[][NAME_SIZE],
    int *count,
    double value,
    double result,
    const char *name
);
void listHistory(
    double originals[],
    double results[],
    char names[][NAME_SIZE],
    int count
);
void searchHistory(
    double originals[],
    double results[],
    char names[][NAME_SIZE],
    int count,
    const char *search
);

void showMenu(void) {
    printf("\n1. Convert\n2. List History\n3. Search\n4. Exit\n");
}

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

void addHistory(
    double originals[],
    double results[],
    char names[][NAME_SIZE],
    int *count,
    double value,
    double result,
    const char *name
) {
    if (*count >= MAX_HISTORY || strlen(name) >= NAME_SIZE) {
        return;
    }

    originals[*count] = value;
    results[*count] = result;
    strcpy(names[*count], name);
    (*count)++;
}

void listHistory(
    double originals[],
    double results[],
    char names[][NAME_SIZE],
    int count
) {
    for (int i = 0; i < count; i++) {
        printf("%s: %.2f -> %.2f\n",
               names[i], originals[i], results[i]);
    }
}

void searchHistory(
    double originals[],
    double results[],
    char names[][NAME_SIZE],
    int count,
    const char *search
) {
    for (int i = 0; i < count; i++) {
        if (strcmp(names[i], search) == 0) {
            printf("%.2f -> %.2f\n",
                   originals[i], results[i]);
        }
    }
}

int main(void) {
    double originals[MAX_HISTORY];
    double results[MAX_HISTORY];
    char names[MAX_HISTORY][NAME_SIZE];

    const char *types[] = {
        "Meters to Centimeters",
        "Centimeters to Meters",
        "Celsius to Kelvin"
    };

    int count = 0;
    int choice = 0;

    do {
        showMenu();

        printf("Choice: ");

        if (scanf("%d", &choice) != 1) {
            break;
        }

        if (choice == 1) {
            int type;
            double value;

            printf("Type (1-3): ");

            if (scanf("%d", &type) != 1) {
                break;
            }

            if (type < 1 || type > 3) {
                continue;
            }

            printf("Value: ");

            if (scanf("%lf", &value) != 1) {
                break;
            }

            if (type == 3 && value < -273.15) {
                continue;
            }

            double result = convert(value, type);

            addHistory(
                originals,
                results,
                names,
                &count,
                value,
                result,
                types[type - 1]
            );

            printf("Result: %.2f\n", result);

        } else if (choice == 2) {
            listHistory(originals, results, names, count);

        } else if (choice == 3) {
            char search[NAME_SIZE];

            printf("Conversion name: ");

            if (scanf(" %39[^\n]", search) != 1) {
                break;
            }

            searchHistory(
                originals,
                results,
                names,
                count,
                search
            );
        }

    } while (choice != 4);

    return 0;
}
```

### Explanation

- Function prototypes declare functions before they're used.
- Parameters pass data into functions.
- `return` sends a value back to the caller.
- `void` means a function doesn't return a value.
- `*count` accesses the value through a pointer.
- `&count` passes the address of the counter.
- Arrays can be passed to functions.
- Local variables belong to their function or block.
- `main()` now controls the program while other functions handle specific jobs.

---

## Final Application Checklist

- [ ] Convert meters to centimeters.
- [ ] Convert centimeters to meters.
- [ ] Convert Celsius to Kelvin.
- [ ] Accept user input.
- [ ] Validate conversion choices and measurements.
- [ ] Keep the program running until the user exits.
- [ ] Save up to 100 conversions.
- [ ] List conversion history.
- [ ] Search conversion history.
- [ ] Organize the application using functions.

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
