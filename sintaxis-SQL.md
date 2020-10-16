## Recuperar datos
Para recuperar datos de una tabla uso la instruccion `SELECT` y posteriormente con `FROM` le indico de que tabla debe leer los datos.

~~~~Mysql
SELECT columna1, columna2, ..., FROM tabla1;
~~~~

si deseo todas las columnas de una tabla uso (*)

~~~~Mysql
SELECT * FROM tabla1;
~~~~


## Limitar datos
Para limitar los datos a recuperar se usa la instruccion `LIMIT`.

~~~~Mysql
SELECT columnas que deseo ver
FROM tabla especifica
LIMIT numero de registros

SELECT * FROM table1 LIMIT 10; # Esta instruccion recuperara todas las columnas de la tabla1, solo mostrara 10 registros
~~~~

## Crear tablas
Para crear tablas se usa la instruccion `CREATE TABLE`.

~~~~Mysql
CREATE TABLE tabla1
(
columna1    tipo de dato  Primary key,
columna2    tipo de dato  null,
columna3    tipo de dato  not null
);
~~~~

en la creacion de la tabla se definen las columnas, el tipo de datos (char, decimal, varchar...), tambien se puede definir si permite valores nulos o no.


## Insertar datos en una tabla
Para insertar datos se usa el comando `INSERT INTO` luego se especifica la tabla y los valores con el comando `VALUES`.

~~~~Mysql
INSERT INTO tabla1 VALUES('valor.columna1',NULL,'valor.columna3');
~~~~

de esta forma se ingresan los valores a la tabla, justo en el orden delcomando VALUES, otra forma es especificando el orden antes de VALUES.

~~~~Mysql
INSERT INTO tabla1 (columna1, columna2, columna3) VALUES('valor.columna1',NULL,'valor.columna3');
~~~~

## Crear tablas temporales
las tablas temporales se eliminan una vez termine la sesion del ususario, es por eso que son tablas temporales.
Para crear tablas temporales se usa el comando `CREATE TEMPORARY TABLE`.

~~~~Mysql
CREATE TEMPORARY TABLE tabla.temp AS (
SELECT *
FROM tabla1
WHERE columna1 = condicion
);
~~~~



