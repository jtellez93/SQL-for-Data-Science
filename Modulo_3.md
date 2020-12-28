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

Numero total de ordenes por estado para cada cliente.
| Customer_name | Customer_state | orders |
| ------------- | -------------- | ------ |
| Becky		| IA		 | 5	  |
| Nita		| CA		 | 6	  |
| Raj		| OH		 | 0	  |
| Steve		| AZ		 | 1	  |

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





























