# Subqueries and Joins

## Subqueries
Son consultas incrustadas en otras consultas (una consulta dentro de otra consulta) son utiles cuando se requiere informacion de varias tablas.
~~~~Mysql
SELECT column_name_1
	,column_name_2
	,column_name_3
FROM table_name_1
WHERE column_name_1 IN (
		SELECT column_name_1
		FROM table_name_2
		WHERE column_name operator value
		);
~~~~
No hay limite en el numero de subconsultas que puedes tener en una declaracion, se debe tener en cuenta que las selecciones de una subconsulta solo pueden recuperar una sola columna.

### Subquery in Subquery
~~~~Mysql
SELECT customer_name
	,customer_contact
FROM customers
WHERE cust_id IN

    SELECT customer_id
    FROM orders
    WHERE order_number IN (
		    SELECT order_number
		    FROM order_items
		    WHERE prod_name = 'Toothbrush'
		    );
~~~~

Tambien es importante hacer una buena identacion del codigo, esto facilita la lectura y comprension de las subconsultas, si se toma codigo SQL de algun sistema y no esta identado el sitio [PoorSQL](https://poorsql.com/) identa de forma automatica el codigo que le suministremos.

### Subqueries for calculations
Finalmente tambien es importante mencionar que tabien se pueden usar sudconsultas para hacer calculos.

En este ejemplo calculamos el numero total de ordenes por estado para cada cliente.
~~~~Mysql
SELECT Customer_name
	,Customer_state
	,(
		SELECT COUNT(*) AS orders
		FROM Orders
		WHERE Orders.Customer_id = Customer.customer_id
		) AS orders
FROM Customers
ORDER BY Customer_name;
~~~~
| Customer_name | Customer_state | orders |
| ------------- | -------------- | ------ |
| Becky		| IA		 | 5	  |
| Nita		| CA		 | 6	  |
| Raj		| OH		 | 0	  |
| Steve		| AZ		 | 1	  |


## Joining Tables
La sentencia JOIN (unir, combinar) permite combinar registros de una o más tablas en una base de datos. En el Lenguaje de Consultas Estructurado (SQL) hay tres tipos de JOIN: `interno`, `externo` y `cruzado`. El estándar ANSI del SQL especifica cinco tipos de JOIN: INNER, LEFT OUTER, RIGHT OUTER, FULL OUTER y CROSS. Una tabla puede unirse a sí misma, produciendo una auto-combinación, SELF-JOIN.

### Cartesian (Cross) Joins
Este tipo de union permite tomar cada elemento de la primera tabla y emparejarlo con todos los registros de la segunda tabla, si la primera tabla tiene **X** filas y la segunda tiene **Y** filas, el resultado sera una tabla de $X\*Y$ filas.

~~~~Mysql
SELECT product_name
	,unit_price
	,company_name
FROM Suppliers
CROSS JOIN Products;
~~~~

### Inner Joins
Una combinación interna se usa para seleccionar registros que tienen valores coincidentes en ambas tablas. Entonces aquí es donde las claves se vuelven realmente importantes en las tablas.

~~~~Mysql
SELECT Suppliers.CompanyName
	,ProductName
	,UnitPrice
FROM Suppliers
INNER JOIN Products ON Suppliers.supplierid = Products.supplierid;
~~~~

Con multiples tablas

~~~~Mysql
SELECT o.OrderId
	,c.CompanyName
	,e.LastName
FROM (
	(
		Orders o INNER JOIN Customers c ON o.CustomerID = c.CustomerID
		) INNER JOIN Employees e ON o.EmployeeID = E.EmployeeID
	);
~~~~

## Aliases and Self Joins
### Aliases
Los alias se usan para simplicar la escritura de las consultas, puedo asignarle un alias a un objeto para facilitar su llamado.

**Query sin alias**
~~~~Mysql
SELECT vendor_name
	,product_name
	,product_price
FROM Vendors, Products
WHERE Vendors.vendor_id = Products.vendor_id;
~~~~

**Query con alias**
~~~~Mysql
SELECT vendor_name
	,product_name
	,product_price
FROM Vendors AS v, Products AS p
WHERE v.vendor_id = p.vendor_id;
~~~~

### Self Joins
Self Joins es un caso especial popular del JOIN. Mientras que la mayoría de los JOIN vinculan dos o más tablas entre sí para presentar sus datos juntos, una combinación de sí mismo vincula una tabla a sí misma. Esto normalmente se hace uniendo una tabla a sí misma solo una vez dentro de una consulta SQL, pero es posible hacerlo varias veces dentro de la misma consulta.

Normalmente, cada tabla de una base de datos almacena un tipo específico de información. Por lo tanto, a menudo hay cientos de tablas relacionadas entre sí en una base de datos. Esto implica la necesidad de uniones. Puede unir diferentes tablas por sus columnas comunes mediante la palabra clave. También es posible unirse a una tabla para sí mismo. Este último se conoce como Self Joins.

## Advanced Joins: Left, Right, and Full Outer Joins
### Left Join
Esta union es una union por la izquierda, asumiendo que tenemos dos tablas, x e y, el left join hace la union entre estas tablas conservando todos los elementos de x.
~~~~Mysql
SELECT C.CustomerName
	,O.orderId
FROM Customers C
LEFT JOIN Orders O ON C.CustomerId = O.CustomerId
ORDER BY C.CustomerName;
~~~~

### Right Join
Esta union es por la drecha, en este caso conserva todos los elementos de y.
~~~~Mysql
SELECT Orders.OrderId
	,Employees.LastName
	,Employees.FirstName
FROM Orders
RIGTH JOIN Employees ON 
Orders.EmployeeId = Employees.EmployeeId
ORDER BY Orders.OrderId;
~~~~

### Full Outer Join
Es una union externa completa, extrae todos los elementos de x y todos los elementos de y que tengan una coincidencia o mas.
~~~~Mysql
SELECT Customers.CustomerName
	,Orders.OrderId
FROM Customers
FULL OUTER JOIN Orders ON 
Customers.CustomerId = Orders.CustomerId
ORDER BY Customers.CustomerName;
~~~~








