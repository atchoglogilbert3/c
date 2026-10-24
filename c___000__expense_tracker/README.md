
# C-000 — Expense Tracker

## Project Overview

Build a command-line Expense Tracker in C.

The application allows users to record expenses, display
stored expenses, and calculate total spending.

The project introduces the fundamentals of C programming
through incremental development of a functional application.

**Level:** Beginner  
**Language:** C  
**Repository:** `c-000-expense-tracker`

---

# Learning Objectives

## Programming Chapters

1. C Fundamentals
2. Data Types and Expressions
3. Console Input and Output
4. Conditional Statements
5. Loops
6. Functions
7. Arrays
8. Strings

---

# Module 1 — Basic Expense Calculator

## Goal

Create a console application that accepts one expense
and displays its information.

### Task 1.1 — Create an Expense

**Skills / Topics:**
- Variables
- Data Types
- Variable Initialization
- Assignment Operators

**Assignment:**

1. Create a variable for the expense name.
2. Create a variable for the expense amount.
3. Initialize both variables.
4. Store an example expense.

**Code Snippet:**

```c
char name[] = "Groceries";
double amount = 25.50;
```

**Expected Result:**

The application stores an expense name and amount.

### Task 1.2 — Display the Expense

**Skills / Topics:**
- Standard Output
- printf()
- Format Specifiers
- Escape Sequences

**Assignment:**

1. Display the expense name.
2. Display the expense amount.
3. Format the amount to two decimal places.
4. Display the currency EUR.

**Code Snippet:**

```c
printf("%s: %.2f EUR\n", name, amount);
```

**Expected Output:**

```text
Groceries: 25.50 EUR
```

### Task 1.3 — Accept User Input

**Skills / Topics:**
- Standard Input
- scanf()
- Input Formatting
- Character Arrays

**Assignment:**

1. Ask the user for an expense name.
2. Read the expense name.
3. Ask the user for an amount.
4. Read the amount.
5. Display the entered expense.

**Code Snippet:**

```c
char name[100];
double amount;

printf("Expense name: ");
scanf("%99s", name);

printf("Amount: ");
scanf("%lf", &amount);
```

**Expected Output:**

```text
Expense name: Food
Amount: 15.50

Food: 15.50 EUR
```

**Module 1 Result:**

A working application that accepts and displays
a single expense.

---

# Module 2 — Expense Validation

## Goal

Validate expense amounts before accepting them.

### Task 2.1 — Validate Positive Amounts

**Skills / Topics:**
- Relational Operators
- Boolean Expressions
- Conditional Statements
- if / else

**Assignment:**

1. Read an expense amount.
2. Check whether the amount is positive.
3. Accept valid amounts.
4. Reject zero or negative amounts.

**Code Snippet:**

```c
if (amount > 0) {
    printf("Expense accepted.\n");
} else {
    printf("Invalid amount.\n");
}
```

### Task 2.2 — Classify Expenses

**Skills / Topics:**
- Logical Operators
- else if
- Multiple Conditions

**Assignment:**

Classify expenses into three categories:

- Small: below 20 EUR
- Medium: 20–100 EUR
- Large: above 100 EUR

**Code Snippet:**

```c
if (amount < 20) {
    printf("Small expense\n");
} else if (amount <= 100) {
    printf("Medium expense\n");
} else {
    printf("Large expense\n");
}
```

**Module 2 Result:**

An expense calculator with amount validation
and expense classification.

---

# Module 3 — Interactive Expense Menu

## Goal

Allow users to interact with the application
through a menu.

### Task 3.1 — Create the Main Menu

**Skills / Topics:**
- Integer Variables
- switch Statements
- case Labels
- break
- default

**Assignment:**

Create a menu containing:

1. Add expense
2. Show total
3. Exit

**Code Snippet:**

```c
switch (choice) {
    case 1:
        printf("Add expense\n");
        break;

    case 2:
        printf("Show total\n");
        break;

    case 3:
        printf("Goodbye!\n");
        break;

    default:
        printf("Invalid choice\n");
}
```

### Task 3.2 — Keep the Application Running

**Skills / Topics:**
- while Loops
- do-while Loops
- Loop Conditions
- Loop Control

**Assignment:**

1. Display the main menu.
2. Read the user's choice.
3. Execute the selected action.
4. Return to the menu.
5. Stop only when the user selects Exit.

**Code Snippet:**

```c
int choice;

do {
    printf("\n1. Add expense\n");
    printf("2. Show total\n");
    printf("3. Exit\n");

    scanf("%d", &choice);

} while (choice != 3);
```

**Module 3 Result:**

An interactive console application with
a repeating menu.

---

# Module 4 — Multiple Expenses

## Goal

Store multiple expenses during application execution.

### Task 4.1 — Store Expense Amounts

**Skills / Topics:**
- Arrays
- Array Indexing
- Array Initialization
- Array Bounds

**Assignment:**

1. Create an array for expense amounts.
2. Allow users to add expenses.
3. Store each amount in the next available position.
4. Limit the number of expenses to 100.

**Code Snippet:**

```c
double amounts[100];
int count = 0;

if (count < 100) {
    amounts[count] = 25.50;
    count++;
}
```

### Task 4.2 — Store Expense Names

**Skills / Topics:**
- Character Arrays
- Multidimensional Arrays
- C Strings
- String Storage

**Assignment:**

1. Create an array for expense names.
2. Store a name for each expense.
3. Associate each name with its amount.
4. Maintain matching array indexes.

**Code Snippet:**

```c
char names[100][100];
double amounts[100];
```

### Task 4.3 — List All Expenses

**Skills / Topics:**
- for Loops
- Array Traversal
- Indexed Access

**Assignment:**

1. Add a List Expenses menu option.
2. Iterate through stored expenses.
3. Display each expense name and amount.
4. Display a message when the list is empty.

**Code Snippet:**

```c
for (int i = 0; i < count; i++) {
    printf("%s: %.2f EUR\n",
           names[i], amounts[i]);
}
```

**Module 4 Result:**

An application capable of storing and listing
up to 100 expenses.

---

# Module 5 — Expense Calculations

## Goal

Calculate spending statistics using functions.

### Task 5.1 — Calculate Total Expenses

**Skills / Topics:**
- Functions
- Function Parameters
- Return Values
- Function Declarations

**Assignment:**

1. Create a function named calculateTotal.
2. Accept an array of amounts.
3. Accept the number of expenses.
4. Calculate and return the total.
5. Display the result in the main menu.

**Code Snippet:**

```c
double calculateTotal(double amounts[], int count) {
    double total = 0;

    for (int i = 0; i < count; i++) {
        total += amounts[i];
    }

    return total;
}
```

### Task 5.2 — Calculate Average Spending

**Skills / Topics:**
- Arithmetic Expressions
- Type Conversion
- Function Reuse
- Division

**Assignment:**

1. Create a function named calculateAverage.
2. Reuse calculateTotal.
3. Divide the total by the number of expenses.
4. Handle an empty expense list.

**Code Snippet:**

```c
double calculateAverage(double amounts[], int count) {
    if (count == 0) {
        return 0;
    }

    return calculateTotal(amounts, count) / count;
}
```

### Task 5.3 — Find the Largest Expense

**Skills / Topics:**
- Comparison Operators
- Array Traversal
- Accumulator Variables

**Assignment:**

1. Create a function named findLargest.
2. Compare all stored amounts.
3. Return the largest amount.
4. Handle an empty expense list.

**Code Snippet:**

```c
double findLargest(double amounts[], int count) {
    if (count == 0) {
        return 0;
    }

    double largest = amounts[0];

    for (int i = 1; i < count; i++) {
        if (amounts[i] > largest) {
            largest = amounts[i];
        }
    }

    return largest;
}
```

**Module 5 Result:**

An expense tracker capable of calculating:

- Total spending
- Average spending
- Largest expense

---

# Module 6 — Final Integration

## Goal

Combine all previously developed features
into one complete command-line application.

### Task 6.1 — Organize Application Functions

**Skills / Topics:**
- Function Composition
- Function Prototypes
- Local Variables
- Scope
- Code Reuse

**Assignment:**

Organize the application into functions:

```c
void showMenu(void);
void addExpense(void);
void listExpenses(void);

double calculateTotal(double amounts[], int count);
double calculateAverage(double amounts[], int count);
double findLargest(double amounts[], int count);
```

Adapt function parameters as necessary to share
the expense data correctly.

### Task 6.2 — Integrate the Main Menu

**Skills / Topics:**
- Control Flow Integration
- Function Calls
- Program State
- Modular Code Organization

**Assignment:**

Implement the final menu:

```text
========== EXPENSE TRACKER ==========

1. Add Expense
2. List Expenses
3. Show Total
4. Show Average
5. Show Largest Expense
6. Exit

Choose an option:
```

### Task 6.3 — Handle Invalid Input

**Skills / Topics:**
- Input Validation
- scanf() Return Values
- Input Buffer Handling
- Defensive Programming

**Assignment:**

1. Reject nonnumeric amounts.
2. Reject negative or zero amounts.
3. Reject invalid menu selections.
4. Prevent array overflow.
5. Handle an empty expense list.
6. Ensure invalid input does not cause an infinite loop.

**Code Snippet:**

```c
double amount;

if (scanf("%lf", &amount) != 1) {
    printf("Invalid numeric input.\n");
}
```

Remember to clear or consume invalid input before
requesting another value.

---

# Final Application Requirements

The completed application must support:

- [ ] Adding expenses
- [ ] Storing up to 100 expenses
- [ ] Listing all expenses
- [ ] Calculating total spending
- [ ] Calculating average spending
- [ ] Finding the largest expense
- [ ] Classifying expenses by amount
- [ ] Validating user input
- [ ] Navigating an interactive menu
- [ ] Exiting the application safely

---

# Suggested Repository Structure

```text
c-000-expense-tracker/
├── README.md
└── main.c
```

All modules can initially be developed inside `main.c`.

More advanced source-code organization will be introduced
in Project 001.

---

# Completion Criteria

- [ ] Module 1 — Basic Expense Calculator
- [ ] Module 2 — Expense Validation
- [ ] Module 3 — Interactive Expense Menu
- [ ] Module 4 — Multiple Expenses
- [ ] Module 5 — Expense Calculations
- [ ] Module 6 — Final Integration

---

# Next Project

**C-001 — Student Management System**

New programming chapters:

- Structures
- Enumerations
- Typedef
- Data Modeling
- Modular Programming
- Header Files
