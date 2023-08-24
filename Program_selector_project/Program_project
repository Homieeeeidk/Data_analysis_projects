"""Project for program selection"""
"""
This application gets in a program code and then gives out information based on 
the program code.
"""
import csv
import webbrowser
# First open the database and store the information in a dictionary.

with open('Program data1.csv', 'r') as file:
    reader = csv.reader(file)
    reader.__next__()
    info_dict = {}
    for row in reader:
        info_dict.__setitem__(row[1], [row[0], row[2], row[3], row[4]])

user_input = input("Please enter the program code you want information about. "
                   "     Enter STOP to stop.")

while user_input != "STOP":
    if user_input in info_dict:
        print("Program name: " + info_dict[user_input][0])
        print("Program type: " + info_dict[user_input][1])
        print("Deregulated fees: " + info_dict[user_input][2])
        website = input("Enter Y/y to open the program website?")
        if website == "Y" or website == "y":
            url = info_dict[user_input][3]
            webbrowser.open(url)
    else:
        print("A program with this code doesn't exist at UTM. Please enter a correct program code.")

    user_input = input("Please enter the program code you want information about. "
                       "     Enter STOP to stop.")

# print("Thanks for using this program.")


with open('Program data1.csv', 'r') as file:
    reader = csv.reader(file)
    reader.__next__()
    info_dict = {}
    for row in reader:
        print(len(row))
