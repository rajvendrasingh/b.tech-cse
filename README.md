import datetime

def add_expense():
    amount = float(input("Enter amount: "))
    category = input("Enter category (Food/Travel/Other): ")
    date = datetime.datetime.now().strftime("%Y-%m-%d %H:%M:%S")

    with open("expenses.txt", "a") as file:
        file.write(f"{date} | {category} | ₹{amount}\n")

    print("Expense added successfully!\n")


def view_expenses():
    try:
        with open("expenses.txt", "r") as file:
            print("\n---- All Expenses ----")
            print(file.read())
    except FileNotFoundError:
        print("No expenses recorded yet.\n")


def main():
    while True:
        print("1. Add Expense")
        print("2. View Expenses")
        print("3. Exit")

        choice = input("Choose an option: ")

        if choice == "1":
            add_expense()
        elif choice == "2":
            view_expenses()
        elif choice == "3":
            print("Goodbye!")
            break
        else:
            print("Invalid choice. Try again.\n")


if __name__ == "__main__":
    main()
