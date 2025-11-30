# E-Commerce-PowerBI-Dashboard
A complete Data Analytics project using Power BI. Includes data cleaning, calculated measures using DAX, KPI cards, slicers, trend analysis, and visual insights to understand e-commerce business performance.

-- KPI: Total Sales
Total Sales = SUM(orders[quantity] * products[selling_price])

-- KPI: Total Profit
Total Profit = SUMX(
    orders,
    (orders[quantity] * RELATED(products[selling_price])) -
    (orders[quantity] * RELATED(products[cost_price]))
)

-- KPI: Total Orders
Total Orders = COUNTROWS(orders)

-- Sales by Year
Sales by Year = CALCULATE(
    SUM(orders[quantity] * products[selling_price]),
    YEAR(orders[date])
)

-- Top Category
Top Category = RANKX(
    ALL(products[category]),
    SUM(orders[quantity] * products[selling_price]),
    , DESC
)

