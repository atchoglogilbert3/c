
# C-000 — Expense Tracker

**Language:** C  
**Level:** Beginner  
**Repository:** `c-000-expense-tracker`

## Project Overview

Build a command-line Expense Tracker in C.

The application allows users to add expenses, view stored expenses, and calculate spending statistics.

Each task introduces one new chapter of C programming and extends the existing application.

---

## Task 1 — C Fundamentals

**Feature:** Create and display an expense.

**New Concepts:**
- Variables
- Data Types
- Constants
- Arithmetic Operators
- Assignment Operators

### Coding Assignments

- [ ] Create a variable to store an expense name.
- [ ] Create a variable to store an expense price.
- [ ] Create a variable to store the quantity purchased.
- [ ] Calculate the total expense using price × quantity.
- [ ] Display the expense information.

### Code Snippet

```c
char name[] = "Coffee";
double price = 3.50;
int quantity = 2;

double total = price * quantity;
```

### Expected Output

```text
Expense: Coffee
Price: 3.50 EUR
Quantity: 2
Total: 7.00 EUR
```

---

## Task 2 — Input and Output

**Feature:** Accept expenses from the user.

**New Concepts:**
- Standard Input
- Standard Output
- printf()
- scanf()
- Format Specifiers
- Escape Sequences

### Coding Assignments

- [ ] Ask the user to enter an expense name.
- [ ] Read the expense name.
- [ ] Ask the user to enter an expense price.
- [ ] Read the price.
- [ ] Ask the user to enter a quantity.
- [ ] Calculate the total expense.
- [ ] Display the entered expense information.

### Code Snippet

```c
char name[100];
double price;
int quantity;

printf("Expense name: ");
scanf("%99s", name);

printf("Price: ");
scanf("%lf", &price);

printf("Quantity: ");
scanf("%d", &quantity);
```

### Expected Output

```text
Expense name: Coffee
Price: 3.50
Quantity: 2

Coffee: 7.00 EUR
```

---

## Task 3 — Conditional Statements

**Feature:** Validate and classify expenses.

**New Concepts:**
- if
- else if
- else
- Comparison Operators
- Logical Operators
- Boolean Expressions

### Coding Assignments

- [ ] Reject negative expense prices.
- [ ] Reject zero expense prices.
- [ ] Reject quantities smaller than one.
- [ ] Accept valid expenses.
- [ ] Classify expenses according to their total amount.
- [ ] Display an appropriate validation message.

### Expense Categories

| Category | Amount |
|---|---|
| Small | Below 20 EUR |
| Medium | 20–100 EUR |
| Large | Above 100 EUR |

### Code Snippet

```c
if (price <= 0 || quantity <= 0) {
    printf("Invalid expense.\n");
} else if (total < 20) {
    printf("Small expense.\n");
} else if (total <= 100) {
    printf("Medium expense.\n");
} else {
    printf("Large expense.\n");
}
```

### Expected Output

```text
Expense name: Coffee
Price: 3.50
Quantity: 2

Expense accepted.
Category: Small
```

---

## Task 4 — Loops

**Feature:** Create an interactive expense menu.

**New Concepts:**
- while Loops
- do-while Loops
- for Loops
- Loop Conditions
- break
- continue

### Coding Assignments

- [ ] Create an interactive menu.
- [ ] Add an option to enter a new expense.
- [ ] Add an option to display the current total.
- [ ] Add an option to exit the application.
- [ ] Repeat the menu after each operation.
- [ ] Stop the application only when Exit is selected.
- [ ] Handle invalid menu choices.

### Code Snippet

```c
int choice;

do {
    printf("\n1. Add Expense\n");
    printf("2. Show Total\n");
    printf("3. Exit\n");

    printf("Choice: ");
    scanf("%d", &choice);

    switch (choice) {
        case 1:
            printf("Add Expense\n");
            break;

        case 2:
            printf("Show Total\n");
            break;

        case 3:
            printf("Goodbye!\n");
            break;

        default:
            printf("Invalid choice.\n");
    }

} while (choice != 3);
```

### Expected Output

```text
1. Add Expense
2. Show Total
3. Exit

Choice: 1

Expense name: Coffee
Price: 3.50
Quantity: 2

Expense accepted.

1. Add Expense
2. Show Total
3. Exit

Choice:
```

---

## Task 5 — Arrays and Strings

**Feature:** Store and display multiple expenses.

**New Concepts:**
- One-Dimensional Arrays
- Multidimensional Arrays
- Character Arrays
- Strings
- Array Indexing
- Array Traversal
- String Handling

### Coding Assignments

- [ ] Create an array for expense names.
- [ ] Create an array for expense prices.
- [ ] Create an array for quantities.
- [ ] Store up to 100 expenses.
- [ ] Keep track of the number of stored expenses.
- [ ] Add a List Expenses option to the menu.
- [ ] Display all stored expenses.
- [ ] Display a message when no expenses exist.
- [ ] Prevent adding expenses when the arrays are full.

### Code Snippet

```c
#define MAX_EXPENSES 100

char names[MAX_EXPENSES][100];
double prices[MAX_EXPENSES];
int quantities[MAX_EXPENSES];

int count = 0;
```

### Listing Expenses

```c
for (int i = 0; i < count; i++) {
    double total = prices[i] * quantities[i];

    printf("%d. %s: %.2f EUR\n",
           i + 1, names[i], total);
}
```

### Expected Output

```text
========== EXPENSES ==========

1. Coffee: 7.00 EUR
2. Transport: 15.00 EUR
3. Groceries: 45.50 EUR

Total Records: 3
```

---

## Task 6 — Functions

**Feature:** Calculate expense statistics and organize application logic.

**New Concepts:**
- Function Declarations
- Function Definitions
- Function Parameters
- Return Values
- Function Calls
- Local Variables
- Variable Scope
- Function Reuse

### Coding Assignments

- [ ] Create a function to display the menu.
- [ ] Create a function to add an expense.
- [ ] Create a function to list stored expenses.
- [ ] Create a function to calculate total spending.
- [ ] Create a function to calculate average spending.
- [ ] Create a function to find the largest expense.
- [ ] Handle calculations when no expenses exist.
- [ ] Integrate all functions into the main application.

### Code Snippet

```c
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
```

### Average Spending

```c
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
```

### Largest Expense

```c
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

### Expected Output

```text
========== EXPENSE STATISTICS ==========

Number of Expenses: 3
Total Spending: 67.50 EUR
Average Spending: 22.50 EUR
Largest Expense: 45.50 EUR
```

---

## Final Application

After completing all six tasks, the Expense Tracker should provide the following menu:

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

### Final Requirements

- [ ] Add new expenses.
- [ ] Validate expense prices and quantities.
- [ ] Classify expenses by amount.
- [ ] Store up to 100 expenses.
- [ ] List all stored expenses.
- [ ] Calculate total spending.
- [ ] Calculate average spending.
- [ ] Find the largest expense.
- [ ] Handle invalid user input.
- [ ] Provide an interactive menu.
- [ ] Exit the application safely.

---

## Repository Structure

```text
c-000-expense-tracker/
├── README.md
└── main.c
```

## Completion Checklist

- [ ] Task 1 — C Fundamentals
- [ ] Task 2 — Input and Output
- [ ] Task 3 — Conditional Statements
- [ ] Task 4 — Loops
- [ ] Task 5 — Arrays and Strings
- [ ] Task 6 — Functions

---

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
