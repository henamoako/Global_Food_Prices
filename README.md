# Global_Food_Prices
[global_food_prices_extended.csv](https://github.com/user-attachments/files/18936323/global_food_prices_extended.csv)
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
Data Validation: The dataset was checked for missing values, erroneous data, and extra characters. No issues were found.

Date Format Fixed: The date column was converted from a string format to a datetime format for consistency.

No Duplicate Rows: An inspection revealed that there were no duplicate rows in the original dataset.

Data Integrity: All columns are correctly formatted and consistent, and no further cleaning was necessary.



df = pd.read_csv("https://raw.githubusercontent.com/henamoako/Global_Food_Prices/main/global_food_prices_extended.csv")
df.head()


df['date'] = pd.to_datetime(df['date'], errors='coerce')


plt.figure(figsize=(8, 5))
sns.histplot(df['price'], bins=6, kde=True, color='blue')


plt.title('Distribution of Food Prices', fontsize=14)
plt.xlabel('Price', fontsize=12)
plt.ylabel('Frequency', fontsize=12)



plt.show()


Observation:
Most prices fall within a common range. The highest bars represent the most frequent price values.

The shape of the distribution is mostly balanced. This means there aren’t too many extremely high or low prices.

No major outliers. We don’t see any unusually high or low prices that stand out too much.
