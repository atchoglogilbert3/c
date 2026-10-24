
# C-000 — Unit Converter

**Language:** C  
**Level:** Beginner  
**Repository:** `c-000-unit-converter`

## Project Overview

Build a command-line application that converts measurements between different units.

The application starts with a single conversion and gradually develops into a complete unit converter with a menu, input validation, conversion history, and reusable functions.

Every task adds a useful feature to the same application.

## Programming Roadmap

| Task | Chapter | Feature |
|---|---|---|
| 1 | Variables & Data Types | Store and display a measurement |
| 2 | Constants & Arithmetic Operators | Calculate meters to centimeters |
| 3 | Input & Output | Let the user enter a measurement |
| 4 | Conditional Statements | Choose between different conversions |
| 5 | Loops | Convert multiple measurements without restarting |
| 6 | Arrays & Strings | Save and search conversion history |
| 7 | Functions | Organize the application into reusable functions |

---

## Task 1

**Chapter:** Variables & Data Types

### Feature / Mission

Create a basic measurement display.

The application stores a measurement's value and unit, then displays them.

### Assignments

- [ ] Create a decimal variable to store the measurement.
- [ ] Create a character variable to store its unit.
- [ ] Display the measurement.

### Code

```c
#include <stdio.h>

int main(void) {
    double value = 5.0;
    char unit = 'm';

    printf("%.2f %c\n", value, unit);

    return 0;
}
```

### Explanation

- `double` stores a decimal number.
- `char` stores a single character.
- `=` initializes a variable.
- `printf()` displays the measurement.
- `%f` formats a floating-point number.
- `%c` formats a character.

### Expected Output

```text
5.00 m
```

---

## Task 2

**Chapter:** Constants & Arithmetic Operators

### Feature / Mission

Convert a measurement from meters to centimeters.

Instead of displaying a hardcoded result, the application calculates it using a conversion factor.

### Assignments

- [ ] Define a constant for the number of centimeters in one meter.
- [ ] Multiply the measurement by the conversion factor.
- [ ] Store the calculated result.
- [ ] Display the original measurement and converted result.

### Code

```c
#include <stdio.h>

int main(void) {
    const double CM_PER_METER = 100.0;

    double value = 5.0;
    double result = value * CM_PER_METER;

    printf("%.2f m = %.2f cm\n", value, result);

    return 0;
}
```

### Explanation

- `const` defines a value that cannot be reassigned.
- `*` multiplies two numbers.
- `result` stores the calculated conversion.

### Expected Output

```text
5.00 m = 500.00 cm
```

---

## Task 3

**Chapter:** Input & Output

### Feature / Mission

Allow the user to enter the measurement they want to convert.

The application should no longer require source-code changes to convert a different value.

### Assignments

- [ ] Ask the user to enter a value in meters.
- [ ] Read the value from the keyboard.
- [ ] Convert the entered value into centimeters.
- [ ] Display the result.

### Code

```c
#include <stdio.h>

int main(void) {
    const double CM_PER_METER = 100.0;

    double value;

    printf("Enter meters: ");
    scanf("%lf", &value);

    double result = value * CM_PER_METER;

    printf("%.2f m = %.2f cm\n", value, result);

    return 0;
}
```

### Explanation

- `scanf()` reads user input.
- `%lf` reads a `double`.
- `&value` gives `scanf()` the variable's memory address.
- The entered value is used in the calculation.

### Example

```text
Enter meters: 2.5
2.50 m = 250.00 cm
```

---

## Task 4

**Chapter:** Conditional Statements

### Feature / Mission

Allow the user to choose the direction of the conversion.

The converter now supports both meters to centimeters and centimeters to meters.

### Assignments

- [ ] Display two conversion options.
- [ ] Ask the user to select an option.
- [ ] Ask for the measurement.
- [ ] Use `switch` to perform the selected calculation.
- [ ] Reject invalid menu choices.
- [ ] Reject invalid numeric input.
- [ ] Use `if` to reject negative lengths.

### Code

```c
#include <stdio.h>

int main(void) {
    const double CM_PER_METER = 100.0;

    int choice;
    double value;
    double result;

    printf("1. Meters to Centimeters\n");
    printf("2. Centimeters to Meters\n");
    printf("Choice: ");

    if (scanf("%d", &choice) != 1) {
        printf("Invalid input.\n");
        return 1;
    }

    if (choice != 1 && choice != 2) {
        printf("Invalid choice.\n");
        return 1;
    }

    printf("Enter value: ");

    if (scanf("%lf", &value) != 1 || value < 0) {
        printf("Invalid measurement.\n");
        return 1;
    }

    switch (choice) {
        case 1:
            result = value * CM_PER_METER;
            printf("%.2f m = %.2f cm\n", value, result);
            break;

        case 2:
            result = value / CM_PER_METER;
            printf("%.2f cm = %.2f m\n", value, result);
            break;
    }

    return 0;
}
```

### Explanation

- `int` stores the selected menu option.
- `if` checks conditions.
- `!=` checks whether two values are different.
- `&&` means logical AND.
- `||` means logical OR.
- `switch` selects the appropriate conversion.
- `case` defines an option.
- `break` exits the `switch`.
- `/` converts centimeters back to meters.

### Example

```text
1. Meters to Centimeters
2. Centimeters to Meters
Choice: 2
Enter value: 250
250.00 cm = 2.50 m
```

---

## Task 5

**Chapter:** Loops

### Feature / Mission

Allow users to perform multiple conversions during one session.

Add an exit option and keep the program running until the user chooses to close it.

### Assignments

- [ ] Display the conversion menu repeatedly.
- [ ] Add an option to exit.
- [ ] Use `do...while` to keep the application running.
- [ ] Use `continue` to restart the menu after invalid input.
- [ ] Use `break` to exit the application.
- [ ] Keep a count of successful conversions.
- [ ] Display the number of conversions when exiting.

### Code

```c
#include <stdio.h>

int main(void) {
    const double CM_PER_METER = 100.0;

    int choice;
    int count = 0;
    double value;
    double result;

    do {
        printf("\n1. Meters to Centimeters\n");
        printf("2. Centimeters to Meters\n");
        printf("3. Exit\n");
        printf("Choice: ");

        if (scanf("%d", &choice) != 1) {
            int ch;
            while ((ch = getchar()) != '\n' && ch != EOF) {
            }
            printf("Invalid input.\n");
            continue;
        }

        if (choice == 3) {
            break;
        }

        if (choice != 1 && choice != 2) {
            printf("Invalid choice.\n");
            continue;
        }

        printf("Enter value: ");

        if (scanf("%lf", &value) != 1) {
            int ch;
            while ((ch = getchar()) != '\n' && ch != EOF) {
            }
            printf("Invalid input.\n");
            continue;
        }

        if (value < 0) {
            printf("Measurement cannot be negative.\n");
            continue;
        }

        switch (choice) {
            case 1:
                result = value * CM_PER_METER;
                printf("%.2f m = %.2f cm\n", value, result);
                break;

            case 2:
                result = value / CM_PER_METER;
                printf("%.2f cm = %.2f m\n", value, result);
                break;
        }

        count++;

    } while (1);

    printf("Total conversions: %d\n", count);

    return 0;
}
```

### Explanation

- `do...while` repeats a block of code.
- `while` can also repeat code while a condition remains true.
- `break` exits a loop.
- `continue` skips to the next iteration.
- `++` increases a counter by one.
- The input buffer is cleared after invalid text input.

### Example

```text
1. Meters to Centimeters
2. Centimeters to Meters
3. Exit
Choice: 1
Enter value: 3
3.00 m = 300.00 cm

1. Meters to Centimeters
2. Centimeters to Meters
3. Exit
Choice: 3
Total conversions: 1
```

---

## Task 6

**Chapter:** Arrays & Strings

### Feature / Mission

Save completed conversions so the user can view earlier measurements.

Add a history menu and the ability to search for a saved conversion by its number.

### Assignments

- [ ] Create arrays to store original and converted values.
- [ ] Save the conversion type for each record.
- [ ] Store up to 100 conversions.
- [ ] Add an option to display all saved conversions.
- [ ] Use a `for` loop to list history.
- [ ] Add an option to retrieve a conversion by its history number.
- [ ] Reject history indexes outside the saved range.
- [ ] Display conversion names using a string array.

### Code

```c
#include <stdio.h>

#define MAX_HISTORY 100

int main(void) {
    const double CM_PER_METER = 100.0;

    double originals[MAX_HISTORY];
    double results[MAX_HISTORY];
    int types[MAX_HISTORY];

    const char *names[] = {
        "Meters to Centimeters",
        "Centimeters to Meters"
    };

    int count = 0;
    int choice;

    do {
        printf("\n1. Convert\n");
        printf("2. View History\n");
        printf("3. Find Conversion\n");
        printf("4. Exit\n");
        printf("Choice: ");

        if (scanf("%d", &choice) != 1) {
            int ch;
            while ((ch = getchar()) != '\n' && ch != EOF) {
            }
            continue;
        }

        if (choice == 1) {
            if (count == MAX_HISTORY) {
                printf("History is full.\n");
                continue;
            }

            int type;
            double value;
            double result;

            printf("1. Meters to Centimeters\n");
            printf("2. Centimeters to Meters\n");
            printf("Type: ");

            if (scanf("%d", &type) != 1) {
                int ch;
                while ((ch = getchar()) != '\n' && ch != EOF) {
                }
                continue;
            }

            if (type != 1 && type != 2) {
                continue;
            }

            printf("Value: ");

            if (scanf("%lf", &value) != 1) {
                int ch;
                while ((ch = getchar()) != '\n' && ch != EOF) {
                }
                continue;
            }

            if (value < 0) {
                continue;
            }

            if (type == 1) {
                result = value * CM_PER_METER;
            } else {
                result = value / CM_PER_METER;
            }

            originals[count] = value;
            results[count] = result;
            types[count] = type;
            count++;

            printf("Result: %.2f\n", result);

        } else if (choice == 2) {
            for (int i = 0; i < count; i++) {
                printf("%d. %s: %.2f -> %.2f\n",
                       i + 1,
                       names[types[i] - 1],
                       originals[i],
                       results[i]);
            }

        } else if (choice == 3) {
            int number;

            printf("History number: ");

            if (scanf("%d", &number) != 1) {
                int ch;
                while ((ch = getchar()) != '\n' && ch != EOF) {
                }
                continue;
            }

            if (number < 1 || number > count) {
                printf("Conversion not found.\n");
                continue;
            }

            int i = number - 1;

            printf("%s: %.2f -> %.2f\n",
                   names[types[i] - 1],
                   originals[i],
                   results[i]);
        }

    } while (choice != 4);

    return 0;
}
```

### Explanation

- Arrays store multiple values of the same type.
- `[]` accesses an array element.
- Array indexes begin at zero.
- `const char *names[]` stores a collection of strings.
- `for` processes stored records.
- `MAX_HISTORY` prevents writing beyond the allocated array.
- A history number is converted to an array index by subtracting one.

---

## Task 7

**Chapter:** Functions

### Feature / Mission

Organize the converter into reusable functions without changing its functionality.

Separate calculations, menu display, input handling, and conversion history.

### Assignments

- [ ] Create a function to display the menu.
- [ ] Create a function to read an integer.
- [ ] Create a function to read a measurement.
- [ ] Create a function to calculate the conversion.
- [ ] Create a function to display conversion history.
- [ ] Create a function to find a saved conversion.
- [ ] Use function parameters and return values.
- [ ] Keep `main()` responsible for controlling the application.

### Code

```c
#include <stdio.h>

#define MAX_HISTORY 100
#define CM_PER_METER 100.0

void showMenu(void);
int readInteger(void);
int readMeasurement(double *value);
double convert(double value, int type);
void showHistory(
    const double originals[],
    const double results[],
    const int types[],
    int count
);
void findConversion(
    const double originals[],
    const double results[],
    const int types[],
    int count,
    int number
);

const char *names[] = {
    "Meters to Centimeters",
    "Centimeters to Meters"
};

void showMenu(void) {
    printf("\n1. Convert\n");
    printf("2. View History\n");
    printf("3. Find Conversion\n");
    printf("4. Exit\n");
}

int readInteger(void) {
    int value;

    if (scanf("%d", &value) != 1) {
        int ch;
        while ((ch = getchar()) != '\n' && ch != EOF) {
        }
        return -1;
    }

    return value;
}

int readMeasurement(double *value) {
    if (scanf("%lf", value) != 1) {
        int ch;
        while ((ch = getchar()) != '\n' && ch != EOF) {
        }
        return 0;
    }

    return *value >= 0;
}

double convert(double value, int type) {
    if (type == 1) {
        return value * CM_PER_METER;
    }

    return value / CM_PER_METER;
}

void showHistory(
    const double originals[],
    const double results[],
    const int types[],
    int count
) {
    for (int i = 0; i < count; i++) {
        printf("%d. %s: %.2f -> %.2f\n",
               i + 1,
               names[types[i] - 1],
               originals[i],
               results[i]);
    }
}

void findConversion(
    const double originals[],
    const double results[],
    const int types[],
    int count,
    int number
) {
    if (number < 1 || number > count) {
        printf("Conversion not found.\n");
        return;
    }

    int i = number - 1;

    printf("%s: %.2f -> %.2f\n",
           names[types[i] - 1],
           originals[i],
           results[i]);
}

int main(void) {
    double originals[MAX_HISTORY];
    double results[MAX_HISTORY];
    int types[MAX_HISTORY];

    int count = 0;
    int choice;

    do {
        showMenu();

        printf("Choice: ");
        choice = readInteger();

        switch (choice) {
            case 1: {
                if (count == MAX_HISTORY) {
                    printf("History is full.\n");
                    break;
                }

                printf("1. Meters to Centimeters\n");
                printf("2. Centimeters to Meters\n");
                printf("Type: ");

                int type = readInteger();

                if (type != 1 && type != 2) {
                    printf("Invalid type.\n");
                    break;
                }

                double value;

                printf("Value: ");

                if (!readMeasurement(&value)) {
                    printf("Invalid measurement.\n");
                    break;
                }

                double result = convert(value, type);

                originals[count] = value;
                results[count] = result;
                types[count] = type;
                count++;

                printf("Result: %.2f\n", result);
                break;
            }

            case 2:
                showHistory(originals, results, types, count);
                break;

            case 3: {
                printf("History number: ");
                int number = readInteger();

                findConversion(
                    originals,
                    results,
                    types,
                    count,
                    number
                );
                break;
            }

            case 4:
                break;

            default:
                printf("Invalid choice.\n");
        }

    } while (choice != 4);

    return 0;
}
```

### Explanation

- Functions separate different responsibilities.
- Function prototypes declare functions before use.
- Parameters pass information into functions.
- `return` sends values back to the caller.
- `void` indicates that a function returns no value.
- Pointers allow functions to update variables provided by callers.
- `const` parameters protect array data from accidental modification.
- Local variables exist within their scope.

---

## Final Application

The completed program should:

- [ ] Convert meters into centimeters.
- [ ] Convert centimeters into meters.
- [ ] Accept numeric user input.
- [ ] Reject invalid measurements and menu options.
- [ ] Allow repeated conversions.
- [ ] Store up to 100 conversions.
- [ ] Display conversion history.
- [ ] Retrieve a conversion by its history number.
- [ ] Organize logic into reusable functions.

## Repository Structure

```text
c-000-unit-converter/
├── README.md
└── main.c
```

## Compile and Run

```bash
gcc main.c -o converter
./converter
```

## Next Project

**C-001 — Student Management System**

New chapters:

- Structures
- Enumerations
- Typedef
- Pointers and Memory
- Header Files
- Modular Programming
