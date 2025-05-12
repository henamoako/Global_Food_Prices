# Global_Food_Prices
(https://raw.githubusercontent.com/henamoako/global-food_prices/refs/heads/main/wfp_market_food_prices.csv)
Analysis of the Dataset
1.	Structure or Shape of the Data
o	The dataset consists of 20 rows and 7 columns.
o	It is structured in a tabular format with clearly defined attributes.
2.	Granularity of the Data
o	The data appears to be at a market-level granularity. Each row represents a specific food commodity's price in a particular country and market on a given date.
o	The pricing information is provided in both local currency and USD.
3.	Scope and Completeness of the Data
o	The dataset includes information on food prices across multiple countries.
o	Columns include: commodity, country, market, price, usd_price, currency, and date.
o	No missing values (all 20 rows have non-null values for all columns).
o	The dataset is relatively small, so it may not be comprehensive for all global food prices.
4.	Temporality of the Data
o	The date column suggests a time-based relationship, with prices recorded on different dates.
o	The dataset appears time-series based, capturing price changes over time.
5.	Faithfulness of the Data
o	The dataset appears to correctly capture food prices in different markets with appropriate currency conversion.
o	However, with only 20 records, it may not fully represent the global food price landscape.
o	Further validation against official price indices or larger datasets would be needed to confirm accuracy.

Cleaning Summary:
Missing Data: Filled missing values in numeric columns with the median of the respective column, while leaving categorical columns untouched.
Erroneous Data: Removed currency symbols and commas from the mp_price column and converted it to a numerical type (float).
Duplicates: Identified and removed duplicate rows to ensure the analysis was based on unique data.
Data Types: Ensured that columns like mp_year were of the correct data type (integer).
Final Verification: Displayed the first few rows of the cleaned data to confirm the successful application of these steps.

import pandas as pd
df = pd.read_csv("https://raw.githubusercontent.com/henamoako/global-food_prices/refs/heads/main/wfp_market_food_prices.csv")

df.head()

"Distribution of mp_price"
plt.subplot(2, 2, 2)
df["mp_price"].hist()
plt.xlabel("mp_price")
plt.ylabel("Frequency")
plt.title("Distribution of mp_price")
plt.show()

"Distribution of mp_year"
plt.subplot(2, 2, 4)
df["mp_year"].hist()
plt.xlabel("mp_year")
plt.ylabel("Frequency")
plt.title("Distribution of mp_year")
plt.show()

Observation:
Most prices fall within a common range. The highest bars represent the most frequent price values.

The shape of the distribution is mostly balanced. This means there aren’t too many extremely high or low prices.

No major outliers. We don’t see any unusually high or low prices that stand out too much.
