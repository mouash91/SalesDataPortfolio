### Superstore Sales Performance and Trend Analysis 
This repository contains a set of SQL queries designed to analyze the sales performance and trends in a superstore dataset. The queries cover various aspects such as price per item, total sales by year and month, category-wise and sub-category-wise sales with ranks, sales per region and state, and more. These queries provide valuable insights into the sales data and can be used for business analysis and decision-making.

### Queries

**Price per item and parse out year and month**

This part of the query extracts the relevant columns from the Sales table and calculates the price per item by dividing the sales amount by the quantity. It also extracts the year and month from the Order Date column for further analysis.

**Total Sales by year, sales difference between years, and year-over-year growth**

Using a common table expression (CTE), this section calculates the total sales for each year in the dataset. It also calculates the sales difference between the current year and the previous year and calculates the year-over-year growth percentage.

**Sales total per month**

Another CTE is used here to calculate the total sales for each month, along with the corresponding year. The month is formatted as a combination of the two-digit month number and the month name. The result is grouped by year and month.

**Total Sales per category with rank**

This section retrieves the total quantity and sales for each category in the dataset. It also assigns a rank to each category based on the total sales amount.

**Total Sales per sub-category with rank**

Similar to the previous section, this part calculates the total quantity and sales for each sub-category. It combines the category and sub-category names for better readability and assigns a rank based on the total sales amount.

**Total sales per region with rank**

Here, the query calculates the total sales for each region and assigns a rank based on the sales amount.

**Total sales per region and state**

This section provides the total sales for each combination of region and state. The results are ordered by region.

**Total sales of each category within each region with ranks**

The final part of the query calculates the total sales for each category within each region. It assigns a rank to each category based on the sales amount within its respective region.

**Skills Used**

The SQL queries in this repository demonstrate the utilization of various SQL skills and techniques, including:

- SELECT statement: Retrieves specific columns from tables.
- WITH statement (Common Table Expressions): Defines temporary result sets for complex queries.
- Aggregate functions: Calculates the sum of sales, quantity, and other metrics.
- Window functions (LAG, RANK, PARTITION BY): Performs calculations and ranking based on specific criteria.
- Conversion functions (YEAR, FORMAT, CONCAT, CAST): Extracts year, month, and other values from dates and converts data types.
- GROUP BY statement: Groups data based on specified columns for aggregations.
- ORDER BY statement: Sorts the results based on specific columns and order.
- These skills are crucial for analyzing sales performance and trends, making comparisons, and ranking the data to gain valuable insights.
