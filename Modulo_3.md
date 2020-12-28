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
FROM suppliers
CROSS JOIN products;
~~~~

























