---
layout: post
title:  "Apuntes: Laravel Fullstack"
date:   2022-05-21 1:26:00 -0500
---

He aprendido Laravel en trabajos como programador que he tenido.

## Contenido

* [Trabajar en Laragon con proyectos de Laravel](#trabajar-en-laragon-con-proyectos-de-laravel)

* [Añadir un proyecto a los *sites-enabled* de Laragon y a los *hosts* de Windows](#añadir-un-proyecto-a-los-sites-enabled-de-laragon-y-a-los-hosts-de-windows)

* [Comandos php artisan que uso con frecuencia](#comandos-php-artisan-que-uso-con-frecuencia)



<br>
<hr>
<br>



## Trabajar en Laragon con proyectos de Laravel

En un trabajo que tuve me pidieron clonar un repositorio para agregarle 3 CRUD lo único que me dijeron fue *hazlo con Laragon y composer*. 

Sabiendo nada de laravel y laragon y después de mucho buscar encontre esta forma de clonar y *levantar* el proyecto de Laravel.

## Descargar e instalar Laragon

Ir a [laragon](https://laragon.org/){:target="_blank"} y en la [sección de descargas](https://laragon.org/download/){:target="_blank"} escoger la versión *full*.

## Clonar un repositorio de un proyecto de Laravel

Abrir una terminal de Laragon y posicionarla en la carpeta `www` de la instalacion de Laragon, después ejecutar

```
git clone url_del_proyecto

cd la_carpeta_del_proyecto_clonado
```

## *Levantar* el sitio

Abrir una terminal **en la raíz del proyecto clonado**.

```
composer install

npm install
```

En Laragon dar click en el boton *Database* y después crear una base de datos (ej. *basedatos1*).

Crear un archivo `.env` a partir del archivo `.env.example` que se encuentra en la raíz de la carpeta del proyecto clonado. Dejar `.env` en el mismo directorio que `.env.example`.

Abrir el archivo `.env`  y agregar la base de datos que se creo anteriormente.

```
archivo: .env

DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=basedatos1  <----- agregar aqui en nombre de la base de datos
DB_USERNAME=root        <----- valor por defecto de Laragon
DB_PASSWORD=            <----- valor por defecto de Laragon
```

Con la terminal (que sigue posicionada en la carpeta raíz del proyecto) hacer:

Generar una *key*

```
php artisan key:generate
```

Realizar las migraciones

```
php artisan migrate
```

Llenar la base de datos con registros de prueba usando el *seeder*. Si no pasa nada es porque el seeder esta vacío

```
php artisan db:seed
```

Construir los *styles* y *scripts*. 

```
npm run <orden>
```

Las ordenes a ejecutar se encuentran en el archivo `package.json` que esta en la raiz de la carpeta del proyecto.

Se deben ejecutar las ordenes tipo `npm run development`.

A continuación se muestra un ejemplo:
```
archivo: package.json

"scripts": {
        "dev": "npm run development",  <---------------- EJECUTAR ESTO EN TERMINAL

        "development": "cross-env NODE_ENV=development node_modules/webpack/bin/webpack.js --progress --hide-modules --config=node_modules/laravel-mix/setup/webpack.config.js",
        
        "watch": "npm run development -- --watch", <---------------- EJECUTAR ESTO EN TERMINAL
        
        "watch-poll": "npm run watch -- --watch-poll", <---------------- EJECUTAR ESTO EN TERMINAL
        
        "hot": "cross-env NODE_ENV=development node_modules/webpack-dev-server/bin/webpack-dev-server.js --inline --hot --disable-host-check --config=node_modules/laravel-mix/setup/webpack.config.js",
        
        "prod": "npm run production", <---------------- EJECUTAR ESTO EN TERMINAL
        
        "production": "cross-env NODE_ENV=production node_modules/webpack/bin/webpack.js --no-progress --hide-modules --config=node_modules/laravel-mix/setup/webpack.config.js"
    },
```

En la ventana de laragon o su icono en la barra de tareas dar click derecho apache->ssl->habilitado.

Abrir un explorador como firefox e introducir la ruta `nombre_del_proyecto.test` 

donde: 

nombre_del_proyecto es el nombre de la carpeta resultante de las instrucciones.

```
git clone url_del_proyecto

cd la_carpeta_del_proyecto_clonado
```
**Si no muestra el sitio se puede intentar añadir el proyecto a los *sites-enabled* de Laragon y a los *hosts* de Windows.**



<br>
<hr>
<br>



## Añadir un proyecto a los *sites-enabled* de Laragon y a los *hosts* de Windows

**Nota:** Si el proyecto esta dentro de varias carpetas ejemplo: `proyecto/proyectoMaster/codigo/CRUDLaravel` se aconseja dar click derecho sobre laragon->preferencias y desactivar la opción *Crear automáticamente hosts virtuales* para que Laragon no sobreescriba y destruya lo cambios que se muestran a continuación.

Desactivar *Crear automáticamente hosts virtuales* tiene el inconveniente de agregar manualmente todos los proyectos futuros a los *sites-enabled* de Laragon y a los *hosts* de Windows.

## *Sites-enabled* de Laragon

Ir a la carpeta laragon->etc->apache2->sites-enabled La carpeta laragon se crea al instalar Laragon.

Crear un archivo auto.nombre_del_proyecto.test (ejemplo auto.CRUDLaravel.test) que tenga lo siguiente.

```
define ROOT "C:\laragon\www\CRUDLaravel\public"
define SITE "CRUDLaravel.test"

<VirtualHost *:80> 
    DocumentRoot "${ROOT}"
    ServerName ${SITE}
    ServerAlias *.${SITE}
    <Directory "${ROOT}">
        AllowOverride All
        Require all granted
    </Directory>
</VirtualHost>

<VirtualHost *:443>
    DocumentRoot "${ROOT}"
    ServerName ${SITE}
    ServerAlias *.${SITE}
    <Directory "${ROOT}">
        AllowOverride All
        Require all granted
    </Directory>

    SSLEngine on
    SSLCertificateFile      C:/laragon/etc/ssl/laragon.crt
    SSLCertificateKeyFile   C:/laragon/etc/ssl/laragon.key
 
</VirtualHost>
```

Sustituir `define ROOT "C:\laragon\www\CRUDLaravel\public"` por la ruta a la carpeta *public* del proyecto.

Sustituir `define SITE "CRUDLaravel.test"` por la carpeta del nombre del proyecto, este nombre se debe introducir como ruta al navegador

## *Hosts* de Windows

Para agregar el proyecto a los *Hosts* de windows ir a `C:\Windows\System32\drivers\etc` y abrir el archivo `hosts` (Si no existe el archivo crearlo. El archivo no tiene extención) después agregar la siguiente linea y guardar (necesita permisos de administrador).

```
127.0.0.1      CRUDLaravel.test #laragon magic!   
```

Sustituir `CRUDLaravel.test` por lo que hay en `define SITE` del paso anterior (`define SITE "CRUDLaravel.test"`).

Recargar Laragon (o cerrarlo y abrirlo), abrir el navegador e introducir la ruta *tal cual* se puso (ej. CRUDLaravel.test), respetando mayusculas, minúsculas y/o guiones. Puede tardar en reconocer y mostrar el sitio.

**Fuente** 

[forum.laragon.org/topic/175 &mdash; *Tutorial how to work with Laravel projects on Github* (parece que ahora el sitio pide logearse 👎)](https://forum.laragon.org/topic/175/tutorial-how-to-work-with-laravel-projects-on-github){:target="_blank"}



<br>
<hr>
<br>



## Comandos php artisan que uso con frecuencia


```
php artisan migrate:fresh --seed
```

Destruye las tablas, migra de nuevo y corre el seeder con el factory si aplica.

<br>
<br>

```
php artisan make:migration create_users_table
```
Crea una nueva migración.

<br>
<br>

```
php artisan make:model Flight --migration
```

Crea un modelo y su migración. El nombre de la tabla en la migración saldrá en plural (Flight -> Flights).

<br>
<br>

```
php artisan make:factory CategoriaFactory --model=Categoria
```

Crea un factory relacionado a un modelo.

**Fuente:** [youtube.com &mdash; *Laravel 5.8 - Factorías y Faker [Tutorial en Español 2019]*](https://www.youtube.com/watch?v=8-16tFIj88M)

<br>
<br>

```
php artisan make:middleware CheckAge
```

Crea un middleware.

**Fuente:** [laravel.com/docs/7.x/middleware &mdash; *Middleware*](https://laravel.com/docs/7.x/middleware)

<br>
<br>

```
php artisan make:migration add_name_to_costs_table --table=costs
```

Crea una migración que modificará una tabla para cambiar o agregar columnas.

**Fuente:** [stackoverflow.com/questions/16791613/ &mdash; *Laravel Add a new column to existing table in a migration*](https://stackoverflow.com/questions/16791613/laravel-add-a-new-column-to-existing-table-in-a-migration)