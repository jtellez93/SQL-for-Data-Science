# PostgreSQL
[PostgreSQL](https://es.wikipedia.org/wiki/PostgreSQL), también llamado Postgres, es un sistema de gestión de bases de datos relacional orientado a objetos y de código abierto, publicado bajo la licencia PostgreSQL, similar a la BSD o la MIT.
Como muchos otros proyectos de código abierto, el desarrollo de PostgreSQL no es manejado por una empresa o persona, sino que es dirigido por una comunidad de desarrolladores que trabajan de forma desinteresada, altruista, libre o apoyados por organizaciones comerciales. Dicha comunidad es denominada el PGDG (PostgreSQL Global Development Group).

PostgreSQL no tiene un gestor de errores (bugs), haciendo muy difícil conocer el estado de corrección de los mismos.


## instalación de postgres en ubuntu.
```console
sudo apt-get install postgresql postgresql-contrib
```

### instalación de la interfaz gráfica.
```console
sudo apt-get install pgadmin3
```
Instalacion de [pgadmin4](https://comoinstalar.me/como-instalar-pgadmin-en-ubuntu-20-04-lts/). Para acceder lo hago en la Url: http://127.0.0.1/pgadmin4

## Iniciar la base de datos
```console
sudo -u postgres psql -> Indica que se está iniciando sesión con el usuario postgres.
```

## Cambiar la contraseña del usuario postgres.
Dentro de la base de datos activa:
```console
alter user postgres with password '<contraseña>'; -> Las comillas en la contraseña son obligatorias.
```
Usuario: postgres  
Contraseña: siempre

## Funciones
| Comando | Descripcion |
| -- | -- |
| ` \? ` | Ver los comandos de Postgres |
| ` \l `  | Listar todas las bases de datos |
| ` \dt `  | Ver las tablas de una base de datos |
| ` \d nombre_tabla ` | Describir una tabla |
| ` \dn `  | Listar los esquemas de la base de datos actual |
| ` \df `  | Listar las funciones disponibles de la base de datos actual |
| ` \dv `  | Listar las vistas de la base de datos actual |
| ` \du `  | Listar los usuarios y sus roles de la base de datos actual |
| ` \c nombre_BD ` | Cambiar a otra BD |
| ` \h ` | Ver todos los comandos SQL |
| ` \h nombre_de_la_funcion ` | Ver como se ejecuta un comando SQL |
| ` SELECT version(); ` | Ver la version de Postgres instalada, importante poner el ';' |
| ` \g ` | Volver a ejecutar la funcion ejecutada anteriormente |
| ` \timing ` | Iniciar temporizador para saber cuando se demora en ejecutar cada comando |
| ` SHOW config_file; ` | Ver donde se encuentran los archivos de configuracion |

## Archivos de configuracion de postgres
- ***postgresql.conf:*** Configuración general de postgres, múltiples opciones referentes a direcciones de conexión de entrada, memoria, cantidad de hilos de pocesamiento, replica, etc.
- **pg_hba.conf:** Muestra los roles así como los tipos de acceso a la base de datos.
- **pg_ident.conf:** Permite realizar el mapeo de usuarios. Permite definir roles a usuarios del sistema operativo donde se ejecuta postgres.

## Tipos de datos
[Tipos de datos PostgreSQL](https://www.postgresql.org/docs/11/datatype.html)

## Jerarquía de Bases de Datos
Toda jerarquía de base de datos se basa en los siguientes elementos:

- **Servidor de base de datos:** Computador que tiene un motor de base de datos instalado y en ejecución.
- **Motor de base de datos:** Software que provee un conjunto de servicios encargados de administrar una base de datos.
- **Base de datos:** Grupo de datos que pertenecen a un mismo contexto.
- **Esquemas de base de datos en PostgreSQL:** Grupo de objetos de base de datos que guarda relación entre sí (tablas, funciones, relaciones, secuencias).
- **Tablas de base de datos:** Estructura que organiza los datos en filas y columnas formando una matriz.

PostgreSQL es un motor de base de datos.  

## Roles
Que puede hacer un ROLE
- Crear y Eliminar
- Asignar atributos
- Agrupar con otros roles
- Roles predeterminados

Ver las funciones del comando CREATE ROLE
```console
\h CREATE ROLE;
```

Creamos un ROLE (consultas -> lectura, insertar, actualizar)
```console
CREATE ROLE usuario_consulta;
```

Mostrar todos los usuarios junto a sus atributos
```console
\dg
```
Agregamos atributos al usuario o role
```console
ALTER ROLE  usuario_consulta WITH LOGIN;
ALTER ROLE  usuario_consulta WITH SUPERUSER;
ALTER ROLE  usuario_consulta WITH PASSWORD'1234';
```
Elimanos el usuario o role
```console
DROP ROLE usuario_consulta;
```

Crear un usuario o role por pgadmin
```console
CREATE ROLE usuario_consulta WITH
  LOGIN
  NOSUPERUSER
  NOCREATEDB
  NOCREATEROLE
  INHERIT
  NOREPLICATION
  CONNECTION LIMIT -1
  PASSWORD '1234';
```

Para otorgar privilegios a nuestro usuario_consulta

```console
GRANT INSERT, SELECT, UPDATE ON TABLE public.tabla TO usuario_consulta;
```

## Inserción masiva de datos
[Mockaroo](https://www.mockaroo.com/) genera datos aleatorios para probar la base que se este trabajando.

