# Car_Sales_Data_Analysis
## Overview:

+ This is a sales report for a Car Sales company 

---

## Contents

+ [Project Overview](#Project-Overview) |+ [Data Source](#Data-Source) |+ [Tools Used](#Tools-Used) |+ [Table Outlay](#Table-Outlay) |+ [Query Language](#Query-Language) |+ [VIsualisation](#VIsualisation)

---
## Project Overview

>>

--- 
## Data Source
www.kaggle.com/dataset

---
## Tools Used
+ Pivot table/ Charts
+ PowerBi
+ SQL

## Table Outlay:
FIrst Four Rows
|b|	Date|	Customer Name|	Gender|	Annual Income|	Dealer_Name|	Company|	Model|	Engine|	Transmission|	Color|	Price ($)|	Dealer_No| 	Body Style|	Phone|	Dealer_Region|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|C_CND_000001|	1/2/2022|	Geraldine|	Male|	13500| Buddy Storbeck's Diesel Service Inc|	Ford|	Expedition|	DoubleÃ‚Â Overhead Camshaft|	Auto|	Black|	26000|	06457-3834|	SUV| 8264678|	Middletown|
|C_CND_000002|	1/2/2022|	Gia|	Male|	1480000|	C & M Motors Inc|	Dodge|	Durango|	DoubleÃ‚Â Overhead Camshaft|	Auto|	Black|	19000|	60504-7114|	SUV|	6848189|	Aurora|
|C_CND_000003|	1/2/2022|	Gianna|	Male|	1035000|	Capitol KIA|	Cadillac|	Eldorado|	Overhead Camshaft|	Manual|	Red|	31500|	38701-8047|	Passenger|	7298798|	Greenville|

## Query Language:

### SQL
Some of the query languages to retrieve records are displayed here

```SQL
---Categorize customers into gold, silver and diamond based on price---
SELECT Price, 
CASE
WHEN Price <= 15000 THEN 'Silver'
WHEN Price >= 40000 THEN 'Gold'
ELSE 'Diamond'
END AS Customer_Segment
FROM [dbo].[new_car_dataset];

```

```SQL
---retrieve all female customers that bought cars above 40000---
SELECT * FROM [dbo].[new_car_dataset]
WHERE Gender = 'Female'
AND Price >= 40000;

```

```SQL
---Retrieve the sales by color, arranging from largest to smallest amount---
SELECT Color,
COUNT (*) AS Carsold, 
SUM(Price) AS TotalSales
FROM [dbo].[new_car_dataset]
GROUP BY Color
ORDER BY TotalSales DESC;

```

```SQL
---Retrieve the Sales by Dealer Region---
SELECT Dealer_Region, SUM(Price)TotalSales
FROM [dbo].[new_car_dataset]
GROUP BY Dealer_Region
ORDER BY TotalSales DESC;

```

```SQL
---Retrieve the Sales by Body styles---
SELECT Body_Style, SUM(Price)TotalSales
FROM [dbo].[new_car_dataset]
GROUP BY Body_Style
ORDER BY TotalSales DESC;

```

```SQL
---Retrieve the COUNT of Sales by Body styles---
SELECT Body_Style, COUNT(*) AS Totalsold
FROM [dbo].[new_car_dataset]
GROUP BY Body_Style
ORDER BY TotalSold DESC;
```
