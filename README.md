# Currency-Converter

from bs4 import BeautifulSoup
import urllib3
from tkinter import *


def choose_currency(currency_value, currency):  # Sets chosen currency on button press
    calculate(currency_value)  # Sends chosen currency to be used in calculations

    choice_label2.config(text=currency)  # Updates various labels depending on chosen currency
    answer_currency_label.config(text=currency + "s: ")
    rate_value_label.config(text=currency_value)
    choice_label.config(text="You chose: ")
    current_rate_label.config(text="Current exchange rate: ")


def calculate(currency):  # Acquires user input (dollar amount), calculates worth in chosen currency
    user_input = user_USD.get()
    if user_input == '':
        answer_label.config(text="Type number of dollars")
    else:
        total_value = int(user_input) * float(currency)
        answer_label.config(text=round(total_value, 5))


url = "https://www.x-rates.com/table/?from=USD&amount=1"  # x-rates.com is scraped for current exchange rates
http = urllib3.PoolManager()
response = http.request('GET', url)
soup = BeautifulSoup(response.data, "html.parser")

euro = soup.find("a", href="https://www.x-rates.com/graph/?from=USD&to=EUR").string  # Acquires current exchange rates for each desired currency
british_pound = soup.find("a", href="https://www.x-rates.com/graph/?from=USD&to=GBP").string
canadian_dollar = soup.find("a", href="https://www.x-rates.com/graph/?from=USD&to=CAD").string
singapore_dollar = soup.find("a", href="https://www.x-rates.com/graph/?from=USD&to=SGD").string
japanese_yen = soup.find("a", href="https://www.x-rates.com/graph/?from=USD&to=JPY").string
mexican_peso = soup.find("a", href="https://www.x-rates.com/graph/?from=USD&to=MXN").string

window = Tk()  # Tkinter is used to allow easy changes in chosen currency
window.title("Currency Converter")

label1 = Label(window, text="How many U.S. Dollars do you want to convert? ")
label1.grid(row=0, column=0, columnspan=2)
user_USD = Entry(window)
user_USD.grid(row=1, column=0, columnspan=2)

label2 = Label(window, text="Choose a currency to convert to: ")
label2.grid(row=2, column=0, columnspan=2)

euro_button = Button(window, text="Euro", command=lambda: choose_currency(euro, "Euro"))
euro_button.grid(row=3, column=0)
b_pound_button = Button(window, text="Pound", command=lambda: choose_currency(british_pound, "Pound"))
b_pound_button.grid(row=3, column=1)
c_dollar_button = Button(window, text="Canadian Dollar", command=lambda: choose_currency(canadian_dollar, "Canadian Dollar"))
c_dollar_button.grid(row=4, column=0)
s_dollar_button = Button(window, text="Singapore Dollar", command=lambda: choose_currency(singapore_dollar, "Singapore Dollar"))
s_dollar_button.grid(row=4, column=1)
yen_button = Button(window, text="Yen", command=lambda: choose_currency(japanese_yen, "Yen"))
yen_button.grid(row=5, column=0)
peso_button = Button(window, text="Peso", command=lambda: choose_currency(mexican_peso, "Peso"))
peso_button.grid(row=5, column=1)

separation_label = Label(window, text="-------------------------------------------")
separation_label.grid(row=6, column=0, columnspan=2)

choice_label = Label(window, text="")
choice_label.grid(row=7, column=0)

choice_label2 = Label(window, text="")
choice_label2.grid(row=7, column=1)

separation_label2 = Label(window, text="-------------------------------------------")
separation_label2.grid(row=8, column=0, columnspan=2)

answer_label = Label(window, text="")
answer_label.grid(row=11, column=1)

answer_currency_label = Label(window, text="")
answer_currency_label.grid(row=11, column=0)

separation_label3 = Label(window, text="-------------------------------------------")
separation_label3.grid(row=10, column=0, columnspan=2)

current_rate_label = Label(window, text="")
current_rate_label.grid(row=9, column=0)

rate_value_label = Label(window, text="")
rate_value_label.grid(row=9, column=1)

separation_label4 = Label(window, text="-------------------------------------------")
separation_label4.grid(row=12, column=0, columnspan=2)

window.mainloop()
