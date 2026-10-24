
# C-000 — Unit Converter

**Language:** C  
**Level:** Beginner  
**Repository:** `c-000-unit-converter`

## Project

Build a command-line program that converts measurements from one unit to another.

For example:

- Meters ↔ Centimeters
- Kilograms ↔ Grams
- Celsius ↔ Kelvin

You'll start with a simple conversion and gradually turn it into a complete program with a menu, user input, conversion history, and reusable functions.

Each task introduces a new C programming chapter and adds something useful to the program.

## Chapters

| Task | Chapter | Topics |
|---|---|---|
| 1 | Variables & Data Types | `int`, `double`, `char`, declarations, initialization |
| 2 | Constants | `const`, `#define` |
| 3 | Operators | `=`, `+`, `-`, `*`, `/`, `%`, `+=`, `-=`, `*=`, `/=` |
| 4 | Input & Output | `printf`, `scanf`, format specifiers, escape sequences |
| 5 | Conditional Statements | `if`, `else if`, `else`, `switch`, `case`, `default`, logical operators |
| 6 | Loops | `for`, `while`, `do...while`, `break`, `continue` |
| 7 | Arrays & Strings | `[]`, `char[]`, `strlen`, `strcmp`, `strcpy` |
| 8 | Functions | `void`, `return`, parameters, function calls, scope |

---

## Task 1

**Chapter:** Variables & Data Types — `int`, `double`, `char`, declarations, initialization

### Feature / Mission

Create your first conversion record.

For now, you'll store a measurement and its converted value directly in the code. The program should display both values.

### Assignments

- [ ] Create a `double` variable for the original measurement.
- [ ] Create another `double` variable for the converted measurement.
- [ ] Use an `int` variable to give the conversion an ID.
- [ ] Use a `char` variable to store a unit symbol.
- [ ] Use a character array to store the measurement name.
- [ ] Give each variable a starting value.
- [ ] Print the conversion details.

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

- `int` stores whole numbers.
- `double` stores numbers with decimal places.
- `char` stores a single character.
- `char[]` stores text.
- Declaring a variable means creating it with a name and type.
- Initializing a variable means giving it its first value.
- `printf()` displays information on the screen.

---

## Task 2

**Chapter:** Constants — `const`, `#define`

### Feature / Mission

Add fixed values that your converter can use.

Instead of writing numbers like `100` or `1000` everywhere, give them names so they're easier to understand and change.

### Assignments

- [ ] Create a constant called `METERS_TO_CM` with the value `100.0`.
- [ ] Create another constant called `KG_TO_GRAMS` with the value `1000.0`.
- [ ] Use `const` for both conversion factors.
- [ ] Use `#define` to create an application name.
- [ ] Use `#define` to set the maximum number of saved conversions to `100`.
- [ ] Print the conversion factors and settings.
- [ ] Try changing a `const` variable after creating it. See what happens, then remove that line.

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

    printf("Meters to cm: %.2f\n", METERS_TO_CM);
    printf("Kg to grams: %.2f\n", KG_TO_GRAMS);
    printf("Maximum conversions: %d\n", MAX_CONVERSIONS);

    return 0;
}
```

### Explanation

- `const` makes a variable read-only after you initialize it.
- `#define` gives a name to a value or piece of code that the preprocessor substitutes before compilation.
- Named constants make the program easier to read.
- `MAX_CONVERSIONS` will be useful when you add conversion history.

---

## Task 3

**Chapter:** Operators — `=`, `+`, `-`, `*`, `/`, `%`, `+=`, `-=`, `*=`, `/=`

### Feature / Mission

Make the converter actually calculate results.

You'll use arithmetic operators to convert length, mass, and temperature instead of typing the answers yourself.

### Assignments

- [ ] Convert meters to centimeters using `*`.
- [ ] Convert centimeters back to meters using `/`.
- [ ] Convert kilograms to grams.
- [ ] Convert Celsius to Kelvin using `+`.
- [ ] Convert Kelvin back to Celsius using `-`.
- [ ] Use `=` to save a result in a variable.
- [ ] Use `+=` to add the Kelvin offset to a temperature.
- [ ] Use `-=` to remove that offset.
- [ ] Use `*=` to change meters into centimeters.
- [ ] Use `/=` to change centimeters back into meters.
- [ ] Use `%` to split `257` centimeters into whole meters and leftover centimeters.
- [ ] Print the results.

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

    double length = meters;
    length *= METERS_TO_CM;
    length /= METERS_TO_CM;

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

    printf("Restored length: %.2f\n", length);
    printf("Restored temperature: %.2f\n", temperature);

    printf("%d cm = %d m and %d cm\n",
           totalCentimeters,
           wholeMeters,
           remainingCentimeters);

    return 0;
}
```

### Explanation

- `=` saves a value in a variable.
- `+` adds values.
- `-` subtracts values.
- `*` multiplies values.
- `/` divides values.
- `%` gives the remainder of integer division.
- `+=` adds to the current value.
- `-=` subtracts from the current value.
- `*=` multiplies the current value.
- `/=` divides the current value.

---

## Task 4

**Chapter:** Input & Output — `printf`, `scanf`, format specifiers, escape sequences

### Feature / Mission

Let users enter their own measurements.

The program should ask for a length, mass, and temperature, then display the converted values.

### Assignments

- [ ] Print a welcome message.
- [ ] Ask the user for a length in meters.
- [ ] Read the length using `scanf()`.
- [ ] Ask for a mass in kilograms.
- [ ] Ask for a temperature in Celsius.
- [ ] Read decimal numbers using `%lf`.
- [ ] Calculate the three conversions.
- [ ] Print the results using `%.2f`.
- [ ] Use `%s` to display unit names.
- [ ] Use `%d` to display the number of conversions.
- [ ] Use `\n` to put text on a new line.
- [ ] Use `\t` to separate labels from values.

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
    printf("Conversions completed: %d\n", 3);

    return 0;
}
```

### Explanation

- `printf()` prints text and values.
- `scanf()` reads what the user types.
- `%lf` reads a `double` in `scanf()`.
- `%.2f` prints a number with two decimal places.
- `%s` prints text.
- `%d` prints an integer.
- `\n` starts a new line.
- `\t` adds a tab.
- `&` passes a variable's address to `scanf()`.

---

## Task 5

**Chapter:** Conditional Statements — `if`, `else if`, `else`, `switch`, `case`, `default`, comparison and logical operators

### Feature / Mission

Let users choose what they want to convert.

Instead of converting everything at once, the program should show a few options and perform only the selected conversion.

It should also reject invalid values.

### Assignments

- [ ] Show three conversion options: length, mass, and temperature.
- [ ] Ask the user to choose an option.
- [ ] Use `switch` to handle the selected conversion.
- [ ] Use `case` for each option.
- [ ] Use `default` for unsupported options.
- [ ] Use `if` to check whether the input is valid.
- [ ] Reject negative mass values.
- [ ] Reject temperatures below absolute zero.
- [ ] Use `else if` and `else` to classify temperatures.
- [ ] Use comparison operators such as `<`, `>`, `<=`, `>=`, and `==`.
- [ ] Use `&&` and `||` to combine conditions.
- [ ] Print the result of the selected conversion.

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
        printf("Please enter a valid number.\n");
        return 1;
    }

    if (choice < 1 || choice > 3) {
        printf("Invalid option.\n");
        return 1;
    }

    printf("Value: ");
    if (scanf("%lf", &value) != 1) {
        printf("Please enter a valid measurement.\n");
        return 1;
    }

    if (choice == 2 && value < 0) {
        printf("Mass cannot be negative.\n");
        return 1;
    }

    if (choice == 3 && value < -273.15) {
        printf("Temperature cannot be below absolute zero.\n");
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

- `if` runs code when a condition is true.
- `else if` checks another condition.
- `else` handles the remaining situation.
- `switch` chooses which block of code to run.
- `case` represents one possible choice.
- `break` stops execution from falling into the next case.
- `default` handles unexpected choices.
- `&&` means AND.
- `||` means OR.
- Comparison operators compare values.

---

## Task 6

**Chapter:** Loops — `for`, `while`, `do...while`, `break`, `continue`

### Feature / Mission

Keep the converter running until the user chooses to exit.

Users should be able to perform several conversions in one session without restarting the program.

### Assignments

- [ ] Create a menu with conversion options.
- [ ] Add an Exit option.
- [ ] Use `do...while` to keep showing the menu.
- [ ] Use `for` to print the menu options.
- [ ] Use `while` to ask again when the menu input isn't a number.
- [ ] Use `continue` to return to the menu after an invalid choice.
- [ ] Use `break` to exit.
- [ ] Count successful conversions.
- [ ] Show the conversion count when the user exits.

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

- `for` repeats code a known number of times.
- `while` keeps running as long as its condition is true.
- `do...while` runs the code at least once.
- `break` exits the nearest loop.
- `continue` skips the rest of the current loop iteration.
- `conversionCount` keeps track of completed conversions.

---

## Task 7

**Chapter:** Arrays & Strings — `[]`, `char[]`, `strlen`, `strcmp`, `strcpy`

### Feature / Mission

Add conversion history.

Every time the user completes a conversion, the program should save it. Users should then be able to view their previous conversions or search for a specific conversion type.

### Assignments

- [ ] Create an array for original values.
- [ ] Create an array for converted values.
- [ ] Create a two-dimensional character array for conversion names.
- [ ] Allow up to `100` saved conversions.
- [ ] Keep track of how many conversions have been saved.
- [ ] Save each new conversion in the next available position.
- [ ] Use `strlen()` to check that conversion names aren't empty.
- [ ] Use `strcpy()` to save conversion names.
- [ ] Use `strcmp()` to find conversions by name.
- [ ] Add a List History option to the menu.
- [ ] Add a Search History option.
- [ ] Print all saved conversions.
- [ ] Stop adding records when the history is full.

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

- `[]` is used to create arrays and access their elements.
- Arrays let you store several values of the same type.
- Two-dimensional character arrays can store multiple names.
- `char[]` stores text.
- `strlen()` gives the length of a string.
- `strcmp()` compares two strings.
- `strcpy()` copies text into another character array.
- Array positions start at index `0`.
- `count` tells the program how many conversions are stored.

---

## Task 8

**Chapter:** Functions — `void`, `return`, parameters, function calls, scope

### Feature / Mission

Clean up the converter by splitting it into functions.

Instead of putting everything inside `main()`, create separate functions for the menu, conversions, and history.

By the end of this task, all the features from the earlier tasks should work together in one application.

### Assignments

- [ ] Create a function that displays the menu.
- [ ] Create a function that converts meters to centimeters.
- [ ] Create a function that converts centimeters to meters.
- [ ] Create a function that converts kilograms to grams.
- [ ] Create a function that converts grams to kilograms.
- [ ] Create a function that converts Celsius to Kelvin.
- [ ] Create a function that converts Kelvin to Celsius.
- [ ] Create a function that saves a conversion to history.
- [ ] Create a function that displays conversion history.
- [ ] Create a function that searches conversion history.
- [ ] Write function prototypes before `main()`.
- [ ] Give functions parameters when they need input.
- [ ] Use `return` to send calculated values back.
- [ ] Use `void` for functions that don't return anything.
- [ ] Pass arrays and counts to history functions.
- [ ] Keep temporary calculations in local variables.
- [ ] Connect all the functions to the main menu.

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

- A function is a reusable block of code.
- A function prototype tells C about a function before it's defined.
- Parameters let you pass values into functions.
- `return` sends a result back.
- `void` means a function doesn't return a value.
- Local variables belong to the function or block where they're declared.
- Functions make the program easier to organize and update.
- You can call the same function whenever you need that conversion.

---

## Final Application Checklist

- [ ] Convert meters to centimeters.
- [ ] Convert centimeters to meters.
- [ ] Convert kilograms to grams.
- [ ] Convert grams to kilograms.
- [ ] Convert Celsius to Kelvin.
- [ ] Convert Kelvin to Celsius.
- [ ] Let users enter their own values.
- [ ] Reject invalid inputs.
- [ ] Show conversion results.
- [ ] Keep the menu running until the user exits.
- [ ] Save up to 100 conversions.
- [ ] Show conversion history.
- [ ] Search conversion history.
- [ ] Count successful conversions.
- [ ] Organize the program using functions.

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
