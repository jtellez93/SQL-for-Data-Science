# Filtrar, ordenar y calcular datos con SQL

## Filtrar
Cuando filtramos nuestros datos, reducimos la cantidad de registros que recuperamos. En lugar de simplemente tomar una tabla completa y extraer cada columna y fila de ella, podemos ser realmente específicos sobre los datos que queremos obtener de esa tabla. Y posteriormente, eso reduce la cantidad de datos que extraemos del sistema.

~~~~Mysql
SELECT column_name, column_name
FROM  table_name
WHERE column_name operator value;
~~~~

| Operator   | Description      |
| ---------- | ---------------- |
| =          | Igual            |
| <>, !=     | Diferente        |
| >          | Mayor            |
| <          | Menor            |
| >=         | Mayor o igual    |
| <=         | Menor o igual    |
| BETWEEN    | Entre un rango   |
| IS NULL    | Es un valor nulo |

Cuando estamos filtrando y el `value` es tipo caracter debe ir entre comillas simples `'value'`, cuando hacemos filtro en un rango debe ir unido con `AND`

~~~~Mysql
SELECT column_name, column_name
FROM  table_name
WHERE column_name operator number;

SELECT column_name, column_name
FROM  table_name
WHERE column_name operator 'text';

SELECT column_name, column_name
FROM  table_name
WHERE column_name BETWEEN number AND number;
~~~~


































