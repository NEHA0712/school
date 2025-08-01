# bank

class BankAccount:
    def __init__(self, name, pin, balance=0):
        self.name = name
        self.pin = pin
        self.balance = balance

    def verify_pin(self, entered_pin):
        return self.pin == entered_pin

    def deposit(self, amount):
        self.balance += amount
        print(f"✅ ₹{amount} deposited successfully. New balance is ₹{self.balance}")

    def withdraw(self, amount):
        if self.balance < amount:
            print("❌ Insufficient balance.")
        else:
            self.balance -= amount
            print(f"✅ ₹{amount} withdrawn successfully. New balance is ₹{self.balance}")

    def check_balance(self):
        print(f"💰 {self.name}, your current balance is ₹{self.balance}")


# Create account
name = input("Enter your name: ")
pin = int(input("Set a 4-digit PIN: "))
account = BankAccount(name, pin)

# Bank Menu
while True:
    print("\n-------- Welcome to the Bank --------")
    print("Menu:")
    print("1. Deposit 💰")
    print("2. Withdraw 💸")
    print("3. Check Balance 🧾")
    print("4. Exit 🚪")

    choice = int(input("Enter your choice (1-4): "))

    if choice in [1, 2, 3]:
        entered_pin = int(input("Enter your PIN: "))
        if not account.verify_pin(entered_pin):
            print("❌ Incorrect PIN. Try again.")
            continue

    if choice == 1:
        amt = int(input("Enter amount to deposit 💵: "))
        account.deposit(amt)

    elif choice == 2:
        amt = int(input("Enter amount to withdraw 💸: "))
        account.withdraw(amt)

    elif choice == 3:
        account.check_balance()

    elif choice == 4:
        print("👋 Thank you for using our service. Goodbye!")
        break

    else:
        print("⚠ Invalid choice. Please select 1 to 4.")
