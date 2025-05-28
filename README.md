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

Milestone 7:
X = df[['mp_year', 'mkt_name', 'adm0_name']]  
y = df['mp_price']


X = pd.get_dummies(X, drop_first=True)


from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)


from sklearn.preprocessing import StandardScaler
scaler = StandardScaler()
X_train = scaler.fit_transform(X_train)
X_test = scaler.transform(X_test)

from sklearn.linear_model import LinearRegression
from sklearn.metrics import mean_squared_error, r2_score


linear_regressor = LinearRegression()
linear_regressor.fit(X_train, y_train)


y_pred = linear_regressor.predict(X_test)


mse = mean_squared_error(y_test, y_pred)  
r2 = r2_score(y_test, y_pred)  

print(f'Mean Squared Error: {mse}')
print(f'R-squared: {r2}')

X2 = df[['mp_year', 'mkt_name']]  


X2 = pd.get_dummies(X2, drop_first=True)


X2_train, X2_test, y_train, y_test = train_test_split(X2, y, test_size=0.2, random_state=42)


X2_train = scaler.fit_transform(X2_train)
X2_test = scaler.transform(X2_test)


linear_regressor.fit(X2_train, y_train)


y_pred2 = linear_regressor.predict(X2_test)
mse2 = mean_squared_error(y_test, y_pred2)
r2_2 = r2_score(y_test, y_pred2)

print(f'Mean Squared Error (Model 2): {mse2}')
print(f'R-squared (Model 2): {r2_2}')

Milestone 8:
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import StandardScaler
from sklearn.neighbors import KNeighborsRegressor
from sklearn.metrics import mean_squared_error, r2_score



X = df[['mp_year', 'mkt_name', 'adm0_name']]  
y = df['mp_price']  


X = pd.get_dummies(X, drop_first=True)


X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)


scaler = StandardScaler()
X_train = scaler.fit_transform(X_train)
X_test = scaler.transform(X_test)


knn = KNeighborsRegressor(n_neighbors=5)
knn.fit(X_train, y_train)


y_pred_knn = knn.predict(X_test)


mse_knn = mean_squared_error(y_test, y_pred_knn)
r2_knn = r2_score(y_test, y_pred_knn)


print(f'Mean Squared Error (KNN): {mse_knn}')
print(f'R-squared (KNN): {r2_knn}')

knn_5 = KNeighborsRegressor(n_neighbors=5)
knn_5.fit(X_train, y_train)


y_pred_knn_5 = knn_5.predict(X_test)
mse_knn_5 = mean_squared_error(y_test, y_pred_knn_5)
r2_knn_5 = r2_score(y_test, y_pred_knn_5)

print(f'Mean Squared Error (KNN with k=5): {mse_knn_5}')
print(f'R-squared (KNN with k=5): {r2_knn_5}')


knn_10 = KNeighborsRegressor(n_neighbors=10, metric='manhattan')
knn_10.fit(X_train, y_train)


y_pred_knn_10 = knn_10.predict(X_test)
mse_knn_10 = mean_squared_error(y_test, y_pred_knn_10)
r2_knn_10 = r2_score(y_test, y_pred_knn_10)

print(f'Mean Squared Error (KNN with k=10, Manhattan): {mse_knn_10}')
print(f'R-squared (KNN with k=10, Manhattan): {r2_knn_10}')


Milestone 9:
