---
layout: post
title:  "Apuntes: LaTeX"
date:   2023-07-19 17:00:00 -0500
categories: latex beamer
---

Estaba revisando un viejo disco duro que tenía por ahí y me encontré con documentos de todo lo que hice en la universidad referente a LaTeX, es decir, mi tesis, diapositivas y un póster científico.

Al revisar los documentos noté que aprendí algunos trucos sobre LaTeX y eso me motivó a hacer esta entrada de blog.

Probablemente este post contiene conocimiento obsoleto pero no me importa.



<br>
<hr>
<br>




## Instalar texlive-full en Kubuntu 22.04

Recomiento ampliamente instalar LaTeX full para evitar problemas a futuro de que falten paquetes. El problema es que dicha instalación necesita tiempo y espacio en el disco.

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

2. Esta presentación de beamer tiene un aspecto 16:9 `\documentclass[aspectratio=169, xcolor=table]{beamer}`. Aprovecha espacio en la pantalla.

3. Los controles de navegación no ocupan tanto espacio y muestran información relevante: El nombre de los temas y la cantidad de diapositivas por tema.

4. En la esquina inferior derecha de cada diapositiva tiene el número de diapositiva. Que es útil para los espectadores si hay preguntas y respuestas después de la presentación ejemplo: "Tengo duda en la diapositiva 3" ó "En la diapositiva 1 hay una falta de ortografía"

[**La plantilla .tex de la presentación se puede encontrar en mi repositorio de GitHub**](https://github.com/JuanMX/plantillas-latex/tree/master/presentacion){:target="_blank"}

Plantilla obtenida de: http://www.LaTeXTemplates.com



<br>
<hr>
<br>



## Al usar pdflatex no aparece la bibiografía [?]

Abrir una terminal y escribir:

```
pdflatex archivo.tex
```
Esto debe generar archivos, entre ellos uno `.aux`

Después:

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

Compilar para que aparezca la sección de referencias:

```
pdflatex archivo.tex
```

Finalmente compilar de nuevo para que aparezcan las citas de tipo [1], [2]:

```
pdflatex archivo.tex
```