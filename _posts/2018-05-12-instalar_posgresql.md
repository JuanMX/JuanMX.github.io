---
layout: post
title:  "Instalar postgreSQL"
date:   2018-05-12 22:05:00 -0500
categories: postgresql
--- 

Son mis primeros apuntes de la universidad de mi clase de bases de datos usando postgreSQL como sistema manejador de bases de datos.

Con el tiempo habrá información sobre otros sistemas manejadores.

## Contenido

* [Instalar postgreSQL crear un rol y una base de datos ](#instalar-postgresql-crear-un-rol-y-una-base-de-datos )

* [Logearse MySql en la terminal](#logearse-mysql-en-la-terminal)

## Instalar postgreSQL crear un rol y una base de datos 

Los pasos mostrados a continuación son para sistemas operativos Ubuntu y derivados.

* **Instalar postgreSQL**

```
sudo apt-get install postgresql postgresql-client postgresql-contrib libpq-dev pgadmin3
```

* **Reiniciar el servicio de postgreSQL**

```
sudo service postgresql restart
```

* **Cambiar *login* al usuario postgres**

```
sudo su - postgres
```

* **Comprobar el cambio de login**

```
id 
```

* **Comprobar psql**

```
psql --version
```

* ***login* a psql**

```
psql
```
* **Comprobar la base de datos**

```
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

```
\q
```

* **Salir del usuario postgres**

```
exit
```

* ***login* a psql como *nombre_del_propietario_de_la_base_de_datos_creada***

```
psql -h localhost -U nombre_del_propietario_de_la_base_de_datos_creada nombre_la_base_de_datos_creada
```

## Extra: cargar un *script* SQL

* **Cargar un *script* SQL con la base de datos hecha**

```
\i nombre_del_script_con_la_base_de_datos_hecha.sql;
```

* **Comprobar la ejecución del *script***

```sql
\d
SELECT * FROM nombre_de_una_tabla;
```

## Nota

Si se siguieron **todos** los pasos y se quiere salir de postgreSQL se necesita poner

```
\q
```

## Logearse MySql en la terminal

Logearse a mysql como usuario `USUARIO` y usar la base de datos `BASE_DE_DATOS`

```
mysql -u USUARIO -p BASE_DE_DATOS
```