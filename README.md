# ATM Machine in C++ 🏧

This is a simple **ATM machine simulation** program written in C++. The program allows users to perform basic ATM operations such as checking balance, depositing money, withdrawing money, and exiting the ATM. It uses functions for each operation, ensuring a modular structure. The program is entirely functional and designed for educational purposes to demonstrate basic concepts of C++ and procedural programming.

## 📋 Table of Contents

- [Description](#description)
- [Features](#features)
- [Getting Started](#getting-started)
- [How to Use](#how-to-use)
- [Code Explanation](#code-explanation)
- [Example](#example)
- [License](#license)

## 💡 Description

This ATM machine simulation offers the following functionalities:
- **Check Balance**: Displays the current balance in the ATM account.
- **Deposit**: Allows the user to deposit a specific amount of money into the ATM account.
- **Withdraw**: Allows the user to withdraw a specified amount of money from the ATM account, given sufficient funds.
- **Exit**: Exits the ATM program after completing the operations.

The program runs in a continuous loop, prompting the user to select an operation until the user chooses to exit.

## 🛠 Features

- **Modular design**: The program uses separate functions for checking balance, depositing, and withdrawing money.
- **Input validation**: Ensures that users enter valid amounts for deposits and withdrawals.
- **Simple interface**: The ATM provides an easy-to-understand menu and prompts for user input.
- **Continuous loop**: The program continues to run until the user opts to exit.

## 🚀 Getting Started

To use or modify this project:

1. **Clone or Download** the repository:
    ```
    bash
    git clone https://github.com/yourusername/ATM-Simulation.git
    ```

2. **Compile the Code**:
    If you're using a terminal and `g++` (or another C++ compiler), you can compile the program with:
    ```
    bash
    g++ atm.cpp -o atm
    ```

3. **Run the Program**:
    After compiling, you can run the program by executing:
    ```
    bash
    ./atm
    ```

## 🖱 How to Use

Once the program is executed, the ATM menu will be displayed with the following options:

1. **Check Balance**: Shows the current balance of the user.
2. **Deposit**: Prompts the user to enter an amount to deposit into the account.
3. **Withdraw**: Prompts the user to enter an amount to withdraw from the account.
4. **Exit**: Exits the program, displaying a thank-you message.

The user can interact with the program using the following input choices:
- Enter a number (1-4) corresponding to the desired operation.
- The program will display appropriate messages after each operation (successful deposit/withdrawal or errors like insufficient balance).

### Example:
```
ATM Menu:
1. Check Balance
2. Deposit
3. Withdraw
4. Exit
Enter your choice (1-4): 2
Enter amount to deposit: $100
You have successfully deposited: $100.00

ATM Menu:
1. Check Balance
2. Deposit
3. Withdraw
4. Exit
Enter your choice (1-4): 1
Your current balance is: $100.00

ATM Menu:
1. Check Balance
2. Deposit
3. Withdraw
4. Exit
Enter your choice (1-4): 3
Enter amount to withdraw: $50
You have successfully withdrawn: $50.00

ATM Menu:
1. Check Balance
2. Deposit
3. Withdraw
4. Exit
Enter your choice (1-4): 4
Exiting ATM. Thank you for using our service!
```
## 📝 Code Explanation

### Functions:

- **`checkBalance(float balance)`**: Displays the current balance in the ATM.
- **`deposit(float& balance, float amount)`**: Takes a positive amount from the user and adds it to the balance.
- **`withdraw(float& balance, float amount)`**: Takes a withdrawal amount from the user and subtracts it from the balance if sufficient funds are available.
- **`startATM()`**: The main function that runs the ATM interface, offering the user a menu to choose an operation. This function keeps looping until the user selects the exit option.

### Flow:
1. The program continuously shows the ATM menu until the user selects the exit option.
2. Depending on the user's choice, the appropriate function is called:
   - If the user chooses **1**, the `checkBalance()` function is called.
   - If the user chooses **2**, the `deposit()` function is called to deposit money.
   - If the user chooses **3**, the `withdraw()` function is called to withdraw money.
   - If the user chooses **4**, the program exits with a message.

---

## 💻 Example Code:

```
#include <iostream>
using namespace std;

// Function to check balance
void checkBalance(float balance) {
    cout << "Your current balance is: $" << balance << endl;
}

// Function to deposit money
void deposit(float& balance, float amount) {
    if (amount > 0) {
        balance += amount;
        cout << "You have successfully deposited: $" << amount << endl;
    } else {
        cout << "Deposit amount must be positive." << endl;
    }
}

// Function to withdraw money
void withdraw(float& balance, float amount) {
    if (amount <= balance) {
        if (amount > 0) {
            balance -= amount;
            cout << "You have successfully withdrawn: $" << amount << endl;
        } else {
            cout << "Withdrawal amount must be positive." << endl;
        }
    } else {
        cout << "Insufficient balance for withdrawal." << endl;
    }
}

// Function to handle ATM operations
void startATM() {
    float balance = 0.0;
    int choice;
    float amount;

    while (true) {
        cout << "\nATM Menu:\n";
        cout << "1. Check Balance\n";
        cout << "2. Deposit\n";
        cout << "3. Withdraw\n";
        cout << "4. Exit\n";
        cout << "Enter your choice (1-4): ";
        cin >> choice;

        switch (choice) {
            case 1:
                checkBalance(balance);
                break;
            case 2:
                cout << "Enter amount to deposit: $";
                cin >> amount;
                deposit(balance, amount);
                break;
            case 3:
                cout << "Enter amount to withdraw: $";
                cin >> amount;
                withdraw(balance, amount);
                break;
            case 4:
                cout << "Exiting ATM. Thank you for using our service!" << endl;
                return;
            default:
                cout << "Invalid choice! Please enter a number between 1 and 4.\n";
        }
    }
}

int main() {
    startATM(); // Start the ATM operation
    return 0;
}
```
