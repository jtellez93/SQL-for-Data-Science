# Subqueries and Joins

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

## Subquery in Subquery
~~~~Mysql
SELECT costumer_name
	,costumer_contact
FROM costumers
WHERE cust_id IN

    SELECT costumer_id
    FROM orders
    WHERE order_number IN (
		    SELECT order_number
		    FROM order_items
		    WHERE prod_name = 'Toothbrush'
		    );
~~~~

Tambien es importante hacer una buena identacion del codigo, esto facilita la lectura y comprension de las subconsultas, si se toma codigo SQL de algun sistema y no esta identado el sitio [PoorSQL](https://poorsql.com/) identa de forma automatica el codigo que le suministremos.





























