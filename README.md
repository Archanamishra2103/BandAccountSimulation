# BankAccountSimulation
A simple Java-based console application that simulates basic banking operations. This project demonstrates the use of Object-Oriented Programming (OOP), ArrayList, and menu-driven programming.
    
     import java.util.ArrayList;
     import java.util.Scanner;

    class Account {
    private String accountHolder;
    private double balance;
    private ArrayList<String> transactionHistory;

    public Account(String accountHolder, double initialBalance) {
        this.accountHolder = accountHolder;
        this.balance = initialBalance;
        this.transactionHistory = new ArrayList<>();
        transactionHistory.add("Account created with balance: " + initialBalance);
    }

    public void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
            transactionHistory.add("Deposited: " + amount + " | Balance: " + balance);
            System.out.println("Deposited " + amount + " successfully.");
        } else {
            System.out.println("Invalid deposit amount!");
        }
    }

    public void withdraw(double amount) {
        if (amount > 0 && amount <= balance) {
            balance -= amount;
            transactionHistory.add("Withdrew: " + amount + " | Balance: " + balance);
            System.out.println("Withdrawn " + amount + " successfully.");
        } else {
            System.out.println("Invalid withdrawal! Insufficient balance.");
        }
    }

    public void checkBalance() {
        System.out.println("Current Balance: " + balance);
    }

    public void showTransactionHistory() {
        System.out.println("\n--- Transaction History ---");
        for (String record : transactionHistory) {
            System.out.println(record);
        }
    }
    }

    public class BankSimulation {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter account holder name: ");
        String name = sc.nextLine();

        System.out.print("Enter initial deposit: ");
        double initialBalance = sc.nextDouble();

        Account account = new Account(name, initialBalance);

        int choice;
        do {
            System.out.println("\n--- Bank Menu ---");
            System.out.println("1. Deposit");
            System.out.println("2. Withdraw");
            System.out.println("3. Check Balance");
            System.out.println("4. Transaction History");
            System.out.println("5. Exit");
            System.out.print("Enter choice: ");
            choice = sc.nextInt();

            switch (choice) {
                case 1 -> {
                    System.out.print("Enter deposit amount: ");
                    double depositAmount = sc.nextDouble();
                    account.deposit(depositAmount);
                }
                case 2 -> {
                    System.out.print("Enter withdrawal amount: ");
                    double withdrawAmount = sc.nextDouble();
                    account.withdraw(withdrawAmount);
                }
                case 3 -> account.checkBalance();
                case 4 -> account.showTransactionHistory();
                case 5 -> System.out.println("Exiting... Thank you for banking with us!");
                default -> System.out.println("Invalid choice! Try again.");
            }
        } while (choice != 5);

        sc.close();
    }
    }

