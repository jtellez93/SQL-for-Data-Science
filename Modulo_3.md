# Subqueries and Joins

Son consultas incrustadas en otras consultas (una consulta dentro de otra consulta) son utiles cuando se requiere informacion de varias tablas.

~~~~Mysql
SELECT column_name_1
,column_name_2
,column_name_3
FROM  table_name_1
WHERE column_name_1 in (SELECT column_name_1
    FROM table_name_2
    WHERE column_name operator value);
~~~~
