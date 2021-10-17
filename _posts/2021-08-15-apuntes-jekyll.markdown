---
layout: post
title:  "Apuntes: Jekyll"
date:   2021-08-15 12:26:00 -0500
---  

Gracias a conocimientos de desarrollo fullstack adquiridos de un trabajo que tuve, quería saber que podía cambiar en mi blog. A continuación se muestra los cambios *técnicos* que he hecho junto con *tips y trucos*. Supone que se esta usando el tema de Jekyll **minima** y el sistema operativo Ubuntu.

**Contenido**

* [Recomendaciones al instalar y ejecutar Jekyll](#recomendaciones-al-instalar-y-ejecutar-jekyll)

* [Obtener y sobreescribir las plantillas del tema por defecto](#obtener-y-sobreescribir-las-plantillas-del-tema-por-defecto)

* [Feed en Jekyll](#feed-en-jekyll)

* [Crear links en markdown que abran en un nuevo tab](#crear-links-en-markdown-que-abran-en-un-nuevo-tab)

* [Actualizar la dependencia Nokogiri](#actualizar-la-dependencia-nokogiri)


<br>
<hr>
<br>

## Recomendaciones al instalar y ejecutar Jekyll

1. Revisar la sección docs -> [quickstart](https://jekyllrb.com/docs/) y seguir los pasos que se indican junto con sus [prerrequisitos](https://jekyllrb.com/docs/installation/).

2. Al ejecutar Jekyll para desarrollo añadir el *flag* `--livereload`

```
bundle exec jekyll serve --livereload
```

**Fuente:** [Documentación oficial de Jekyll](https://jekyllrb.com/docs/)

<br>
<hr>
<br>

## Obtener y sobreescribir las plantillas del tema por defecto

A continuación se muestran los pasos para obtener los archivos del tema minima de Jekyll

### Obtener los archivos del tema minima de Jekyll

Ejecutar en la terminal el siguiente comando.

```
bundle info --path minima
```

En mi caso, me regresó el siguiente mensaje.

```
The dependency tzinfo-data (>= 0) will be unused by any of the platforms Bundler is installing for. Bundler is installing for ruby but the dependency is only for x86-mingw32, x86-mswin32, x64-mingw32, java. To add those platforms to the bundle, run `bundle lock --add-platform x86-mingw32 x86-mswin32 x64-mingw32 java`.
/home/juan/gems/gems/minima-2.5.1
```

Siguiendo el mensaje, ejecuté el comando

```
bundle lock --add-platform x86-mingw32 x86-mswin32 x64-mingw32 java
```

Y nuevamente usar

```
bundle info --path minima
```

La instrucción anterior retornará la ruta en donde están los archivos del tema minima. En mi caso regresó: `/home/juan/gems/gems/minima-2.5.1`

Así se obtienen los archivos del tema minima, a continuación se muestra un ejemplo de como sobreesrcribir (*Override*) el layout `post` para agregar un botón de Ir arriba (*Back to top*).

### Sobreescribir el layout posts para agregar un botón de Ir arriba

Si no existe, crear una carpeta llamada `_layouts` en la raíz del directorio del proyecto de Jekyll.

En la carpeta `_layouts` creada, copiar el archivo `post.html` que está en los archivos por defecto del tema minima de Jekyll.

![copiarposts]({{ "../assets/apuntes-jekyll/sobreescribir_posts.png" | absolute_url }})

En el archivo `post.html` agregar el siguiente contenido:

<script src="https://gist.github.com/JuanMX/2e3967b10b7be8cd6cfc0da533133a8b.js"></script>

[Hay otra entrada en este blog sobre el tema]({% post_url 2021-08-07-agregar-un-boton-back-to-top-en-html %})

**Fuente:** [Documentación oficial de Jekyll](https://jekyllrb.com/docs/themes/#overriding-theme-defaults)

<br>
<hr>
<br>

## Feed en Jekyll

Un *feed* sirve para proporcionar actualizaciones del blog. Se muestra como trabajarlo de manera manual, aunque hay [plugins](https://github.com/jekyll/jekyll-feed) para hacerlo.

### Sobreescribir el home del proyecto

Con los pasos del apartado anterior copiar el archivo `home.html` de la carpeta `_layouts` del tema minima de Jekyll a la carpeta `_layouts` del proyecto.

![copiarposts]({{ "../assets/apuntes-jekyll/sobreescribir_home.png" | absolute_url }})

Abrir el archivo `home.html` y encontrar la siguiente linea de código

```
<p class="rss-subscribe">subscribe <a href="{{ "/feed.xml" | relative_url }}">via RSS</a></p>
```

Aquí hay **dos opciones**, se puede **eliminar** esa linea para que en el home del sitio, cuando se encuentre en producción no aparecerá el texto *subscribe via RSS*. También se puede dejar como esta y **crear un archivo** llamado `feed.xml` en la carpeta raíz del proyecto, el contenido del archivo se muestra a continuación.

### Contenido del archivo feed.xml

Antes de escribir en el archivo `xml` verifique que en el archivo `_config.yml` tenga valores asignados en `url`, `title`, `description` y `author`. Además de que en los archivos markdown de los posts tenga un valor en `date`.

```
======= Fragmento de mi archivo _config.yml =======
.
.
.

title: Mi cuaderno de apuntes
author: Juan
description: >- # this means to ignore newlines until "baseurl:"
  Apuntes sobre programación y software
baseurl: "" # the subpath of your site, e.g. /blog
url: "https://juanmx.github.io/" # the base hostname & protocol for your site, e.g. http://example.com

.
.
.
```

```
======= Ejemplo de date (fecha) en un post (entrada de blog) =======

---
layout: post
title:  "Apuntes: Jekyll"
date:   2021-08-15 12:26:00 -0500
---

```

En el archivo llamado `feed.xml` ubicado en la raíz del proyecto agregar el siguiente contenido.

<script src="https://gist.github.com/JuanMX/fafecf0f26ec0cee8e1055092cdf342c.js"></script>

Y ya se podrá suscribirse via RSS al blog. Para hacerlo se necesita la url al archivo `feed.xml`, en mi caso es `https://juanmx.github.io/feed.xml` y un software que permita suscripciones a sitios web por medio de RSS. Hay muchas opciones en PC, personalmente uso [Mozilla Thunderbird](https://www.thunderbird.net).


**Fuente:** [youtube.com &mdash; *Up and Running with GitHub Pages, Part 6, Multiple Jekyll Blogs and Feeds*](https://www.youtube.com/watch?v=iIBkOWY5aAA)

<br>
<hr>
<br>

## Crear links en markdown que abran en un nuevo tab

Para hacer que en un proyecto de Jekyll, un link de markdown se abra en un nuevo tab (pestaña) se puede hacer lo siguiente.

**Opción 1**. Usar HTML.

```html
<a href="https://github.com/JuanMX" target="_blank">Link a mi perfil de GitHub</a>
```


Resultado: <a href="https://github.com/JuanMX" target="_blank">Link a mi perfil de GitHub</a>

**Opción 2**. Como Jekyll usa Kramdown se puede usar el *helper*/instrucción `{:target="_blank"}`.

```
[Link a mi perfil de GitHub](https://github.com/JuanMX){:target="_blank"}
```

Resultado: [Link a mi perfil de GitHub](https://github.com/JuanMX){:target="_blank"}

Personalmente, si en una computadora quiero abrir un link en una nueva pestaña uso el scroll del mouse. El scroll es la rueda del ratón, se muestra en la siguiente imagen en un circulo rojo.

<img src="https://freesvg.org/img/1543784161.png" width="250" height="250" />

Dar click en un link con el scroll del mouse lo abrirá en una nueva pestaña.

**Fuente:** [stackoverflow.com/questions &mdash; *Can I create links with 'target="_blank"' in Markdown?*](https://stackoverflow.com/questions/4425198/can-i-create-links-with-target-blank-in-markdown){:target="_blank"}


<br>
<hr>
<br>

## Actualizar la dependencia Nokogiri

Cuado hay vulnerabilidades en las dependencias del proyecto de Jekyll en GitHub Pages se notifica en el repositorio de GitHub. En mi caso me notificó sobre la dependencia Nokogiri.

![avisonokogiri]({{ "../assets/apuntes-jekyll/aviso_nokogiri.png" | absolute_url }})

Pero no deja muy clara la manera de actualizar la dependencia. Después de buscar encontré la siguiente solución.

Abrir la **terminal** y posicionarla en la **raíz** del **proyecto** de Jekyll (el proyecto en local) y **ejecutar** lo siguiente.

```
bundle update nokogiri
```

Lo anterior modificará el archivo `Gemfile.lock`, se le debe hacer un *commit* y *push* al repositorio en GitHub. El problema debería estar resuelto.

Lo anterior probablemente sirva para actualizar otras dependencias, por ejemplo, `Kramdown` pero no lo he probado.

**Fuente:** [ajahne.github.io &mdash; *Update Jekyll and Ruby on macOS*](https://ajahne.github.io/blog/tools/2020/10/22/update-jekyll-ruby-gems.html){:target="_blank"}