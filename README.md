Trade Data Analysis Project
This project analyzes trading data from a dataset containing historical trades for various portfolios. The analysis includes calculations for financial metrics such as ROI (Return on Investment), Sharpe Ratio, Maximum Drawdown (MDD), Winning Trades, and the Total Number of Trades. The code processes each portfolio’s trade history and generates insights for further analysis.

Table of Contents
Installation
Data Description
Analysis Methods
ROI Calculation
Sharpe Ratio Calculation
Maximum Drawdown (MDD) Calculation
Winning Trades Calculation
Number of Trades Calculation
Usage
Error Handling
Conclusion
Installation
To run this analysis, you'll need the following Python libraries:

pandas
numpy
sklearn
ast
Install the dependencies using the following command:

bash
Copy code
pip install pandas numpy scikit-learn
Alternatively, you can open this code in Google Colab to run it without installing any dependencies locally.

Data Description
The dataset consists of a CSV file that contains the following columns:

Port_IDs: Portfolio ID for each set of trades.
Trade_History: A list of dictionaries where each dictionary contains details of a single trade, such as:
time: Unix timestamp of the trade.
symbol: Trading pair (e.g., ETHUSDT).
side: Whether the trade is a buy or sell order.
price: The price at which the trade was executed.
fee: Fee paid for the trade.
quantity: The quantity traded.
realizedProfit: The realized profit or loss from the trade.
Analysis Methods
ROI Calculation
The Return on Investment (ROI) is calculated for each portfolio by summing the net profit and dividing it by the total investment. The formula used is:

ROI= (Net Profit)/(Total Investment) ×100
​

Where:

Net Profit = realizedProfit + fee
Total Investment = sum(price \times quantity)
Sharpe Ratio Calculation
The Sharpe Ratio measures the risk-adjusted return of a portfolio. It is calculated by dividing the average daily return by the standard deviation of daily returns and annualizing the result over a 90-day period. The formula used is:


Sharpe Ratio=  (Average Daily Return)/((Standard Deviation of Returns)× Annualization Factor
Where the annualization factor for 90 days is:


Annualization Factor= root (365/90)
​
 
​
 
Maximum Drawdown (MDD) Calculation
The Maximum Drawdown represents the peak-to-trough decline of a portfolio's value during a specific period. It is calculated by determining the difference between the running maximum balance and the current balance and finding the highest such drawdown.

MDD= ((Peak Balance−Trough Balance)/Peak Balance)×100

Winning Trades Calculation
This calculates the number of trades in a portfolio where the net profit is positive (realizedProfit + fee > 0).

Number of Trades Calculation
This simply counts the total number of trades in the Trade_History for each portfolio.

Usage
Load the Dataset: The dataset is loaded using pandas and stored in a DataFrame.
python
Copy code
df = pd.read_csv('TRADES_CopyTr_90D_ROI.csv')
Preprocess the Data: Handle any missing values by dropping them.
python
Copy code
df = df.dropna().reset_index(drop=True)
Calculate Metrics: The financial metrics like ROI, Sharpe Ratio, MDD, and number of trades are calculated using loops that iterate over each portfolio’s trade history.
python
Copy code
# Example for calculating ROI
roi = (net_profit / total_investment) * 100
Store Results: The calculated values are added as new columns to the DataFrame.
python
Copy code
df['ROI'] = ROI
df['Sharp_Ratio'] = sharpRatio
df['MDD'] = mdd
df['winning_trades'] = winning_trades
df['number_of_trades'] = noOfTrades
Error Handling
The code handles various exceptions such as:

Missing or invalid data (NaN values in the trade history).
Calculation errors due to division by zero (e.g., in Sharpe Ratio when the standard deviation is zero).
These errors are logged, and the program continues processing the remaining portfolios.

Conclusion
This project provides a comprehensive analysis of historical trade data by calculating key performance metrics for each portfolio. The results can be further used to assess the risk and return of each portfolio and make informed decisions for future trading strategies.

Contact
For any questions or issues, please contact:

Name: [Gokul Singh Shah]
Email: [gokulsinghshah041@gmail.com]
