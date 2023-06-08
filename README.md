# Superstore Sales Performance and Trend Analysis
This SQL query provides a comprehensive analysis of the sales performance and trends in the Superstore dataset. The query retrieves various metrics and rankings to help understand the sales patterns and identify areas of growth and opportunity. Let's break down each section of the query:

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

Overall, this SQL query offers a comprehensive analysis of sales performance and trends, providing insights into the Superstore dataset. It can be useful for identifying top-performing categories, sub-categories, regions, and states, as well as tracking year-over-year growth and monthly sales patterns.
