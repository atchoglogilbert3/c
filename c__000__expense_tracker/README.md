
# C-000 — Expense Tracker

**Language:** C  
**Level:** Beginner  
**Repository:** `c-000-expense-tracker`

## Project Overview

Build a command-line Expense Tracker in C.

The application allows users to create expenses, calculate costs, validate amounts, store multiple expenses, and calculate spending statistics.

Each task introduces one programming chapter and extends the existing application.

## Chapters

| Task | Chapter | Programming Keywords / Concepts |
|---|---|---|
| 1 | Variables & Data Types | `int`, `double`, `char`, declaration, initialization |
| 2 | Constants | `const`, `#define` |
| 3 | Operators | `=`, `+`, `-`, `*`, `/`, `%`, `+=`, `-=`, `*=`, `/=` |
| 4 | Input & Output | `printf`, `scanf`, format specifiers |
| 5 | Conditional Statements | `if`, `else`, `switch`, `case`, `default` |
| 6 | Loops | `for`, `while`, `do`, `break`, `continue` |
| 7 | Arrays & Strings | `[]`, `char[]`, `strlen`, `strcmp`, `strcpy` |
| 8 | Functions | `void`, `return`, parameters, function calls |

---

## Task 1

**Chapter:** Variables & Data Types — `int`, `double`, `char`, declaration, initialization

### Assignments

- [ ] Declare a character array to store an expense name.
- [ ] Declare a `double` variable to store the unit price.
- [ ] Declare an `int` variable to store the quantity purchased.
- [ ] Initialize all variables with example values.
- [ ] Declare another `double` variable to store the expense amount.
- [ ] Display the expense information.

### Code

```c
#include <stdio.h>

int main(void) {
    char name[] = "Coffee";
    double price = 3.50;
    int quantity = 2;
    double amount = 7.00;

    printf("Expense: %s\n", name);
    printf("Price: %.2f EUR\n", price);
    printf("Quantity: %d\n", quantity);
    printf("Amount: %.2f EUR\n", amount);

    return 0;
}
```

### Explanation

- `char` represents a character; `char[]` stores a sequence of characters.
- `int` stores integer values.
- `double` stores floating-point values.
- A variable declaration specifies its name and type.
- Initialization assigns a starting value when a variable is declared.
- `printf()` displays information. Its formatting features are explored in Task 4.

---

## Task 2

**Chapter:** Constants — `const`, `#define`

### Assignments

- [ ] Declare a constant named `VAT_RATE` using `const`.
- [ ] Initialize `VAT_RATE` with `0.19`.
- [ ] Define a constant named `CURRENCY` using `#define`.
- [ ] Define a constant named `MAX_EXPENSES` with the value `100`.
- [ ] Replace hardcoded currency text with `CURRENCY`.
- [ ] Use `MAX_EXPENSES` to display the application's expense limit.
- [ ] Display the configured VAT rate.
- [ ] Verify that attempting to reassign `VAT_RATE` produces a compilation error, then remove the invalid assignment.

### Code

```c
#include <stdio.h>

#define CURRENCY "EUR"
#define MAX_EXPENSES 100

int main(void) {
    const double VAT_RATE = 0.19;

    char name[] = "Coffee";
    double price = 3.50;
    int quantity = 2;
    double amount = 7.00;

    printf("Expense: %s\n", name);
    printf("Amount: %.2f %s\n", amount, CURRENCY);
    printf("VAT Rate: %.0f%%\n", VAT_RATE * 100);
    printf("Maximum Expenses: %d\n", MAX_EXPENSES);

    return 0;
}
```

### Explanation

- `const` makes a variable read-only after initialization.
- `#define` creates a preprocessor macro.
- `VAT_RATE` is a typed constant.
- `CURRENCY` is a string macro.
- `MAX_EXPENSES` is a numeric macro used later for array capacity.
- The preprocessor substitutes macros before compilation.

---

## Task 3

**Chapter:** Operators — `=`, `+`, `-`, `*`, `/`, `%`, `+=`, `-=`, `*=`, `/=`

### Assignments

- [ ] Calculate the subtotal using multiplication.
- [ ] Calculate VAT using the `VAT_RATE` constant.
- [ ] Calculate the final total using addition.
- [ ] Calculate the remaining budget using subtraction.
- [ ] Calculate the percentage of the budget spent using division.
- [ ] Calculate the remaining whole euros using the modulo operator.
- [ ] Use `=` to assign the subtotal to a variable.
- [ ] Use `+=` to add VAT to the total.
- [ ] Use `-=` to subtract the total from the budget.
- [ ] Use `*=` to double an example quantity.
- [ ] Use `/=` to restore the original quantity.

### Code

```c
#include <stdio.h>

#define CURRENCY "EUR"

int main(void) {
    const double VAT_RATE = 0.19;

    char name[] = "Coffee";
    double price = 3.50;
    int quantity = 2;
    double budget = 100.00;

    double subtotal = price * quantity;
    double vat = subtotal * VAT_RATE;

    double total = subtotal;
    total += vat;

    double remaining = budget - total;
    double percentage = total / budget * 100;

    budget -= total;

    int wholeEuros = (int)budget;
    int remainder = wholeEuros % 10;

    quantity *= 2;
    quantity /= 2;

    printf("Expense: %s\n", name);
    printf("Subtotal: %.2f %s\n", subtotal, CURRENCY);
    printf("VAT: %.2f %s\n", vat, CURRENCY);
    printf("Total: %.2f %s\n", total, CURRENCY);
    printf("Remaining: %.2f %s\n", remaining, CURRENCY);
    printf("Budget Used: %.2f%%\n", percentage);
    printf("Whole Euro Remainder: %d\n", remainder);

    return 0;
}
```

### Explanation

- `=` assigns a value.
- `+` adds values.
- `-` subtracts values.
- `*` multiplies values.
- `/` divides values.
- `%` calculates the integer remainder.
- `+=` adds to an existing value.
- `-=` subtracts from an existing value.
- `*=` multiplies an existing value.
- `/=` divides an existing value.
- `(int)` converts a value to an integer, discarding its fractional part.

---

## Task 4

**Chapter:** Input & Output — `printf`, `scanf`, format specifiers

### Assignments

- [ ] Display a welcome message using `printf()`.
- [ ] Ask the user to enter an expense name.
- [ ] Read the expense name using `scanf()`.
- [ ] Ask the user to enter a price.
- [ ] Read the price using `%lf`.
- [ ] Ask the user to enter a quantity.
- [ ] Read the quantity using `%d`.
- [ ] Ask the user to enter a budget.
- [ ] Read the budget using `%lf`.
- [ ] Calculate the expense total.
- [ ] Display the expense information using `%s`, `%d`, and `%.2f`.
- [ ] Use `\n` to separate lines.
- [ ] Use `\t` to align information.

### Code

```c
#include <stdio.h>

#define CURRENCY "EUR"

int main(void) {
    const double VAT_RATE = 0.19;

    char name[100];
    double price;
    int quantity;
    double budget;

    printf("===== EXPENSE TRACKER =====\n");

    printf("Expense name: ");
    scanf("%99s", name);

    printf("Price: ");
    scanf("%lf", &price);

    printf("Quantity: ");
    scanf("%d", &quantity);

    printf("Budget: ");
    scanf("%lf", &budget);

    double subtotal = price * quantity;
    double total = subtotal * (1 + VAT_RATE);
    double remaining = budget - total;

    printf("\n===== EXPENSE DETAILS =====\n");
    printf("Name:\t%s\n", name);
    printf("Price:\t%.2f %s\n", price, CURRENCY);
    printf("Quantity:\t%d\n", quantity);
    printf("Total:\t%.2f %s\n", total, CURRENCY);
    printf("Remaining:\t%.2f %s\n", remaining, CURRENCY);

    return 0;
}
```

### Explanation

- `printf()` writes formatted output.
- `scanf()` reads formatted input.
- `%s` represents a string.
- `%d` represents an integer.
- `%lf` reads a `double` with `scanf()`.
- `%.2f` displays a floating-point value with two decimal places.
- `\n` inserts a new line.
- `\t` inserts a horizontal tab.
- `&` provides a variable's memory address to `scanf()`.
- `%99s` limits the number of characters read into the name array.

---

## Task 5

**Chapter:** Conditional Statements — `if`, `else`, `switch`, `case`, `default`

### Assignments

- [ ] Reject prices less than or equal to zero.
- [ ] Reject quantities less than or equal to zero.
- [ ] Reject negative budgets.
- [ ] Use `if` and `else` to accept or reject expenses.
- [ ] Use `&&` to verify multiple conditions.
- [ ] Use `||` to detect invalid values.
- [ ] Use `else if` to classify expenses.
- [ ] Classify expenses below 20 EUR as Small.
- [ ] Classify expenses from 20 EUR through 100 EUR as Medium.
- [ ] Classify expenses above 100 EUR as Large.
- [ ] Ask the user to select Food, Transport, or Other.
- [ ] Use `switch` and `case` to process the selected category.
- [ ] Use `default` to handle an invalid category.
- [ ] Display whether the expense exceeds the available budget.

### Code

```c
#include <stdio.h>
#include <stdbool.h>

int main(void) {
    const double VAT_RATE = 0.19;

    double price;
    double budget;
    int quantity;
    int category;

    printf("Price: ");
    scanf("%lf", &price);

    printf("Quantity: ");
    scanf("%d", &quantity);

    printf("Budget: ");
    scanf("%lf", &budget);

    bool valid = price > 0 && quantity > 0 && budget >= 0;

    if (!valid) {
        printf("Invalid expense information.\n");
        return 1;
    }

    double total = price * quantity * (1 + VAT_RATE);

    if (total < 20) {
        printf("Small expense\n");
    } else if (total <= 100) {
        printf("Medium expense\n");
    } else {
        printf("Large expense\n");
    }

    if (total > budget) {
        printf("Budget exceeded!\n");
    } else {
        printf("Expense is within budget.\n");
    }

    printf("1. Food\n");
    printf("2. Transport\n");
    printf("3. Other\n");

    printf("Category: ");
    scanf("%d", &category);

    switch (category) {
        case 1:
            printf("Food\n");
            break;
        case 2:
            printf("Transport\n");
            break;
        case 3:
            printf("Other\n");
            break;
        default:
            printf("Invalid category\n");
    }

    return 0;
}
```

### Explanation

- `if` executes code when a condition is true.
- `else if` checks an additional condition.
- `else` handles the remaining case.
- `&&` requires all connected conditions to be true.
- `||` is true when at least one condition is true.
- `!` negates a boolean expression.
- `bool` stores `true` or `false`.
- `switch` selects a branch based on an expression.
- `case` defines a matching branch.
- `break` exits the switch.
- `default` handles unmatched values.

---

## Task 6

**Chapter:** Loops — `for`, `while`, `do`, `break`, `continue`

### Assignments

- [ ] Create an interactive menu.
- [ ] Add an option to record a new expense.
- [ ] Add an option to display total spending.
- [ ] Add an option to exit the application.
- [ ] Use `do...while` to repeat the menu.
- [ ] Use `for` to display menu options.
- [ ] Use `while` to request valid numeric menu input.
- [ ] Use `continue` to restart the menu after invalid choices.
- [ ] Use `break` to exit the application.
- [ ] Maintain a running total of accepted expenses.
- [ ] Allow multiple expenses to be entered during one session.

### Code

```c
#include <stdio.h>

int main(void) {
    const double VAT_RATE = 0.19;

    const char *options[] = {
        "Add Expense",
        "Show Total",
        "Exit"
    };

    double runningTotal = 0;
    int choice = 0;

    do {
        printf("\n===== EXPENSE TRACKER =====\n");

        for (int i = 0; i < 3; i++) {
            printf("%d. %s\n", i + 1, options[i]);
        }

        printf("Choice: ");

        while (scanf("%d", &choice) != 1) {
            int ch;

            while ((ch = getchar()) != '\n' && ch != EOF) {
            }

            printf("Enter a number: ");
        }

        if (choice < 1 || choice > 3) {
            printf("Invalid choice.\n");
            continue;
        }

        if (choice == 1) {
            double price;
            int quantity;

            printf("Price: ");
            if (scanf("%lf", &price) != 1) {
                printf("Invalid price.\n");
                break;
            }

            printf("Quantity: ");
            if (scanf("%d", &quantity) != 1) {
                printf("Invalid quantity.\n");
                break;
            }

            if (price <= 0 || quantity <= 0) {
                printf("Invalid expense.\n");
                continue;
            }

            double total = price * quantity * (1 + VAT_RATE);

            runningTotal += total;

            printf("Expense added.\n");
        } else if (choice == 2) {
            printf("Total: %.2f EUR\n", runningTotal);
        } else {
            break;
        }

    } while (choice != 3);

    return 0;
}
```

### Explanation

- `for` repeats code using initialization, condition, and update expressions.
- `while` repeats while a condition is true.
- `do...while` executes at least once before checking its condition.
- `break` terminates the nearest enclosing loop.
- `continue` skips the remaining statements in the current loop iteration.
- `runningTotal` accumulates spending across multiple menu operations.

---

## Task 7

**Chapter:** Arrays & Strings — `[]`, `char[]`, `strlen`, `strcmp`, `strcpy`

### Assignments

- [ ] Create an array for expense names.
- [ ] Create an array for expense prices.
- [ ] Create an array for quantities.
- [ ] Create an array for expense categories.
- [ ] Use `MAX_EXPENSES` to limit storage to 100 records.
- [ ] Track the number of stored expenses.
- [ ] Store each expense at the next available index.
- [ ] Use `strlen()` to check expense names.
- [ ] Use `strcpy()` to copy validated names into storage.
- [ ] Use `strcmp()` to search for expenses by name.
- [ ] Add a List Expenses option to the menu.
- [ ] Display all stored expenses using array traversal.
- [ ] Prevent array overflow.

### Code

```c
#include <stdio.h>
#include <string.h>

#define MAX_EXPENSES 100

int main(void) {
    char names[MAX_EXPENSES][100];
    double prices[MAX_EXPENSES];
    int quantities[MAX_EXPENSES];
    int categories[MAX_EXPENSES];

    int count = 0;

    char newName[100] = "Coffee";
    double newPrice = 3.50;
    int newQuantity = 2;
    int newCategory = 1;

    if (count < MAX_EXPENSES && strlen(newName) > 0) {
        strcpy(names[count], newName);

        prices[count] = newPrice;
        quantities[count] = newQuantity;
        categories[count] = newCategory;

        count++;
    }

    printf("\n===== EXPENSES =====\n");

    for (int i = 0; i < count; i++) {
        double total = prices[i] * quantities[i];

        printf("%d. %s: %.2f EUR\n",
               i + 1,
               names[i],
               total);
    }

    char searchName[] = "Coffee";

    for (int i = 0; i < count; i++) {
        if (strcmp(names[i], searchName) == 0) {
            printf("Found: %s\n", names[i]);
        }
    }

    return 0;
}
```

### Explanation

- `[]` declares arrays and accesses their elements.
- One-dimensional arrays store multiple values of the same type.
- Multidimensional arrays store data across multiple dimensions.
- `char[]` stores null-terminated strings.
- `strlen()` calculates string length.
- `strcmp()` compares strings.
- `strcpy()` copies a string into a sufficiently large destination array.
- Array indexing begins at zero.
- Array traversal processes stored elements using loops.
- `count` tracks the number of stored records.

---

## Task 8

**Chapter:** Functions — `void`, `return`, parameters, function calls

### Assignments

- [ ] Create a function to display the application menu.
- [ ] Create a function to add an expense.
- [ ] Create a function to list stored expenses.
- [ ] Create a function to calculate total spending.
- [ ] Create a function to calculate average spending.
- [ ] Create a function to find the largest expense.
- [ ] Declare function prototypes before `main()`.
- [ ] Define functions with appropriate parameters.
- [ ] Use `void` for functions that do not return values.
- [ ] Use `return` to return calculated results.
- [ ] Pass arrays and expense counts to functions.
- [ ] Use local variables for intermediate calculations.
- [ ] Reuse existing functions instead of duplicating logic.
- [ ] Integrate all functions into the interactive menu.

### Code

```c
#include <stdio.h>

void showMenu(void);

double calculateTotal(
    double prices[],
    int quantities[],
    int count
);

double calculateAverage(
    double prices[],
    int quantities[],
    int count
);

double findLargest(
    double prices[],
    int quantities[],
    int count
);

void showMenu(void) {
    printf("\n===== EXPENSE TRACKER =====\n");
    printf("1. Add Expense\n");
    printf("2. List Expenses\n");
    printf("3. Show Total\n");
    printf("4. Show Average\n");
    printf("5. Show Largest Expense\n");
    printf("6. Exit\n");
}

double calculateTotal(
    double prices[],
    int quantities[],
    int count
) {
    double total = 0;

    for (int i = 0; i < count; i++) {
        total += prices[i] * quantities[i];
    }

    return total;
}

double calculateAverage(
    double prices[],
    int quantities[],
    int count
) {
    if (count == 0) {
        return 0;
    }

    return calculateTotal(prices, quantities, count) / count;
}

double findLargest(
    double prices[],
    int quantities[],
    int count
) {
    if (count == 0) {
        return 0;
    }

    double largest = prices[0] * quantities[0];

    for (int i = 1; i < count; i++) {
        double amount = prices[i] * quantities[i];

        if (amount > largest) {
            largest = amount;
        }
    }

    return largest;
}
```

### Explanation

- Function declarations introduce functions before their definitions.
- Function definitions contain the implementation.
- Parameters allow functions to receive data.
- Function calls execute reusable code.
- `void` indicates that a function returns no value.
- `return` sends a result back to the caller.
- Local variables exist within their declaring scope.
- Function reuse avoids duplicated calculations.
- Passing arrays allows functions to process stored expenses.

---

## Final Application Requirements

- [ ] Record new expenses.
- [ ] Accept expense names, prices, and quantities.
- [ ] Calculate subtotal, VAT, and total.
- [ ] Validate user input.
- [ ] Classify expenses.
- [ ] Store up to 100 expenses.
- [ ] List stored expenses.
- [ ] Search expenses by name.
- [ ] Calculate total spending.
- [ ] Calculate average spending.
- [ ] Find the largest expense.
- [ ] Navigate an interactive menu.
- [ ] Exit the application safely.

## Repository Structure

```text
c-000-expense-tracker/
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
