---
layout: post
title:  "Apuntes: Git y Github"
date:   2018-09-23 18:12:00 -0500
--- 

## Contenido

* [Agregar expresiones matemáticas en un README](#agregar-expresiones-matemáticas-en-un-readme)
* [Agregar expresiones matemáticas en GitHub Pages](#agregar-expresiones-matemáticas-en-github-pages)
* [Comandos que uso seguido en Git](#comandos-que-uso-seguido-en-git)

## Agregar expresiones matemáticas en un README

De acuerdo con este [hilo de GitHub] no es posible agregarlas *tal cual* pero en el mismo hilo ofrecen esta alternativa:

1. Ir a la página [codecogs.com](https://www.codecogs.com/latex/eqneditor.php).
2. En el cuadro de texto escribir la expresión como en LaTeX o usando las herramientas que brinda el sitio.
3. Dar click derecho en la imagen resultante y luego en la opción *copiar dirección de la imagen*.
4. El *link* copiado insertarlo en el archivo markdown como imagen.

A continuación se muentra el resultado de un par de pruebas

*Una recta se representa por la ecuación*: ![recta](https://latex.codecogs.com/gif.latex?%24y%3Dmx&plus;b%24)

*Una convolución se define como*:

![convolucion](https://latex.codecogs.com/gif.latex?%24%24w%28x%2Cy%29%20*%20f%28x%2Cy%29%20%3D%20%5Csum_%7Bs%3D-a%7D%5Ea%20%5Csum_%7Bt%3D-b%7D%5Eb%20w%28s%2Ct%29%20f%28x-s%2Cy-t%29%24%24)

**Fuente**

El [hilo de GitHub] mencionado arriba.

**Contexto**

Necesitaba agregar expresiones matemáticas a los README de GitHub y en GitHub Pages ya que mi repositorio tiene un poco de *Computer science portafolio*.

[**Ir a la sección Contenido**]

## Agregar expresiones matemáticas en GitHub Pages

**Nota:** los siguientes pasos no son los mejores, yo no tengo formación ni conocimientos en desarrollo web, a pesar de eso el resultado de mostrar fórmulas matemáticas es bueno.

Para mostrar expreiones matemáticas en GitHub Pages se puede usar el método descrito arriba pero en este caso si se puede usar LaTeX, enseguida se describen los pasos para hacerlo.

1. Agregar la siguinte linea en el archivo *.markdown* de tipo *post* en el que se escribirá con lenguaje matemático.
```html
<script type="text/javascript" src="//cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML"></script>
```

2. Para escribir expresiones (o fórmulas) matemáticas centradas se usa `$$ x $$` y para escribir en la misma linea que el texto se usa `\\( x \\)`.

A continuación se muestran ejemplos.

**Ejemplo No. 1**

```latex
*La siguiente expresión matemática se ve impresionante:*

$$\cos\bar{\phi}_k Q_{j,k+1,t} + Q_{j,k+1,x}+ \frac{\sin^2\bar{\phi}_k}{T\cos\bar{\phi}_k} Q_{j,k+1} = -\cos\phi_j Q_{j,k,t} + Q_{j,k,y}-\frac{\sin^2\phi_j}{T\cos\phi_j} Q_{j,k}$$

```
*La siguiente expresión matemática se ve impresionante:*

$$\cos\bar{\phi}_k Q_{j,k+1,t} + Q_{j,k+1,x}+ \frac{\sin^2\bar{\phi}_k}{T\cos\bar{\phi}_k} Q_{j,k+1} = -\cos\phi_j Q_{j,k,t} + Q_{j,k,y}-\frac{\sin^2\phi_j}{T\cos\phi_j} Q_{j,k}$$

**Ejemplo No. 2**

```latex
*La fórmula* \\(I(\nu, T) = \frac{2h\nu^3}{c^2} \frac{1}{e^{\frac{h \nu}{kT}} - 1}\\) *se usa para calcular la radiación espectral de cuerpos a diferentes temperaturas, a esta fórmula se le conoce como función de Planck*.
```
*La fórmula* \\(I(\nu, T) = \frac{2h\nu^3}{c^2} \frac{1}{e^{\frac{h \nu}{kT}} - 1}\\) *se usa para calcular la radiación espectral de cuerpos a diferentes temperaturas, a esta fórmula se le conoce como función de Planck*.

**Fuente**

En [este video](https://www.youtube.com/watch?v=qWrcgHwSG8M) muestran como poner *MathJax* en todo el sitio en un archivo *.html*. A mi se me ocurrió ponerlo en el archivo *.markdown* con el *post* matemático ya que *markdown* se *compila* a html en GitHub Pages.

**Contexto**

Necesitaba agregar expresiones matemáticas en GitHub Pages. Noté que en los cursos de la Univerisdad de Standford alojados en GitHub Pages si ponen expresiones matemáticas, investigando en su repositorio me encontré con el [primer indicio de *MathJax*](https://github.com/cs231n/cs231n.github.io/blob/master/_layouts/default.html) y el video puesto en la sección  **Fuente** me confirmó para que sirve. Como yo uso GitHub Pages con las opciones por *default* no me produce archivos *.html* pero si *.markdown*, asi que se me ocurrió importar *MathJax* desde ahí.

[**Ir a la sección Contenido**]

## Comandos que uso seguido en Git

* `git status`

Estado del repositorio

* `git diff`

Muestra los cambios en el archivo modificado

* `git add NombreDeUnArchivo.extencion`

Añade archivos para hacer el commit

* `git reset HEAD NombreDeUnArchivo.extencion`

Quita archivos para hacer el commit

* `git rm  NombreDeUnArchivo.extencion`

Borra un archivo del repositorio

* `git rm -r NombreDeUnaCarpeta`

Elimina una carpeta

* `git commit`

Realiza un commit (se habrirá un editor de texto de terminal para escribir los cambios hechos)

* `git reset --soft HEAD~1`

Deshace el último commit (puede cambiar esta instrucción según la versión de Git)

* `git commit -m "Cambios hechos"`

Hace un commit con un mensaje corto ("Cambios hechos") para no abrir un editor de textos

* `git remote`

Muestra el nombre del remoto

* `git remote -v`

Muestra la URL del remoto (donde publicamos código)

* `git push NOMBRE DEL REMOTO (origin) NOMBRE DE LA RAMA (master o alguna rama)`

Sube el código al remoto (github u otro, puede pedir usuario y contraseña cuando se hace)

[**Ir a la sección Contenido**]


[**Ir a la sección Contenido**]: #contenido

[hilo de GitHub]: https://github.com/github/markup/issues/897

<script type="text/javascript" src="//cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML"></script>
