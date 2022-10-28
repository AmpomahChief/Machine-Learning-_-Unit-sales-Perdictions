PROJECT OBJECTIVE
The objective of this project is to train a regression model that predicts a unit sale for a super mart business, Corporation Favorita, a large Ecuadorian-based grocery retailer.

Technologies Used: Python
Project Status: Completed 

DATA STRUCTURE.
File Descriptions and Data Field Information
train.csv
•	The training data, comprising time series of features store_nbr, family, and onpromotion as well as the target sales.
•	store_nbr identifies the store at which the products are sold.
•	family identifies the type of product sold.
•	sales gives the total sales for a product family at a particular store at a given date. Fractional values are possible since products can be sold in fractional units (1.5 kg of cheese, for instance, as opposed to 1 bag of chips).
•	onpromotion gives the total number of items in a product family that were being promoted at a store at a given date.
test.csv
•	The test data, having the same features as the training data. You will predict the target sales for the dates in this file.
•	The dates in the test data are for the 15 days after the last date in the training data.
transaction.csv
•	Contains date, store_nbr and transaction made on that specific date.
sample_submission.csv
•	A sample submission file in the correct format.
stores.csv
•	Store metadata, including city, state, type, and cluster.
•	cluster is a grouping of similar stores.
oil.csv
•	Daily oil price which includes values during both the train and test data timeframes. (Ecuador is an oil-dependent country and its economical health is highly vulnerable to shocks in oil prices.)
holidays_events.csv
•	Holidays and Events, with metadata

QUESTIONS ASKED
These are questions that I seek to answer after processing and analyzing the data set. These questions give a better perspective on understanding the data.
•	Which location has the highest the number of stores?
•	Which city had the most sales?
•	What is the highest selling year, month, week and day?
•	Which year had the highest number of transactions?
•	Which store had the greatest number of transactions
•	Which store had the most sales?
•	Which family product sales the most?
•	Which type of holiday brings about more sales?
•	What is the impact of oil prices on sales?

HYPOTHESIS 
•	Sales are positively affected by holidays.
•	Sales are affected negatively when oil prices go up.







DATA PROCESSING
The data processing started with checking for some basic information about the data such as the ‘info’ , unique values in the family column, and the shape of the data  that’s the number of rows and columns 
HANDLING MISSING VALUES IN THE TRAIN DATA SET
The completeness of the data also had to be checked. Since it’s a time series project all dates within the range should not missing. After checking, it was realized that the data was missing the 25th of December of each year.  The missing data was extracted and added to the train data using the ‘concat’ function. 
We could also observe from our train dataset that we have null values in the 'sales' and 'onpromotion' column. Since all our missing values were on the 25th of December, we could assume that the stores didn't open and for that matter there was no sales on that day. Similarly, the same applies to the 'onpromotion' column, if its a holiday, then there can't be a promotion running. With this all null values in the 'sales' and 'onpromotion' was filled out zeros to indicate no sales and no promotions running.
PROCESSING THE STORE DATA SET.
The store data had no missing data but the location/city had to added. The data had the store numbers so they mapped to their respective cities. After adding the city column, the store data was merged with the train data.

ANSWERING QUESTIONS
1.	Which location has the highest the number of stores?
This question was answered by grouping the by cities and aggregating store number column to obtain the sum. This gave us a list of cities with the most stores. Quito had the most number of stores with 21,390,336 stores and Libertad had the least number of stores with 2,005,344 stores.


2.	Which city had the most sales?
The purpose of this question is to find out which city had the most sales regardless of the number of stores. 
To get this data, the data was grouped by city and aggregated by the sum of sales . This gave a data set of cities and the sum of it made over the period. Not surprisingly Quito came out with most sales with 556,741,837 and Puyo came last with 4,090,202. 
Although Libertad had the least number of stores, it wasn’t the city with the least sales. It actually placed 8th out of 21 city locations.
 

3.	What is the highest selling year, month, week and day?

The highest selling year
This was to obtain the year with the most sales. The data was group by the year and aggregated by the sum of sales. 2016 came out with the most sales and followed by 2015, 2014, 2017 and 2013.
 

The highest selling month
This is to obtain the month with the most sales. This is obtained by grouping the data by month and aggregating it by the sum of sales. Month 7 which July was the highest selling month followed by March, December and so on.
 
The highest selling week
This is to obtain the week with the most sales through out the period. This was obtained by grouping the data by week and aggregating it by the sum of sales. Not surprisingly the week 27 which falls in July had the most sales, followed by week 1 in January.
 

The highest selling day
This is to ascertain the day with the most sales. To get this the data was grouped day and aggregated by the sum of sales. Day 2 came out with most sales followed by day 1.
 

4.	Which year had the highest number of transactions?
To obtain this data we had to use the transactions data that was provided.  The transaction data contains data on the number of transactions that occurred in every store.
The transaction data was grouped by the year and aggregated by the sum of transactions to get the total number of transactions for each year. 2015 had the most number of transactions followed by 2016,  2014,  2013 and 2017.

5.	Which store had the greatest number of transactions
To get this, the transactions data was grouped by the store number and aggregated by the number of transactions . store number 44 had the most transactions followed by 47, 45, 46 and so on .
 
6.	Which store had the most sales?
To get this the train data was grouped by store number and aggregated by the sum of sales . store number 44 had the most sales followed by 45, 47, 3 and so on.
 

7.	Which family product sales the most?
This is to obtain the type product the sells the most in the super market. To get this data the train data was grouped by the family column (which contains the type of products) and aggregated by the sum of sales. It realized that groceries had the highest number of sales followed by beverages, produce, cleaning and so on.
 
PROCESSING THE HOLIDAY DATA
The holiday dataset contains data about national and local that were observed. This is important because holidays affect sales .
The transferred column is filled 'True' or 'False'. True suggests the holiday was transferred and vise versa, A holiday that is transferred officially falls on that calendar day but was moved to another date by the government. A transferred day is more like a normal day than a holiday. For example, the holiday Independencia de Guayaquil was transferred from 2012-10-09 to 2012-10-12, which means it was celebrated on 2012-10-12.
Days that are type Bridge are extra days that are added to a holiday (e.g., to extend the break across a long weekend). These are frequently made up by the type Work Day which is a day not normally scheduled for work (e.g., Saturday) that is meant to payback the Bridge.
Since transferred holidays are the same as normal days, those days will be taken out and the days that they were transferred to will be taken as the day of the holiday. The transferred holiday is a normal day and thus does not affect sales in any unique way.

8.	Which type of holiday brings about more sales?
To obtain this data the holiday data was grouped by the type of holiday and aggregated by the sum of sales. This came out that normal holidays had the most sales followed by events, additional days to holidays and holidays that were transferred
Again, we had to check for which holiday be it a national holiday, local holiday or reginal holiday brings in more sales. This came out that national holidays brings about more sales followed by Local holidays and then reginal holidays

PROCESSING THE OIL DATA
The oil data contains the changes in the oil prices within the year of review (2013 - 2017). The oil data contained dates and the prices of oil on that date. It had some null values in them, to fill them the back fill method was used. After the null values were filled up we then merged it with the trian data to make some analysis on the effect of oil prices on sales.
9.	What is the impact of oil prices on sales?
To get this data, the data was grouped by sales and aggregated by the oil prices. it can be seen that when oil prices are go up or when oil prices are high, sales is low and vise versa. This shows that there’s an inverse relationship between the oil prices and sales. This shows that the impact of oil prices on sales is negative when oil prices go up.
 
CONCLUSION TO THE HYPOTHESIS
•	Sales are positively affected by holidays.
From the analysis we can see that the sum of sales on normal days out weighs that on the sales on holidays. This is expected because the number of normal days are far greater than the days of holidays.
However we see a different story when the max sales on holidays and normal days are extracted. The max sales on holidays are huge than the sales on ordinary days which are not holidays. This clearly shows that holidays have positive impact on sales. Customers buy more on holidays.

•	Sales are affected negatively when oil prices go up.
From the analysis it can be seen that when oil prices are go up or when oil prices are high, sales is low and vice versa. This shows that there’s an inverse relationship between the oil prices and sales. This shows that the impact of oil prices on sales is negative when oil prices go up



FEATURE ENGINEERING
After analysing the data and ploting some graphs, we can then move to preparing the data to train the model. Feature engineering involves adding some features to the data which will help in training the model. 
Features such as extracting the month, year, week and day separately from the to help the model. Other features such as weekend, start of the month, end of the month, which quarter it is, start of the year, end of the year,  and what season it is were also extracted from the date to help train the model.


ENCODING 
Encoding is simply assigning numerical values to text. Since this is a machine learning project all columns with text must be encoded before training a model. Columns such as the season, family, city, type, locale and description were all encoded in numerical values before training the model. The LabelEncoder from sklearn was used for this process.
TRAINING THE MODELS
Before training the model it is important that we split the data into train and test .  The train data contained data from for all the years except  2017 and the test data contained data for the rest of 2017 which is January to August 2017.
For this process three models will be trained and the one the better results will be chosen. The models we would use are :
•	DecisionTreeRegressor
•	RandomForestRegressor
•	LinearRegression

Performance Measures
A typical performance measure for regression is the Root Mean Squared Error (RMSE). It gives an idea of how much error the system typically makes in its predictions, with higher weight for larger errors. 

Even though the RMSE is generally the preferred performance measure for regression tasks, in some contexts you may prefer to use another measure. For example, suppose that there are many outlier districts. In that case, you may consider using the Mean Absolute Error (MAE). 
Mean Absolute Error (MAE) and Root mean squared error (RMSE) are two of the most common metrics used to measure accuracy for continuous variables. 

Similarities: Both MAE and RMSE express average model prediction error in units of the variable of interest. Both metrics can range from 0 to ∞ and are indifferent to the direction of errors. They are negatively oriented scores, which means lower values are better. 

Differences: Taking the square root of the average squared errors has some interesting implications for RMSE. Since the errors are squared before they are averaged, the RMSE gives a relatively high weight to large errors, that is, it is more sensitive to outliers than the MAE. But when outliers are rare, the RMSE performs very well.

Root Mean Squared Logarithmic Error (RMSLE)
It is the Root Mean Squared Error of the log-transformed predicted and log-transformed actual values. RMSLE adds 1 to both actual and predicted values before taking the natural logarithm to avoid taking the natural log of possible 0 (zero) values.

