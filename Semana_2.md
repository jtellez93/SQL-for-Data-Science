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
WHERE column_name operator 'text';

SELECT column_name, column_name
FROM  table_name
WHERE column_name BETWEEN value AND value;
~~~~

### Operador IN
Este operador se usa cuando queremos asignar varias condiciones a la vez (Intersecciones entre conjuntos), estas condiciones deben ir entre parentesis y separadas por `,`.

~~~~Mysql
SELECT column_name, column_name
FROM  table_name
WHERE column_name IN (value, value, value);
~~~~

### Operador OR
Este operador se usa cuando queremos asignar varias condiciones a la vez (Uniones entre conjuntos), no evalua la segunda condicion si se cumple la primera. Este operador tambien se puede usar con `AND`.

~~~~Mysql
SELECT column_name, column_name
FROM  table_name
WHERE column_name operator value OR value;

SELECT column_name, column_name
FROM  table_name
WHERE (column_name operator value OR
column_name operator value)
AND column_name operator value;
~~~~
Es importante hacer uso de los parentesis para asegurarnos de obtener los valores que necesitamos.

### Operador NOT
Este operador es una forma de excluir diferentes opciones.
~~~~Mysql
SELECT column_name, column_name
FROM  table_name
WHERE NOT column_name operator value 
AND NOT column_name operator value;
~~~~

### Usando % Wildcards
Este operador o prefijo se usa cuando queremos extraer registros que contienen una cadena de texto en especial.

| Wildcard             | Action                                                        |
| -------------------- | ------------------------------------------------------------- |
| '%Pizza' o '\_Pizza' | Toma todo lo que termmine con la palabra Pizza                |
| 'Pizza%'             | Toma todo lo que empiece con la palabra Pizza                 |
| '%Pizza%'            | Toma todo lo que tenga antes y después la palabra pizza       |
| 'S%E'                | Toma todas las palabras que inicien con S y terminen con E    |
| 't%@gmail.com'       | Toma todos los correos que inicien con t                      |


## Ordenar

Para ordenar los datos usamos la clausula `ORDER BY` la cual nos permite ordenarlos de forma ascendente `ASC` o descendente `DESC`, tambien nos permite ordenar por una columna o por varias columnas, `ORDER BY` siempre debe ser la ultima clausula en la instruccion `SELECT`
~~~~Mysql
SELECT column_name, column_name
FROM  table_name
ORDER BY column_name;

SELECT column_name, column_name
FROM  table_name
ORDER BY column_name, column_name, column_name;

SELECT column_name, column_name
FROM  table_name
ORDER BY column_name ASC, column_name ASC, column_name DESC;
~~~~

## Operadores matematicos

| Operador     | Acción         |
| ------------ | -------------- |
| +            | Suma           |
| -            | Resta          |
| *            | Multiplicación |
| /            | División       |

Estos operadores permiten ejecutar operaciones entre columnas, esta operacion se muestra en una columna nueva, el comando `AS` asigna el nombre a esta nueva columna.
~~~~Mysql
SELECT column_name_1
,column_name_2
,column_name_1 * column_name_2 AS column_name_Total
FROM  table_name;
~~~~
Puedo usar varios operadores en la misma consulta, estos se ejecutan en el siguiente orden:
1. Parentesis `()`.
2. Exponentes.
3. Multiplicacion `*`.
4. Division `/`.
5. Suma `+`.
6. Resta `-`.

~~~~Mysql
SELECT column_name_1
,column_name_2
,column_name_3
,(column_name_1 - column_name_2)/column_name_3 AS column_name_Total
FROM  table_name;
~~~~


























