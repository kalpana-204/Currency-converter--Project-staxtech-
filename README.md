import requests

def convert_currency(from_currency, to_currency, amount):
    url = f"https://api.exchangerate.host/convert?from={from_currency}&to={to_currency}&amount={amount}"
    response = requests.get(url)

    if response.status_code == 200:
        result = response.json()
        converted_amount = result['result']
        print(f"{amount} {from_currency} = {converted_amount:.2f} {to_currency}")
    else:
        print("Error fetching data from API")

# Example usage
print("Currency Converter")
from_curr = input("From currency (e.g., USD): ").upper()
to_curr = input("To currency (e.g., INR): ").upper()
amount = float(input("Amount: "))

convert_currency(from_curr, to_curr, amount)
