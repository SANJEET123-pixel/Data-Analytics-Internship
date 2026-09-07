CREATE DATABASE decodelabs_project3;

USE decodelabs_project3;


-- 1. Display all orders
SELECT * FROM orders;


-- 2. Count total orders
SELECT COUNT(*) AS Total_Orders
FROM orders;


-- 3. Display first 10 orders
SELECT *
FROM orders
LIMIT 10;


-- 4. Orders with total price greater than 2000
SELECT *
FROM orders
WHERE TotalPrice > 2000;


-- 5. Orders from highest to lowest price
SELECT *
FROM orders
ORDER BY TotalPrice DESC;


-- 6. Total revenue
SELECT ROUND(SUM(TotalPrice),2) AS Total_Revenue
FROM orders;


-- 7. Average order value
SELECT ROUND(AVG(TotalPrice),2) AS Average_Order_Value
FROM orders;



-- 8. Total quantity sold
SELECT SUM(Quantity) AS Quantity_Sold
FROM orders;


-- 9. Total sales by product
SELECT Product,
       ROUND(SUM(TotalPrice),2) AS Total_Sales
FROM orders
GROUP BY Product
ORDER BY Total_Sales DESC;


-- 10. Number of orders for each product
SELECT Product,
       COUNT(*) AS Number_of_Orders
FROM orders
GROUP BY Product
ORDER BY Number_of_Orders DESC;


-- 11. Average order value by product
SELECT Product,
       ROUND(AVG(TotalPrice),2) AS Average_Order_Value
FROM orders
GROUP BY Product
ORDER BY Average_Order_Value DESC;


-- 12. Orders and revenue by payment method
SELECT PaymentMethod,
       COUNT(*) AS Orders,
       ROUND(SUM(TotalPrice),2) AS Revenue
FROM orders
GROUP BY PaymentMethod
ORDER BY Revenue DESC;


-- 13. Orders by status
SELECT OrderStatus,
       COUNT(*) AS Number_Of_Orders
FROM orders
GROUP BY OrderStatus
ORDER BY Number_Of_Orders DESC;


-- 14. Orders and revenue by referral source
SELECT ReferralSource,
       COUNT(*) AS Orders,
       ROUND(SUM(TotalPrice),2) AS Revenue
FROM orders
GROUP BY ReferralSource
ORDER BY Revenue DESC;


-- 15. Orders and revenue by coupon code
SELECT CouponCode,
       COUNT(*) AS Orders,
       ROUND(SUM(TotalPrice),2) AS Revenue
FROM orders
GROUP BY CouponCode
ORDER BY Revenue DESC;


-- 16. Products having sales greater than 10000
SELECT Product,
       ROUND(SUM(TotalPrice),2) AS Total_Sales
FROM orders
GROUP BY Product
HAVING SUM(TotalPrice) > 10000
ORDER BY Total_Sales DESC;


-- 17. Yearly sales
SELECT YEAR(Date) AS Year,
       COUNT(*) AS Orders,
       ROUND(SUM(TotalPrice),2) AS Revenue
FROM orders
GROUP BY YEAR(Date)
ORDER BY Year;


-- 18. Monthly sales
SELECT YEAR(Date) AS Year,
       MONTH(Date) AS Month,
       COUNT(*) AS Orders,
       ROUND(SUM(TotalPrice),2) AS Revenue
FROM orders
GROUP BY YEAR(Date), MONTH(Date)
ORDER BY Year, Month;


-- 19. Top 10 highest value orders
SELECT OrderID,
       CustomerID,
       Product,
       Quantity,
       TotalPrice
FROM orders
ORDER BY TotalPrice DESC
LIMIT 10;


-- 20. Top 10 customers by spending
SELECT CustomerID,
       COUNT(*) AS Total_Orders,
       ROUND(SUM(TotalPrice),2) AS Total_Spent
FROM orders
GROUP BY CustomerID
ORDER BY Total_Spent DESC
LIMIT 10;
