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
| ``` \? ``` | Ver los comandos de Postgres |
| ``` \l ```  | Listar todas las bases de datos |
| ``` \dt ```  | Ver las tablas de una base de datos |
| ``` \c nombre_BD ``` | Cambiar a otra BD |
| ``` \d nombre_tabla ``` | Describir una tabla |
| ``` \h ``` | Ver todos los comandos SQL |
| ``` \h nombre_de_la_funcion ``` | Ver como se ejecuta un comando SQL |
| ``` SELECT version(); ``` | Ver la version de Postgres instalada, importante poner el ';' |
| ``` \g ``` | Volver a ejecutar la funcion ejecutada anteriormente |
| ``` \timing ``` | Iniciar temporizador para saber cuando se demora en ejecutar cada comando |





