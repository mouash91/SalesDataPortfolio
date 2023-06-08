
**Superstore Sales Performance and Trend Analysis **


```sql
/* Price per item and parse out year and month */
SELECT 
	[Order Date] AS OrderDate,
	YEAR([Order Date]) AS Year,
	FORMAT(MONTH([Order Date]), '00') AS Month,
	[Customer ID] AS CustomerID,
	Segment,
	Country,
	City,
	State,
	[Postal Code] AS PostalCode,
	Region,
	Category,
	[Sub-Category],
	Sales,
	Quantity,
	CAST(CAST(Sales AS decimal(10, 2)) / Quantity AS decimal(10, 2)) AS PricePerItem,
	Profit 
FROM Sales;
```

```sql
/* Total Sales by year, sales difference between years, and year-over-year growth */

WITH CTE AS (
    SELECT
        YEAR([Order Date]) AS Year,
        SUM(CAST(Sales AS decimal(10, 2))) AS TotalSales,
        LAG(SUM(CAST(Sales AS decimal(10, 2)))) OVER (ORDER BY YEAR([Order Date])) AS PreviousYearSales
    FROM
        Sales
    GROUP BY
        YEAR([Order Date])
)
SELECT
    Year,
    TotalSales,
    TotalSales - PreviousYearSales AS SalesDifference,
    CAST((TotalSales - PreviousYearSales) / PreviousYearSales * 100 AS decimal(10, 1)) AS SalesDifferencePercentage
FROM
    CTE
ORDER BY
    Year DESC;
```

```sql
/* Sales total per month */

WITH CTE AS (
    SELECT
        YEAR([Order Date]) AS Year,
        CONCAT(FORMAT([Order Date], 'MM'), ' - ', DATENAME(month, [Order Date])) AS Month,
        CAST(Sales AS decimal(10, 2)) AS Sales
    FROM
        Sales
)
SELECT
    Year,
    Month,
    SUM(Sales) AS TotalSales
FROM
    CTE
GROUP BY
    Year, Month
ORDER BY
    Year DESC;
```

```sql
/* Total Sales per category with rank */

SELECT
    Category AS Category,
    SUM(Quantity) AS TotalQuantity,
    SUM(CAST(Sales AS decimal(10, 2))) AS TotalSales,
    RANK() OVER (ORDER BY SUM(CAST(Sales AS decimal(10, 2))) DESC) AS CategoryRank
FROM
    Sales
GROUP BY
    Category;
```

```sql
/* Total Sales per sub-category with rank */

SELECT
    CONCAT(Category, ' - ', [Sub-Category]) AS SubCategory,
    SUM(Quantity) AS TotalQuantity,
    SUM(CAST(Sales AS decimal(10, 2))) AS TotalSales,
    RANK() OVER (ORDER BY SUM(CAST(Sales AS decimal(10, 2))) DESC) AS SubCategoryRank
FROM
    Sales
GROUP BY
    Category, [Sub-Category]
ORDER BY
    Category;
```

```sql
/* Total sales per region with rank */

SELECT 
	Region AS Region,
	SUM(CAST(Sales AS decimal(10, 2))) AS TotalSales,
	RANK() OVER (ORDER BY SUM(CAST(Sales AS decimal(10, 2))) DESC) AS RegionSalesRank
FROM Sales
GROUP BY
	Region;
```

```sql
/* Total sales per region and state */

SELECT
	CONCAT(Region, ' - ', State) AS RegionState,
	SUM(CAST(Sales AS decimal(10, 2))) AS TotalSales
FROM Sales
GROUP BY
	Region, State
ORDER BY
	Region;
```

```sql
/* Total sales of each category within each region with ranks */

SELECT
    Region,
    Category,
    TotalSales,
    RANK() OVER (PARTITION BY Region ORDER BY TotalSales DESC) AS CategoryRank
FROM
    (
        SELECT
            Region,
            Category,
            SUM(CAST(Sales AS decimal(10, 2))) AS TotalSales
        FROM
            Sales
        GROUP BY
            Region, Category
    ) AS subquery
ORDER BY
    Region, TotalSales DESC;
```
