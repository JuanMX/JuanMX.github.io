---
layout: post
title:  "Github: Agregar expresiones matemáticas"
date:   2018-09-23 18:12:00 -0500
--- 

## Contenido

* [Agregar expresiones en un README](#agregar-expresiones-en-un-readme)

## Agregar expresiones en un README

De acuerdo con este [hilo de GitHub] no es posible agregarlas *tal cual* pero en el mismo hilo ofrecen esta alternativa:

1. Ir a la página [codecogs.com](https://www.codecogs.com/latex/eqneditor.php).
2. En el cuadro de texto escribir la expresión como en LaTeX o usando sus herramientas.
3. Dar click derecho en la imagen resultante y luego en la opción *copiar dirección de la imagen*.
4. El *link* copiado insertarlo en el archivo markdown como imagen.

A continuación se muentra el resultado de un par de pruebas

*Una recta se representa por la ecuación*: ![recta](https://latex.codecogs.com/gif.latex?%24y%3Dmx&plus;b%24)

*Una convolución se define como*:

![convolucion](https://latex.codecogs.com/gif.latex?%24%24w%28x%2Cy%29%20*%20f%28x%2Cy%29%20%3D%20%5Csum_%7Bs%3D-a%7D%5Ea%20%5Csum_%7Bt%3D-b%7D%5Eb%20w%28s%2Ct%29%20f%28x-s%2Cy-t%29%24%24)

**Fuente**

El [hilo de GitHub] mencionado arriba.

**Contexto**

Necesitaba agregar expresiones matemáticas a los README de GitHub y en GitHub Pages ya que mi repositorio es de tipo *Computer science portafolio*.

[hilo de GitHub]: https://github.com/github/markup/issues/897
