---
layout: post
title:  "Agregar un botón Back to top en HTML"
date:   2021-08-07 16:26:00 -0500
--- 

Quería saber si era posible agregar un botón Back to top a este sitio. Al poder realizarlo pero con complicaciones decidí escribir al respecto.

## Contenido

* [Back to top en HTML](#back-to-top-en-html)
* [Back to top en Jekyll](#back-to-top-en-jekyll)

## Back to top en HTML

Agregar las siguientes lineas de código en html

```html
<script src="https://unpkg.com/vanilla-back-to-top@7.2.1/dist/vanilla-back-to-top.min.js"></script>
<script>addBackToTop()</script>
```

**Fuente:** [github.com/vfeskov &mdash; Vanilla Back To Top](https://github.com/vfeskov/vanilla-back-to-top){:target="_blank"}

## Back to top en Jekyll

Los siguientes pasos son para agregar el botón back to top en los *posts* y en el *index* del proyecto. Supone que se esta usando el tema *minima*.

Si no existe, crear una carpeta llamada `_layouts` en la raíz del directorio del proyecto.

En la carpeta `_layouts` crear un archivo llamado `post.html`.

En el archivo `post.html` agregar el siguiente contenido:

<script src="https://gist.github.com/JuanMX/2e3967b10b7be8cd6cfc0da533133a8b.js"></script>

En el archivo `index.md` agregar el siguiente contenido:

```html
---
layout: home
---
<script src="https://unpkg.com/vanilla-back-to-top@7.2.1/dist/vanilla-back-to-top.min.js"></script>
<script>addBackToTop()</script>
```

Los pasos anteriores provocará que aparezca un botón circular para ir arriba en la parte inferior derecha de la pantalla cuando se realice un *scroll* hacia abajo en el sitio. El botón es ajustable al tamaño de pantalla incluyendo celulares y otros. El siguiente gif animado muestra un ejemplo del funcionamiento.

<br>
<hr>
<br>

![demobacktotop]({{ "../assets/back-to-top-html/back_to_top_3.gif" | absolute_url }})

<br>
<hr>
<br>
**Fuente:** La idea de sobreescribir el layout del post la encontré [En una pagina de github pages](https://mchirico.github.io/javascript/2016/12/22/JavascriptNetwork.html), [con su repositorio en github](https://github.com/mchirico/mchirico.github.io/blob/master/_layouts/post.html) y [en la documentación de Jekyll.](https://jekyllrb.com/docs/layouts/)

El contenido que se pone en la sobreescritura lo encontré en el [repositorio de un curso de Standford.](https://github.com/cs231n/cs231n.github.io/blob/master/_layouts/post.html)