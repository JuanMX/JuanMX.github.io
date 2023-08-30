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

* [La extención de navegador Fake Filler para llenar formularios](#la-extención-de-navegador-fake-filler-para-llenar-formularios)

* [En un div hacer que cambie el cursor por una mano al posicionarlo encima](#en-un-div-hacer-que-cambie-el-cursor-por-una-mano-al-posicionarlo-encima)

* [Usar el helper str de Laravel en un Blade](#usar-el-helper-str-de-laravel-en-un-blade)

* [Laravel Debugbar se adjunta a lo que responde el Controlador](#laravel-debugbar-se-adjunta-a-lo-que-responde-el-controlador)



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

Abrir un explorador como Firefox e introducir la ruta `nombre_del_proyecto.test` 

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

**Fuente:** [youtube.com &mdash; *Laravel 5.8 - Factorías y Faker [Tutorial en Español 2019]*](https://www.youtube.com/watch?v=8-16tFIj88M){:target="_blank"}

<br>
<br>

```
php artisan make:middleware CheckAge
```

Crea un middleware.

**Fuente:** [laravel.com/docs/7.x/middleware &mdash; *Middleware*](https://laravel.com/docs/7.x/middleware){:target="_blank"}

<br>
<br>

```
php artisan make:migration add_name_to_costs_table --table=costs
```

Crea una migración que modificará una tabla para cambiar o agregar columnas.

**Fuente:** [stackoverflow.com/questions/16791613/ &mdash; *Laravel Add a new column to existing table in a migration*](https://stackoverflow.com/questions/16791613/laravel-add-a-new-column-to-existing-table-in-a-migration){:target="_blank"}



<br>
<hr>
<br>



## La extención de navegador Fake Filler para llenar formularios
*24 / Julio / 2022 | 0:19:00*

![fakefillerlogo](https://raw.githubusercontent.com/FakeFiller/fake-filler-extension/ff732ecc70776f938d15ba9716bc5b39f64bb98c/public/images/logo.svg)


En un trabajo que tuve me pedian hacer cambios a sistemas hechos en Laravel. En ocasiones eran muchos formularios con muchos campos a llenar.

Después de buscar en la sección de complementos de Firefox como llenar más rápido los formularios me encontré esta extención para el navegador.

## Fake Filler para Firefox

Esta extención se encuentra [aqui](https://addons.mozilla.org/es/firefox/addon/fake-filler/){:target="_blank"}


![fakefillerfirefox]({{ "../assets/apuntes-laravel-fullstack/fake_filler_firefox.png" | absolute_url }})

Se debe agregar al navegador como cualquier otra extención.

Y eso es todo.

El único cambio que yo hice fue modificar como llenar un campo de formulario de tipo *Date*.

## Modificar en Fake Filler el formato Date   


Ir a la sección complementos de Firefox.

![fakefillerfirefox]({{ "../assets/apuntes-laravel-fullstack/1_firefox_Complementos.png" | absolute_url }})


En los complementos buscar Fake Filler y dar click en *Preferencias*.

![fakefillerfirefox]({{ "../assets/apuntes-laravel-fullstack/2_fakefiller_preferencias.png" | absolute_url }})

En las preferencias de Fake Filler ir a *Custom Fields*, buscar el campo *Date* y dar click en editar.

![fakefillerfirefox]({{ "../assets/apuntes-laravel-fullstack/3_fakefiller_date.png" | absolute_url }})

En la sección *Template* sustituir su contenido por `DD/MM/YYYY` y guardar los cambios.

![fakefillerfirefox]({{ "../assets/apuntes-laravel-fullstack/4_fakefiller_date_editar.png" | absolute_url }})



<style>
    .hover-hand:hover{
        cursor:pointer;
    }
</style>
<div class="hover-hand">
<br>
<hr>
<br>



<h2 id="en-un-div-hacer-que-cambie-el-cursor-por-una-mano-al-posicionarlo-encima"> En un div hacer que cambie el cursor por una mano al posicionarlo encima </h2>


<p>
    Para hacer que en un blade de Laravel el mouse cambie por una mano al hacer un <i>hover</i> sobre un elemento encerrado en un <code>&lt;div&gt;&lt;/div&gt;</code> se puede hacer lo siguiente. 
</p>

<script src="https://gist.github.com/JuanMX/6f34a6be36f31ecdbf4aa90c2fc25ea1.js"></script>



<br>
<hr>
<br>
</div>



## Usar el helper str de Laravel en un Blade

Para hacer rápido una tarea que me pedían usé el helper `str upper` de Laravel directamente en un blade.

A continuación se muestra un ejemplo de como hacerlo.

<script src="https://gist.github.com/JuanMX/cbb3b1aa0e3b1caf9d18ea25e8942f89.js"></script>



<br>
<hr>
<br>



## Laravel Debugbar se adjunta a lo que responde el Controlador

[Debugbar for Laravel]{:target="_blank"} es una herramienta muy útil y usada para el desarrollo. Lo que hace es poner información relevante de vistas, peticiones, consultas a base de datos, entre otros, como en la siguiente imagen:

![debugbar](https://user-images.githubusercontent.com/973269/79428890-196cc680-7fc7-11ea-8229-189f5eac9009.png)

## Descripción de un problema que tuve con Laravel Debugbar

En un trabajo que tuve estaba usando el API de WhatsApp en un proyecto de Laravel.

Para la parte del webhook que usé para recibir mensajes de respuesta tuve un problema al abrir la conexión.

Los pasos para abrir la conexión eran:

1. Dar de alta un token para el webhook en WhatsApp.
2. Guardar el token en local, yo usé el `.env`.
3. Hacer una ruta para verificar que el token en local y de WhatsApp coincidan. Si coinciden retornar un valor `hub_challenge` para que WhatsApp abra la conexión y empiecen a llegar mensajes al proyecto en Laravel.

## El problema en sí

No se abría la conexión porque el HTML del Laravel Debugbar se adjuntaba a la respuesta del controlador. Provocando que se mande valor `hub_challenge` con más información no necesaria.

Revisando en el panel de control de WhatsApp API noté que en el webhook decía algo como:

```
Se espera un valor de hub challenge de: 1234567

Pero se recibió: 1234567<html><body> ESTE HTML ES DEL LARAVEL DEBUGBAR </body></html>
```

A veces lo cambiaba por:

```
Se espera un valor de hub challenge de: 1234567

Pero se recibió: 1234567"/ux7...."
```

Donde `"/ux7...."` hace referencia al caracter `<` pero codificado como UTF-8 o algún otro.

## Solución 

Según [Debugbar for Laravel]{:target="_blank"} es posible desactivarlo en tiempo de ejecución. Yo lo usé en mi controlador donde se abre la conexión.

```
\Debugbar::disable();
```

## Código de ejemplo

Es un código de ejemplo muy tosco. No recomiendo usarlo tal cual está pero ejemplifica la solución a mi problena de inicio. 

```php
/*=======  WhatsAppController.php =======*/
    
public function verifyWebhook(Request $request)
{
    /*==================================================
    //Primero que todo, en esta sección
    //De acuerdo con la documentación de WhatsApp 
    //Se deben hacer las verificaciones correspondientes
    ==================================================*/

    \Debugbar::disable();//Se desactiva Laravel Debugbar antes de responder
    
    if($request["hub_verify_token"] == env('WHATSAPP_WEBHOOK_TOKEN')){
        
        return response($request["hub_challenge"]);//Se hace el response a WhatsApp
    }
}
```

**Fuente:** [github.com/barryvdh/laravel-debugbar &mdash; *Enabling/Disabling on run time*](https://github.com/barryvdh/laravel-debugbar#enablingdisabling-on-run-time){:target="_blank"}


[Debugbar for Laravel]: https://github.com/barryvdh/laravel-debugbar