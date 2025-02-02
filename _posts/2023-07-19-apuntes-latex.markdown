---
layout: post
title:  "Apuntes: LaTeX"
date:   2023-07-19 17:00:00 -0500
categories: latex beamer
---

Estaba revisando un viejo disco duro que tenía por ahí y me encontré con documentos de todo lo que hice en la universidad referente a LaTeX, es decir, mi tesis, diapositivas y un póster científico.

Al revisar los documentos noté que aprendí algunos trucos sobre LaTeX y eso me motivó a hacer esta entrada de blog.

Probablemente este post contiene conocimiento obsoleto pero no me importa.

## Contenido

* [Instalar texlive-full en Kubuntu 22.04](#instalar-texlive-full-en-kubuntu-2204)

* [Obtener el pdf a partir de un archivo tex](#obtener-el-pdf-a-partir-de-un-archivo-tex)

* [Los controles de navegación de una presentación no coinciden con su número de páginas](#los-controles-de-navegación-de-una-presentación-no-coinciden-con-su-número-de-páginas)

* [Mi recomendación de plantilla para una presentación en beamer](#mi-recomendación-de-plantilla-para-una-presentación-en-beamer)

* [Al usar pdflatex no aparece la bibiografía](#al-usar-pdflatex-no-aparece-la-bibiografía)

* [Mi recomendación de plantilla para un póster científico en LaTeX](#mi-recomendación-de-plantilla-para-un-póster-científico-en-latex)

* [Loren Ipsum](#loren-ipsum)

* [Fusionar varios pdf en uno solo](#fusionar-varios-pdf-en-uno-solo)



<br>
<hr>
<br>




## Instalar texlive-full en Kubuntu 22.04

Recomiento ampliamente instalar LaTeX full para evitar problemas a futuro de que falten paquetes. El problema es que dicha instalación necesita mucho tiempo y espacio en el disco.

Para instalar LaTeX full abrir una terminal y escribir lo siguiente:

```
sudo apt install texlive-full
```
En mi caso me mostró el siguiente mensaje:

```
Se necesita descargar 3 494 MB de archivos.

Se utilizarán 6 392 MB de espacio de disco adicional después de esta operación.

¿Desea continuar? [S/n] _
```

Se debe presionar la "S" en el teclado para iniciar la instalación.

**Fuente:** [linuxconfig.org &mdash; *How to install LaTex on Ubuntu 18.04 Bionic Beaver Linux*](https://linuxconfig.org/how-to-install-latex-on-ubuntu-18-04-bionic-beaver-linux){:target="_blank"}



<br>
<hr>
<br>



## Obtener el pdf a partir de un archivo tex

Para obtener el `.pdf` del `.tex` abrir una terminal donde está el `.tex` y escribir:

```
pdflatex nombre_del_archivo.tex
```



<br>
<hr>
<br>



## Los controles de navegación de una presentación no coinciden con su número de páginas

En una presentación en ***beamer*** hay veces que no coinciden los controles de navegación con el contenido del documento. 

Los controles de navegación son donde se da click para moverse rápidamente a un tema, subtema o diapositiva.

![img]({{ "../assets/apuntes-latex/controles-navegacion.png" | absolute_url }})

La manera que yo uso para sincronizar el número de diapositivas con los controles de navegación es: **Compilar dos veces**.

Primero

```
pdflatex nombre_del_archivo.tex
```

Y después

```
pdflatex nombre_del_archivo.tex
```



<br>
<hr>
<br>



## Mi recomendación de plantilla para una presentación en beamer

<object data="{{ '../assets/apuntes-latex/presentacion.pdf' | absolute_url }}" width="100%" height="300" type="application/pdf"></object>

Esta plantilla de presentación me gusta porque:

1. Es de color gris. Al usar una pantalla o proyector no lastima la vista. Si se usan imágenes blancas se distinguen bien por el fondo gris.

2. Esta presentación de beamer tiene una relación de aspecto 16:9 `\documentclass[aspectratio=169, xcolor=table]{beamer}`. Aprovecha espacio en la pantalla.

3. Los controles de navegación no ocupan tanto espacio y muestran información relevante: El nombre de los temas y la cantidad de diapositivas por tema.

4. En la esquina inferior derecha de cada diapositiva tiene el número de diapositiva. Que es útil para los espectadores si hay preguntas y respuestas después de la presentación ejemplo: "Tengo duda en la diapositiva 3" ó "En la diapositiva 1 hay una falta de ortografía"

[**La plantilla .tex de la presentación se puede encontrar en mi repositorio de GitHub**](https://github.com/JuanMX/plantillas-latex/tree/master/presentacion){:target="_blank"}

Plantilla obtenida de: http://www.LaTeXTemplates.com



<br>
<hr>
<br>



## Al usar pdflatex no aparece la bibiografía

Abrir una terminal y escribir:

```
pdflatex archivo.tex
```
Esto debe generar archivos, entre ellos uno con extensión `.aux`

Después escribir:

```
bibtex archivo.aux
```

Mostrará algo como:

```
This is BibTeX, Version 0.99d (TeX Live 2022/dev/Debian)
The top-level auxiliary file: archivo.aux
The style file: plain.bst
Database file #1: referencias.bib
```

Compilar para que aparezca la **sección** de referencias:

```
pdflatex archivo.tex
```

Finalmente compilar otra vez para cambiar 

[?] => [1]:

```
pdflatex archivo.tex
```



<br>
<hr>
<br>



## Mi recomendación de plantilla para un póster científico en LaTeX

<object data="{{ '../assets/apuntes-latex/conference_poster_6.pdf' | absolute_url }}" width="100%" height="500" type="application/pdf"></object>

Esta plantilla de póster científico me gusta porque:

1. Es de color blanco. Es el color común de una hoja de papel. Al imprimir el póster al menos el color de fondo se verá bien.

2. El póster es de tamaño 84 x 118.8 centímetros (cm) que es un tamaño común de póster científico.

3. Es de dos columnas, los párrafos llegarán a la mitad del ancho de la hoja. Compacta el ancho de los párrafos facilitando su lectura.

4. La plantilla está con el paquete de idioma español y se cambio el nombre "*Cuadro*" por "*Tabla*".

El póster cuenta con un *placeholder* de 3 logos para el cual tengo la siguiente recomendación:

> Si hay que poner más de un logo al póster, lo más rápido para lograrlo es hacer una única imagen que contenga todos los logos. Después poner la imagen única al póster.

[**La plantilla .tex del póster se puede encontrar en mi repositorio de GitHub**](https://github.com/JuanMX/plantillas-latex/tree/master/poster){:target="_blank"}

Plantilla obtenida de: http://www.LaTeXTemplates.com



<br>
<hr>
<br>



## Loren Ipsum

Para usar textos de tipo lorem ipsum a modo de placeholder lo que hago es:

```
\usepackage{lipsum}
```

Para usar renglones se usa:

```
\lipsum[1][1]
```
o
```
\lipsum[1][1-3]
```

Y para párrafos completos:

```
\lipsum[1]
```



<br>
<hr>
<br>



## Fusionar varios PDF en uno solo

En una ocasión me encontraba haciendo un trámite de hombre adulto. Ese trámite era por internet y contaba con muchos pasos, por cada paso se generaba un archivo PDF como probatorio de que fue completado con éxito. 

Como paso final debía mandar **un solo archivo PDF** que contenga todos los PDF de los pasos anteriores junto con otros archivos.

Por un momento mi mundo colapsó. No tenía idea de como *pegar* varios PDF para formar uno solo. Después de pensarlo con calma recordé que en el pasado (en mis épocas de estudiante) a mi tesis (hecha en LaTeX y que ya estaba completa) le debía agregar un oficio escaneado y en PDF. Para añadir ese PDF a otro que era mi tesis lo hice con LaTeX usando el paquete `\usepackage{pdfpages}`

La manera crear **un** PDF a partir de la unión de **dos** archivos PDF es con el siguiente fragmento de código:

``` tex
%%%%%%% archivo: fusion.tex %%%%%%%
\documentclass{book}
\usepackage{pdfpages} %paquete que permite agregar pdfs

\begin{document}

    \includepdf[pages=-,fitpaper=true]{documento1.pdf}
    \includepdf[pages=-,fitpaper=true]{documento2.pdf}
    %\includepdf[pages=-,fitpaper=true]{documento3.pdf}

    %%%%%%%%%%%
    % pages=-       significa que se van a agregar todas las paginas del archivo pdf
    % fitpaper=true significa que el documento se va a incluir con sus medidas de hoja originales
    % se pueden agregar mas pdfs al archivo agregando mas lineas de tipo \includepdf[pages=-,fitpaper=true]{archivo.pdf}
    %%%%%%%%%%%

\end{document}
```

[**Un ejemplo un poco más completo se encuentra en mi repositorio de GitHub**](https://github.com/JuanMX/plantillas-latex/tree/master/fusion){:target="_blank"}