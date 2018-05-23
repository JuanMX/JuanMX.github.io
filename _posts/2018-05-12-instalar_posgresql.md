---
layout: post
title:  "Instalar postgreSQL"
date:   2018-05-12 22:05:00 -0500
categories: postgresql
--- 

## Instalar postgreSQL, crear un *rol* y una base de datos 

Los pasos mostrados a continuación son para sistemas operativos Ubuntu y derivados.

* **Instalar postgreSQL**

```bash
sudo apt-get install postgresql postgresql-client postgresql-contrib libpq-dev pgadmin3
```

* **Reiniciar el servicio de postgreSQL**

```bash
sudo service postgresql restart
```

* **Cambiar *login* al usuario postgres**

```bash
sudo su - postgres
```

* **Comprobar el cambio de login**

```bash
id 
```

* **Comprobar psql**

```bash
psql --version
```

* ***login* a psql**

```bash
psql
```
* **Comprobar la base de datos**

```sql
\l
```

* **Crear un *rol* dueño de la base de datos *nombre_del_propietario_de_la_base_de_datos_a_crear***

```sql
CREATE ROLE nombre_del_propietario_de_la_base_de_datos_a_crear WITH LOGIN PASSWORD 'contraseña_del_dueño_de_la_base_de_datos';
```

* **Crear la base de datos *nombre_la_base_de_datos_a_crear***

```sql
CREATE DATABASE nombre_la_base_de_datos_a_crear OWNER nombre_del_propietario_de_la_base_de_datos_a_crear;
```

* **salir**

```sql
\q
```

* **Salir del usuario postgres**

```bash
exit
```

* ***login* a psql como *nombre_del_propietario_de_la_base_de_datos_creada***

```bash
psql -h localhost -U nombre_del_propietario_de_la_base_de_datos_creada nombre_la_base_de_datos_creada
```

## Extra: cargar un *script* SQL

* **Cargar un *script* SQL con la base de datos hecha**

```sql
\i nombre_del_script_con_la_base_de_datos_hecha.sql;
```

* **Comprobar la ejecución del *script***

```sql
\d
SELECT * FROM nombre_una_tabla;
```

## Nota

Si se siguieron **todos** los pasos y quieres salir de postgreSQL se necesita poner

```sql
\q
```

**Fuente y contexto**

Son los primeros apuntes de mi clase de bases de datos usando postgreSQL como sistema manejador de bases de datos y por lo tanto no hay *link* disponible.
