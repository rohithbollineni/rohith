import io
import sys
import requests
import telepot
from bs4 import BeautifulSoup

print("\n************ Welcome to Stock Screener ************\n")
stock_name = input("Enter Stock Name to Display details: ")

# sys.stdout = buffer = io.StringIO()
sendingMsg=""
# sys.stdout = open("test.txt","w")

url = f"https://ticker.finology.in/company/{stock_name}"
htmlContent = requests.get(url)
soup = BeautifulSoup(htmlContent.content,'html.parser')

sendingMsg += stock_name.capitalize()+ " Share Price, Financials and Stock Analysis:\n"

print(stock_name.capitalize()," Share Price, Financials and Stock Analysis:\n")
stock_price = soup.find("span",class_="Number").get_text()
sendingMsg += f"\nStock Price of the Company: {stock_price}"
print("Stock Price of the Company:",stock_price)

stock_mCap = soup.find(class_="col-6 col-md-4 compess")
sendingMsg += f"\nMarketCap: {stock_mCap.p.span.get_text()}"

print("MarketCap:",stock_mCap.p.span.get_text())
stock_change = soup.find(id="mainContent_pnlPriceChange").get_text().strip()
stock_change = stock_change.replace(" ","")
sendingMsg += f"\nPrice Change & Percentage Change: {stock_change}"

print("Price Change & Percentage Change:",stock_change)
sendingMsg += "\n\nCompany's Financials:\n\n"
print("\nCompany's Financials:\n")

one = soup.find(id="mainContent_divOwner").get_text().split()
one = one[2:len(one)]
for i in one:
    sendingMsg += f"{i}  "
    print(i, end=" ")
sendingMsg += "\n\n"
print("\n")

two = soup.find(id="mainContent_divValuation").get_text().split()
two = two[2:len(two)]
for i in two:
    sendingMsg += f"{i}  "
    print(i, end=" ")
sendingMsg += "\n\n"
print("\n")

three = soup.find(id="mainContent_divEff").get_text().split()
three = three[2:len(three)]
for i in three:
    sendingMsg += f"{i}  "
    print(i, end=" ")
sendingMsg += "\n\n"
print("\n")

four = soup.find(id="mainContent_divFinance").get_text().split()
four = four[2:len(four)]
for i in four:
    sendingMsg += f"{i}  "
    print(i, end=" ")
sendingMsg += "\n\n"
print("\n")
# sys.stdout.close()

# print("Data Succesfully sent to file..")

token = '5679243130:AAHVHiIOZkxArmI434hPIXFCtDvwVOcGno0'
reciever_id = 5571389671 #my telegram ID

bot = telepot.Bot(token)
bot.sendMessage(reciever_id,sendingMsg)
print("Message Succesfully Sent to your Telegram!")
