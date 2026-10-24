
# C-000 — Unit Converter

**Language:** C  
**Level:** Beginner  
**Repository:** `c-000-unit-converter`

## Project Overview

Build a command-line Unit Converter in C.

The application allows users to convert values between different units of measurement, including length, mass, and temperature.

Each task introduces one programming chapter and incrementally extends the same application.

## Chapters

| Task | Chapter | Programming Keywords / Concepts |
|---|---|---|
| 1 | Variables & Data Types | `int`, `double`, `char`, declaration, initialization |
| 2 | Constants | `const`, `#define` |
| 3 | Operators | `=`, `+`, `-`, `*`, `/`, `%`, `+=`, `-=`, `*=`, `/=` |
| 4 | Input & Output | `printf`, `scanf`, format specifiers, escape sequences |
| 5 | Conditional Statements | `if`, `else if`, `else`, `switch`, `case`, `default`, comparison and logical operators |
| 6 | Loops | `for`, `while`, `do...while`, `break`, `continue` |
| 7 | Arrays & Strings | `[]`, `char[]`, `strlen`, `strcmp`, `strcpy` |
| 8 | Functions | `void`, `return`, parameters, function calls, scope |

---

## Task 1

**Chapter:** Variables & Data Types — `int`, `double`, `char`, declaration, initialization

### Feature / Mission

Create the initial unit conversion record containing a measurement name, source value, target value, and unit symbols.

### Assignments

- [ ] Declare a `double` variable to store a measurement value.
- [ ] Declare another `double` variable to store the converted value.
- [ ] Declare an `int` variable to store a conversion identifier.
- [ ] Declare a `char` variable to store a single-character unit symbol.
- [ ] Declare a character array to store the measurement name.
- [ ] Initialize all variables with example values.
- [ ] Display the measurement information.

### Code

```c
#include <stdio.h>

int main(void) {
    char measurement[] = "Length";
    char unit = 'm';

    int conversionId = 1;

    double value = 5.0;
    double convertedValue = 500.0;

    printf("Measurement: %s\n", measurement);
    printf("Conversion ID: %d\n", conversionId);
    printf("Original: %.2f %c\n", value, unit);
    printf("Converted: %.2f cm\n", convertedValue);

    return 0;
}
```

### Explanation

- `int` stores integer values.
- `double` stores floating-point values.
- `char` stores a single character.
- `char[]` stores a sequence of characters.
- Declaration creates a named variable with a specific type.
- Initialization assigns an initial value.
- `printf()` displays the values. Formatted input and output are covered in Task 4.

---

## Task 2

**Chapter:** Constants — `const`, `#define`

### Feature / Mission

Introduce fixed conversion factors and configuration values so the application can use standardized measurement relationships.

### Assignments

- [ ] Declare a constant named `METERS_TO_CM` using `const`.
- [ ] Initialize `METERS_TO_CM` with `100.0`.
- [ ] Declare a constant named `KG_TO_GRAMS` with the value `1000.0`.
- [ ] Define `APP_NAME` using `#define`.
- [ ] Define `MAX_CONVERSIONS` with the value `100`.
- [ ] Display the configured conversion factors.
- [ ] Display the application name and conversion limit.
- [ ] Experiment with modifying a `const` variable and observe the compilation error, then remove the invalid statement.

### Code

```c
#include <stdio.h>

#define APP_NAME "Unit Converter"
#define MAX_CONVERSIONS 100

int main(void) {
    const double METERS_TO_CM = 100.0;
    const double KG_TO_GRAMS = 1000.0;

    double value = 5.0;
    double convertedValue = 500.0;

    printf("%s\n", APP_NAME);
    printf("Original: %.2f meters\n", value);
    printf("Converted: %.2f centimeters\n", convertedValue);

    printf("Meters to centimeters factor: %.2f\n", METERS_TO_CM);
    printf("Kilograms to grams factor: %.2f\n", KG_TO_GRAMS);
    printf("Maximum conversions: %d\n", MAX_CONVERSIONS);

    return 0;
}
```

### Explanation

- `const` declares a read-only variable.
- `#define` creates a preprocessor macro.
- `METERS_TO_CM` and `KG_TO_GRAMS` are typed constants.
- `APP_NAME` is a string macro.
- `MAX_CONVERSIONS` defines the future history capacity.
- Constants avoid scattering hardcoded configuration values throughout the application.

---

## Task 3

**Chapter:** Operators — `=`, `+`, `-`, `*`, `/`, `%`, `+=`, `-=`, `*=`, `/=`

### Feature / Mission

Implement actual unit conversion calculations for length, mass, and temperature using arithmetic operators.

### Assignments

- [ ] Convert meters to centimeters using multiplication.
- [ ] Convert centimeters to meters using division.
- [ ] Convert kilograms to grams using multiplication.
- [ ] Convert Celsius to Kelvin using addition.
- [ ] Convert Kelvin to Celsius using subtraction.
- [ ] Use `=` to assign conversion results.
- [ ] Use `+=` to add an offset to a temperature value.
- [ ] Use `-=` to remove the offset.
- [ ] Use `*=` to convert meters to centimeters.
- [ ] Use `/=` to convert centimeters back to meters.
- [ ] Use `%` to calculate the remaining centimeters after extracting whole meters from an integer centimeter measurement.
- [ ] Display all calculated results.

### Code

```c
#include <stdio.h>

int main(void) {
    const double METERS_TO_CM = 100.0;
    const double KG_TO_GRAMS = 1000.0;
    const double KELVIN_OFFSET = 273.15;

    double meters = 5.0;
    double centimeters = meters * METERS_TO_CM;
    double metersAgain = centimeters / METERS_TO_CM;

    double kilograms = 2.5;
    double grams = kilograms * KG_TO_GRAMS;

    double celsius = 25.0;
    double kelvin = celsius + KELVIN_OFFSET;
    double celsiusAgain = kelvin - KELVIN_OFFSET;

    double result = meters;
    result *= METERS_TO_CM;
    result /= METERS_TO_CM;

    double temperature = celsius;
    temperature += KELVIN_OFFSET;
    temperature -= KELVIN_OFFSET;

    int totalCentimeters = 257;
    int wholeMeters = totalCentimeters / 100;
    int remainingCentimeters = totalCentimeters % 100;

    printf("Meters to cm: %.2f\n", centimeters);
    printf("Cm to meters: %.2f\n", metersAgain);
    printf("Kg to grams: %.2f\n", grams);
    printf("Celsius to Kelvin: %.2f\n", kelvin);
    printf("Kelvin to Celsius: %.2f\n", celsiusAgain);

    printf("Restored length: %.2f\n", result);
    printf("Restored temperature: %.2f\n", temperature);

    printf("%d cm = %d m and %d cm\n",
           totalCentimeters,
           wholeMeters,
           remainingCentimeters);

    return 0;
}
```

### Explanation

- `=` assigns values.
- `+` adds a temperature offset.
- `-` removes a temperature offset.
- `*` multiplies a measurement by a conversion factor.
- `/` divides a measurement by a conversion factor.
- `%` calculates an integer remainder.
- `+=` adds to an existing variable.
- `-=` subtracts from an existing variable.
- `*=` multiplies an existing variable.
- `/=` divides an existing variable.
- Integer division discards the fractional part.

---

## Task 4

**Chapter:** Input & Output — `printf`, `scanf`, format specifiers, escape sequences

### Feature / Mission

Allow users to enter measurement values and receive calculated conversion results instead of relying on hardcoded values.

### Assignments

- [ ] Display the application title using `printf()`.
- [ ] Ask the user to enter a length in meters.
- [ ] Read the length using `scanf()` and `%lf`.
- [ ] Ask the user to enter a mass in kilograms.
- [ ] Read the mass using `%lf`.
- [ ] Ask the user to enter a temperature in Celsius.
- [ ] Calculate the corresponding conversions.
- [ ] Display results using `%.2f`.
- [ ] Use `\n` to separate lines.
- [ ] Use `\t` to align conversion information.
- [ ] Use `%s` to display unit names.
- [ ] Use `%d` to display the number of completed conversions.

### Code

```c
#include <stdio.h>

#define APP_NAME "Unit Converter"

int main(void) {
    const double METERS_TO_CM = 100.0;
    const double KG_TO_GRAMS = 1000.0;
    const double KELVIN_OFFSET = 273.15;

    double meters;
    double kilograms;
    double celsius;

    int conversionCount = 3;

    printf("===== %s =====\n", APP_NAME);

    printf("Enter length in meters: ");
    scanf("%lf", &meters);

    printf("Enter mass in kilograms: ");
    scanf("%lf", &kilograms);

    printf("Enter temperature in Celsius: ");
    scanf("%lf", &celsius);

    double centimeters = meters * METERS_TO_CM;
    double grams = kilograms * KG_TO_GRAMS;
    double kelvin = celsius + KELVIN_OFFSET;

    printf("\n===== RESULTS =====\n");
    printf("Length:\t%.2f %s\n", centimeters, "cm");
    printf("Mass:\t%.2f %s\n", grams, "g");
    printf("Temperature:\t%.2f %s\n", kelvin, "K");

    printf("Conversions completed: %d\n", conversionCount);

    return 0;
}
```

### Explanation

- `printf()` displays formatted output.
- `scanf()` reads formatted input.
- `%lf` reads a `double` with `scanf()`.
- `%.2f` displays a floating-point value with two decimal places.
- `%s` displays a string.
- `%d` displays an integer.
- `\n` inserts a newline.
- `\t` inserts a horizontal tab.
- `&` supplies the address of a variable to `scanf()`.

---

## Task 5

**Chapter:** Conditional Statements — `if`, `else if`, `else`, `switch`, `case`, `default`, comparison and logical operators

### Feature / Mission

Allow users to select a conversion type, validate the input value, and execute the appropriate calculation.

### Assignments

- [ ] Display conversion options for length, mass, and temperature.
- [ ] Ask the user to select a conversion type.
- [ ] Use `switch` to process the selected option.
- [ ] Use `case` for each supported conversion.
- [ ] Use `default` to reject unsupported options.
- [ ] Use `if` to validate measurement values.
- [ ] Use `else if` to classify a temperature as below freezing, freezing, or above freezing.
- [ ] Use `else` for the remaining classification.
- [ ] Use `&&` to verify a value is within a valid interval.
- [ ] Use `||` to reject invalid menu options.
- [ ] Reject negative mass values.
- [ ] Reject Celsius temperatures below absolute zero.
- [ ] Display the conversion result.

### Code

```c
#include <stdio.h>

int main(void) {
    const double METERS_TO_CM = 100.0;
    const double KG_TO_GRAMS = 1000.0;
    const double KELVIN_OFFSET = 273.15;

    int choice;
    double value;
    double result;

    printf("1. Meters to Centimeters\n");
    printf("2. Kilograms to Grams\n");
    printf("3. Celsius to Kelvin\n");

    printf("Choice: ");
    if (scanf("%d", &choice) != 1) {
        printf("Invalid menu input.\n");
        return 1;
    }

    if (choice < 1 || choice > 3) {
        printf("Invalid conversion type.\n");
        return 1;
    }

    printf("Value: ");
    if (scanf("%lf", &value) != 1) {
        printf("Invalid measurement input.\n");
        return 1;
    }

    if (choice == 2 && value < 0) {
        printf("Mass cannot be negative.\n");
        return 1;
    }

    if (choice == 3 && value < -273.15) {
        printf("Temperature is below absolute zero.\n");
        return 1;
    }

    if (choice == 3 && value >= -273.15) {
        if (value < 0) {
            printf("Below freezing.\n");
        } else if (value == 0) {
            printf("At freezing point.\n");
        } else {
            printf("Above freezing.\n");
        }
    }

    switch (choice) {
        case 1:
            result = value * METERS_TO_CM;
            printf("%.2f cm\n", result);
            break;

        case 2:
            result = value * KG_TO_GRAMS;
            printf("%.2f g\n", result);
            break;

        case 3:
            result = value + KELVIN_OFFSET;
            printf("%.2f K\n", result);
            break;

        default:
            printf("Unsupported conversion.\n");
            return 1;
    }

    return 0;
}
```

### Explanation

- `if` executes code when a condition is true.
- `else if` checks additional conditions.
- `else` handles the remaining case.
- `switch` selects a branch based on a value.
- `case` identifies a matching branch.
- `break` prevents execution from continuing into subsequent cases.
- `default` handles unmatched values.
- `&&` requires both conditions to be true.
- `||` requires at least one condition to be true.
- Comparison operators such as `<`, `>`, `<=`, `>=`, and `==` evaluate relationships between values.

---

## Task 6

**Chapter:** Loops — `for`, `while`, `do...while`, `break`, `continue`

### Feature / Mission

Create an interactive conversion menu that allows users to perform multiple conversions without restarting the application.

### Assignments

- [ ] Create a menu with conversion options.
- [ ] Add an Exit option.
- [ ] Use `do...while` to keep the application running.
- [ ] Use `for` to display menu options.
- [ ] Use `while` to request valid numeric input.
- [ ] Use `continue` to restart the menu after invalid choices.
- [ ] Use `break` to exit the application.
- [ ] Track the number of successful conversions.
- [ ] Display the total conversion count before exiting.
- [ ] Allow multiple conversions during one application session.

### Code

```c
#include <stdio.h>

int main(void) {
    const double METERS_TO_CM = 100.0;
    const double KG_TO_GRAMS = 1000.0;
    const double KELVIN_OFFSET = 273.15;

    const char *options[] = {
        "Meters to Centimeters",
        "Kilograms to Grams",
        "Celsius to Kelvin",
        "Exit"
    };

    int choice = 0;
    int conversionCount = 0;

    do {
        printf("\n===== UNIT CONVERTER =====\n");

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

        if (choice < 1 || choice > 4) {
            printf("Invalid choice.\n");
            continue;
        }

        if (choice == 4) {
            break;
        }

        double value;
        double result;

        printf("Value: ");

        if (scanf("%lf", &value) != 1) {
            int ch;

            while ((ch = getchar()) != '\n' && ch != EOF) {
            }

            printf("Invalid value.\n");
            continue;
        }

        if ((choice == 2 && value < 0) ||
            (choice == 3 && value < -273.15)) {
            printf("Value outside the valid range.\n");
            continue;
        }

        switch (choice) {
            case 1:
                result = value * METERS_TO_CM;
                printf("%.2f cm\n", result);
                break;

            case 2:
                result = value * KG_TO_GRAMS;
                printf("%.2f g\n", result);
                break;

            case 3:
                result = value + KELVIN_OFFSET;
                printf("%.2f K\n", result);
                break;
        }

        conversionCount++;

    } while (choice != 4);

    printf("Conversions completed: %d\n", conversionCount);

    return 0;
}
```

### Explanation

- `for` repeats code using initialization, condition, and update expressions.
- `while` repeats while a condition remains true.
- `do...while` executes at least once before checking its condition.
- `break` terminates the nearest enclosing loop.
- `continue` skips the remaining statements in the current iteration.
- `conversionCount` tracks successful conversions across menu iterations.

---

## Task 7

**Chapter:** Arrays & Strings — `[]`, `char[]`, `strlen`, `strcmp`, `strcpy`

### Feature / Mission

Add conversion history so users can store, list, and search up to 100 previously completed conversions.

### Assignments

- [ ] Create an array for original measurement values.
- [ ] Create an array for converted values.
- [ ] Create a two-dimensional character array for conversion names.
- [ ] Use `MAX_CONVERSIONS` to limit history storage.
- [ ] Track the number of stored conversions.
- [ ] Store each successful conversion at the next available index.
- [ ] Use `strlen()` to validate conversion names.
- [ ] Use `strcpy()` to copy conversion names into history.
- [ ] Use `strcmp()` to search conversion history by name.
- [ ] Add a List History option to the menu.
- [ ] Add a Search History option to the menu.
- [ ] Display all stored conversions using array traversal.
- [ ] Prevent array overflow.

### Code

```c
#include <stdio.h>
#include <string.h>

#define MAX_CONVERSIONS 100
#define NAME_LENGTH 50

int main(void) {
    char conversionNames[MAX_CONVERSIONS][NAME_LENGTH];
    double originalValues[MAX_CONVERSIONS];
    double convertedValues[MAX_CONVERSIONS];

    int count = 0;

    char name[] = "Meters to Centimeters";
    double original = 5.0;
    double converted = original * 100.0;

    if (count < MAX_CONVERSIONS &&
        strlen(name) > 0 &&
        strlen(name) < NAME_LENGTH) {

        strcpy(conversionNames[count], name);
        originalValues[count] = original;
        convertedValues[count] = converted;

        count++;
    }

    printf("\n===== CONVERSION HISTORY =====\n");

    for (int i = 0; i < count; i++) {
        printf("%d. %s: %.2f -> %.2f\n",
               i + 1,
               conversionNames[i],
               originalValues[i],
               convertedValues[i]);
    }

    char searchName[] = "Meters to Centimeters";

    printf("\n===== SEARCH RESULTS =====\n");

    for (int i = 0; i < count; i++) {
        if (strcmp(conversionNames[i], searchName) == 0) {
            printf("Found: %.2f -> %.2f\n",
                   originalValues[i],
                   convertedValues[i]);
        }
    }

    return 0;
}
```

### Explanation

- `[]` declares arrays and accesses their elements.
- One-dimensional arrays store multiple values of the same type.
- Two-dimensional character arrays can store multiple strings.
- `char[]` stores null-terminated strings.
- `strlen()` calculates string length.
- `strcmp()` compares strings.
- `strcpy()` copies strings into sufficiently large destination arrays.
- Array indexing begins at zero.
- Array traversal processes stored elements using loops.
- `count` tracks the number of stored conversions.

---

## Task 8

**Chapter:** Functions — `void`, `return`, parameters, function calls, scope

### Feature / Mission

Organize the Unit Converter into reusable functions, integrate conversion history, and create a complete interactive application.

### Assignments

- [ ] Create a function to display the application menu.
- [ ] Create a function to convert meters to centimeters.
- [ ] Create a function to convert centimeters to meters.
- [ ] Create a function to convert kilograms to grams.
- [ ] Create a function to convert grams to kilograms.
- [ ] Create a function to convert Celsius to Kelvin.
- [ ] Create a function to convert Kelvin to Celsius.
- [ ] Create a function to add a conversion to history.
- [ ] Create a function to list conversion history.
- [ ] Create a function to search conversion history.
- [ ] Declare function prototypes before `main()`.
- [ ] Define functions with appropriate parameters.
- [ ] Use `void` for functions that do not return values.
- [ ] Use `return` to return calculated results.
- [ ] Pass arrays and conversion counts to functions.
- [ ] Use local variables for intermediate calculations.
- [ ] Integrate all functions into the interactive menu.

### Code

```c
#include <stdio.h>

void showMenu(void);

double metersToCentimeters(double meters);
double centimetersToMeters(double centimeters);

double kilogramsToGrams(double kilograms);
double gramsToKilograms(double grams);

double celsiusToKelvin(double celsius);
double kelvinToCelsius(double kelvin);

void showMenu(void) {
    printf("\n===== UNIT CONVERTER =====\n");

    printf("1. Meters to Centimeters\n");
    printf("2. Centimeters to Meters\n");
    printf("3. Kilograms to Grams\n");
    printf("4. Grams to Kilograms\n");
    printf("5. Celsius to Kelvin\n");
    printf("6. Kelvin to Celsius\n");
    printf("7. List History\n");
    printf("8. Search History\n");
    printf("9. Exit\n");
}

double metersToCentimeters(double meters) {
    return meters * 100.0;
}

double centimetersToMeters(double centimeters) {
    return centimeters / 100.0;
}

double kilogramsToGrams(double kilograms) {
    return kilograms * 1000.0;
}

double gramsToKilograms(double grams) {
    return grams / 1000.0;
}

double celsiusToKelvin(double celsius) {
    return celsius + 273.15;
}

double kelvinToCelsius(double kelvin) {
    return kelvin - 273.15;
}
```

### Explanation

- Function declarations introduce functions before their definitions.
- Function definitions contain reusable implementations.
- Parameters allow functions to receive measurement values.
- Function calls execute reusable code.
- `void` indicates that a function returns no value.
- `return` sends a calculated result to the caller.
- Local variables exist within their declaring scope.
- Function reuse avoids duplicated conversion formulas.
- Passing arrays allows functions to process conversion history.

---

## Final Application Requirements

- [ ] Convert meters to centimeters.
- [ ] Convert centimeters to meters.
- [ ] Convert kilograms to grams.
- [ ] Convert grams to kilograms.
- [ ] Convert Celsius to Kelvin.
- [ ] Convert Kelvin to Celsius.
- [ ] Accept measurement values from the user.
- [ ] Validate measurement values and menu input.
- [ ] Display formatted conversion results.
- [ ] Perform multiple conversions in one session.
- [ ] Store up to 100 conversions.
- [ ] List conversion history.
- [ ] Search conversion history by name.
- [ ] Track the number of successful conversions.
- [ ] Use reusable functions for conversions and history operations.
- [ ] Exit the application safely.

## Repository Structure

```text
c-000-unit-converter/
├── README.md
└── main.c
```

## Next Project

**C-001 — Student Management System**

**Repository:** `c-001-student-management`

New programming chapters:

- Structures
- Enumerations
- Typedef
- Data Modeling
- Modular Programming
- Header Files
