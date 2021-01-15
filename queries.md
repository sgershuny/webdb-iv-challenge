# Database Queries

### Display the ProductName and CategoryName for all products in the database. Shows 76 records.

SELECT p.productname,c.categoryname
FROM Products as p
inner JOIN Categories as c on c.categoryID = p.categoryID

### Display the OrderID and ShipperName for all orders placed before January 9, 1997. Shows 161 records.

SELECT s.ShipperName,o.OrderId,o.OrderDate
FROM Shippers as s
inner JOIN Orders as o on o.ShipperId = s.ShipperId
WHERE o.orderDate < date('1997-01-09')

### Display all ProductNames and Quantities placed on order 10251. Sort by ProductName. Shows 3 records.

SELECT p.ProductName, od.Quantity,od.OrderId
FROM Products as p
inner JOIN OrderDetails as od on od.ProductId = p.productId
WHERE od.OrderId = 10251
ORDER BY p.ProductName asc 

### Display the OrderID, CustomerName and the employee's LastName for every order. All columns should be labeled clearly. Displays 196 records.

SELECT o.OrderId, c.CustomerName, e.LastName
FROM Orders as o
inner JOIN Customers as c on c.CustomerId = o.CustomerId
inner JOIN Employees as e on e.EmployeeId = o.EmployeeId

### (Stretch)  Displays CategoryName and a new column called Count that shows how many products are in each category. Shows 9 records.

SELECT c.CategoryName, c.CategoryId, count( p.ProductName) as count
FROM Categories as c
inner JOIN Products as p on c.CategoryId = p.CategoryId
GROUP BY c.CategoryId

### (Stretch) Display OrderID and a  column called ItemCount that shows the total number of products placed on the order. Shows 196 records. 

SELECT OrderId, count(ProductId) FROM OrderDetails
GROUP BY OrderId
