from Loan import Loan
import sys
from time import sleep

def display_menu():
    print("""
    Menu
    --------------------
    1. Start a new loan
    2. Show Payment
    3. Show Amortization Table
    4. Show Loan Summary
    5. Plot Balances
    6. Show size of payment to payoff in specific time
    7. Show effect of adding
    8. Exit
    """)



def pmt(loan):
    print(loan.pmt_str)


def amort(loan):
    print(loan.table)

def summary(loan):
    loan.summary()

def plot(loan):
    loan.plot_balances()

def pay_faster(loan):
    amount = float(input("Enter years to be debt free: "))
    result = loan.retire_debt(amount)
    print(f"Monthly extra: ${result[0]:,.2f}\tTotal monthly:{result[1]:,.2f}")

def pay_early(loan):
    amount = float(input("Enter monthly extra amount: "))
    new_term = loan.extra_pmt(amount)
    print(f"Loan paid off in {new_term}")

action = {'2': pmt, '3':amort, '4':summary, '5':plot, '6':pay_faster, '7': pay_early}

def main():
    while True:
        display_menu()
        choice = input("Enter your selection: ")
        if choice == '1':
            rate = float(input("Please enter the  interest rate:"))
            term = int(input("Please enter the term: "))
            pv = float(input("Please enter the amount borrowed: "))
            loan = Loan(rate,term,pv)
            print("Loan initialized")
            sleep(1)
        elif choice in '234567':
            try:
                action[choice](loan)
                sleep(1)
            except NameError:
                print("No loan setup")
                print("Choose option 1 from the menu")
                sleep(1)
        elif choice == '8':
            print("Thanks for using our program.")
            sys.exit()
        else:
            print("Please enter a valid input.")


if __name__ == "__main__":
    main()
