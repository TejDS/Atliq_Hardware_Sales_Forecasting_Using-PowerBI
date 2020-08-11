# Sales_Forecasting_Project_End_To_End

# Problem Statement :

Atliq hardware is a company which supplies computer hardware and peripheral manfacturer to many of there clients{Surge Stores,Nomad Stores,Excel Stores,Electricalsara Stores} across India. There Head Office is located in New Delhi and they have lot of regional offices across India.
                                                                                              
                                                                                                      Bhavin Patel is the sales director  of the company and he is facing many challenges. So, the challenge is this the market is growing dynamically and he is facing issues tracking the sales in the dynamically growing market and he is having issues with the insights of his business. He has regional managers for South India, North India and Central India.Whenever he wants to get insights in these three regions he would call these people and on phone these local regional managers will give him some insights this was the sales last quarter and we are going to grow by this much by next quarter. Sometimes there are chances of managers lying and manipulate the facts. The sales director is frustrated with this as he see's that sales are declining and when he talks with regional manager he doesnt get a complete picture. When asked for numbers regarding sales  he was given lot of excel files which has lots of data. He wants a dashboard with real time data
Whicch will help him to know the facts and performance in much better way and save his time.                                                                                                    


# Technology used to solve this problem:

Business Intelligence is a  method of collecting, storing and analyzing data of business operations. It has an impact on organizational startegical decision about business operations which inturn will have huge impact on the financial model and revenue of the orgnization.

## Power BI is a business analytics solution that lets you visualize the data and share the insights to the concern stakeholders and business owners.

![alt text](https://www.kdatascience.com/wp-content/uploads/2019/08/Power-BI-Business-Intellgence-Reporting.jpg)


# Data Discovery :

### Tool Used Is AIMSGRID

(i) Purpose : To unlock sales insights that are not visible before the sales team for decision support and automate them to reduced manual time spent in data gathering.
(ii) Stakeholders : Sales Director,Marketing team, Customer Service Team, Data & Analytics Team,IT.
(iii) End Result : An automated dashboard providing quick and latest sales insights in order to support data driven decision making.
(iv) Success Criteria : Dashboard(s) uncovering sales order insights with latest data available.Sales team able to take better decisions and prove 10% cost savings of total spend. Sales Analysts stop data gathering manually in order to save 20% of their business time and reinvest it value added activity.


Now data analyst team approaches IT team within organization who owns software system that keep track of sales records. These records are stored in the SQl Server.

# Data Analysis Using SQL:

MySQL

![alt text](https://www.freepnglogos.com/uploads/logo-mysql-png/logo-mysql-mysql-logo-png-images-are-download-crazypng-21.png)

Show all customer records

SELECT * FROM customers;

Show total number of customers

SELECT count(*) FROM customers;

Show transactions for Chennai market (market code for chennai is Mark001

SELECT * FROM transactions where market_code='Mark001';

Show distrinct product codes that were sold in chennai

SELECT distinct product_code FROM transactions where market_code='Mark001';

Show transactions where currency is US dollars

SELECT * from transactions where currency="USD"

Show transactions in 2020 join by date table

SELECT transactions.*, date.* FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020;

Show total revenue in year 2020,

SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and transactions.currency="INR\r" or transactions.currency="USD\r";

Show total revenue in year 2020, January Month,

SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and and date.month_name="January" and (transactions.currency="INR\r" or transactions.currency="USD\r");

Show total revenue in year 2020 in Chennai

SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and transactions.market_code="Mark001";

# Data Cleaning and ETL Using Power BI:
(i) Filtered blank rows in sales markets table.

(ii) select * from sales.transactions  where sales_amount<=0;(Removed Rows having sales_amount as 0 and -1 from sales transaction table).

(iii) Converting USD to INR : = Table.AddColumn(#"Filtered Rows", "Normalized Currency", each if [currency] = "USD" then [sales_amount] *75 else [sales_amount])

# Data Modelling: (Star Schema)
![image](https://user-images.githubusercontent.com/65170754/89860132-57b67300-dbc0-11ea-8f10-586100943ee0.png)


# DashBoard

https://app.powerbi.com/view?r=eyJrIjoiYjAwOTc1NmYtMzA2MC00YzgzLTg3ZWMtNWVjM2I5ODZkZGVhIiwidCI6ImFjZjcwOGQyLTg0ZjAtNGQ0Mi04MmE2LTQyMDc3NTNmOWJjNiJ9
