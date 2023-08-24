import requests
import matplotlib.pyplot as plt
import webbrowser
api_key = "9d4c98aa17ad1e9c1f07ce22dd665aac"
# You can get api_key for free by signing up in
# https://site.financialmodelingprep.com/developer/docs/stock-market-quote-free-api/#Python
symbol_url = "https://stockanalysis.com/stocks/"
message = "Please input the company symbol: enter HELP if you want " \
          "to see the list of symbols. enter STOP to stop."
company = input(message)


if company == "HELP":
    webbrowser.open(symbol_url)
    company = input(message)
if company == "STOP":
    print("Thanks for using this program.")
while company != "STOP":
    years = int(input("How many past years would you like to see about your "
                      "company?"))
    income_statement = requests.get(f"https://financialmodelingprep.com"
                                    f"/api/v3/income-statement/{company}?"
                                    f"limit={years+1}&apikey={api_key}")
    income_statement = income_statement.json()
    # To get the last number of years of revenue from latest to earliest.
    revenues = list(reversed([income_statement[i]['revenue']
                              for i in range(len(income_statement))]))

    # To get the last number of years of profit from latest to earliest.
    profits = list(reversed([income_statement[i]['grossProfit']
                             for i in range(len(income_statement))]))
    # Draws the graph.
    print("Note that if the symbol you enter is invalid, the graph will be empty.")
    plt.plot(revenues, label="Revenue")
    plt.plot(profits, label="Profit")
    plt.title(f"{company} Revenue & Profit")
    plt.xlabel("Years")
    plt.ylabel("Amount")
    plt.legend(loc="upper left")
    plt.show()
    # The option which lets the user download the csv file with financial information.
    csv_file = input("Would you like to have a csv file with all the "
                     "information about the company? Y/y")
    if csv_file == "Y" or csv_file == "y":
        name = input("Please put in the name for the file:")
        income_statement = requests.get(f"https://financialmodelingprep.com/api/v3/"
                                        f"income-statement/{company}?"
                                        f"datatype=csv&limit={years}&apikey={api_key}")
        with open(name+'.csv', 'wb') as f:
            f.write(income_statement.content)
    company = input(message)
    if company != "STOP":
        print("Note that if the symbol you enter is invalid, the graph will be empty.")
        if company == "HELP":
            webbrowser.open(symbol_url)
            company = input(message)
        years = int(input("How many past years would you like to see about your company?"))
    else:
        print("Thanks for using this program.")
