Question 2: For this question you’ll need to use SQL. Follow this link to access the data set required for the challenge. Please use queries to answer the following questions. Paste your queries along with your final numerical answers below.
<ol type="a">
<li> How many orders were shipped by Speedy Express in total? </li>
	<code> `SELECT COUNT(*) FROM Orders where ShipperID=(select ShipperID from Shippers where ShipperName='Speedy Express')`</code>
    
    54 orders were shipped by Speedy Express in total.
<li> What is the last name of the employee with the most orders? </li>
    <code> `SELECT LastName from Employees e where e.employeeID=(select EmployeeID from (select EmployeeID, count(*) as orders FROM [Orders] group by EmployeeID order by orders desc limit 1))` </code>
    
    The last name of the employee with the most orders is Peacock.

<li> What product was ordered the most by customers in Germany? </li>
	<code> `SELECT p.productname,sum(od.quantity) as count FROM [Orders] o, [OrderDetails] od, [Products] p where customerID in (SELECT customerID FROM [Customers] where Country='Germany') and o.orderid=od.orderid and od.productid=p.productid group by p.productid order by count desc limit 1` </code>
    
    Boston Crab Meat was ordered the most by customers in Germany with a quantity of 160.
