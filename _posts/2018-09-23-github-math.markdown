---
layout: post
title:  "Apuntes: Git y GitHub"
date:   2018-09-23 18:12:00 -0500
--- 

## Contenido

* [Agregar expresiones matemáticas en un README](#agregar-expresiones-matemáticas-en-un-readme)

* [Agregar expresiones matemáticas en GitHub Pages usando MathJax](#agregar-expresiones-matemáticas-en-github-pages-usando-mathjax)

* [Comandos que uso seguido en Git](#comandos-que-uso-seguido-en-git)

* [Server certificate verification failed](#server-certificate-verification-failed)

* [Remoto local](#remoto-local)



<br>
<hr>
<br>



## Agregar expresiones matemáticas en un README

De acuerdo con este [hilo de GitHub] no es posible agregarlas *tal cual* pero en el mismo hilo ofrecen la siguiente alternativa:

1. Ir a la página [codecogs.com](https://www.codecogs.com/latex/eqneditor.php).
2. En el cuadro de texto escribir la expresión como en LaTeX o usando las herramientas que brinda el sitio.
3. Dar click derecho en la imagen resultante y luego en la opción *copiar dirección de la imagen*.
4. El *link* copiado insertarlo en el archivo markdown como imagen.

*Ejemplo de una expresión matemática*: ![img](https://latex.codecogs.com/png.latex?\dpi{110}%20\frac{\sum_{i=1}^{n}%20x_i%20}{n})



**Fuente:** [github.com/github/markup/issues/897 &mdash; *Rendering math equations?*](https://github.com/github/markup/issues/897){:target="_blank"}



<br>
<hr>
<br>



## Agregar expresiones matemáticas en GitHub Pages usando MathJax

Necesitaba agregar expresiones matemáticas en GitHub Pages. Noté que en los [cursos de la Univerisdad de Standford](https://cs231n.github.io/convolutional-networks/){:target="_blank"} en GitHub Pages si ponen expresiones matemáticas. Buscando en su repositorio me encontré con el [primer indicio de *MathJax*](https://github.com/cs231n/cs231n.github.io/blob/master/_layouts/default.html){:target="_blank"}.


1. Agregar lo siguiente en el archivo *.markdown* (o HTML) que usará lenguaje matemático. Se sugiere ponerlo hasta el final del archivo.
```html
<script type="text/javascript" src="//cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.1/MathJax.js?config=TeX-AMS-MML_HTMLorMML"></script>
<script type="text/x-mathjax-config">
    // Make responsive
    MathJax.Hub.Config({
    "HTML-CSS": { linebreaks: { automatic: true } },
    "SVG": { linebreaks: { automatic: true } },
    });
</script>
```

2. Para escribir expresiones matemáticas centradas (en párrafo) se usa `$$ x $$` y para escribir en la misma linea que el texto (*inline*) se usa `\\( x \\)`.

Los pasos anteriores son para usar MathJax con la opción responsiva. Esto es, ajustar las expresiónes matemáticas al tamaño de la pantalla.

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

**Fuentes:**

Agregar *MathJax* en HTML (video no dispnible): [https://www.youtube.com/watch?v=qWrcgHwSG8M](https://www.youtube.com/watch?v=qWrcgHwSG8M){:target="_blank"}

Ejemplo de agregar *MathJax* en GitHub Pages: [cs231n.github.io/_layouts/default.html](https://github.com/cs231n/cs231n.github.io/blob/master/_layouts/default.html){:target="_blank"}



<br>
<hr>
<br>



## Comandos que uso seguido en Git

`git status` Estado del repositorio.

`git add NombreDeUnArchivo.extencion` Añade archivos para hacer el commit.

`git rm  NombreDeUnArchivo.extencion`Borra un archivo del repositorio.

`git rm -r NombreDeUnaCarpeta` Elimina una carpeta del repositorio.

`git commit` Realiza un commit (se habrirá un editor de texto para escribir los cambios hechos).

`git reset --soft HEAD~1` Deshace el último commit (puede cambiar esta instrucción según la versión de Git).

`git commit -m "Cambios hechos"` Hace un commit con un mensaje corto ("Cambios hechos") para no abrir un editor de textos.

`git remote -v` Muestra la URL del remoto (donde publicamos código)

`git push NOMBRE DEL REMOTO (origin) NOMBRE DE LA RAMA (master o alguna rama)` Sube el código al remoto (GitHub u otro, puede pedir usuario y contraseña de la cuenta de GitHub cuando se hace)



<br>
<hr>
<br>



## Server certificate verification failed

Este error me apareció al intentar pushear código.

```
juan@juanMX:~/proyecto$ git push origin master

fatal: unable to access 'https://git/juanmx/proyecto.git/': server certificate verification failed. CAfile: /etc/ssl/certs/ca-certificates.crt CRLfile: none
```

Una solución rápida es abrir una terminal y poner lo siguiente.

```
export GIT_SSL_NO_VERIFY=1
```

Lo anterior hace que no pida el certificado. 
Este cambio se revierte al apagar o reiniciar la computadora.

**Fuente:**

[shakaran.net/blog/2017/06 &mdash; *Solucionar error: server certificate verification failed. CAfile: /etc/ssl/certs/ca-certificates.crt CRLfile: none*](https://shakaran.net/blog/2017/06/solucionar-error-server-certificate-verification-failed-cafile/){:target="_blank"}



<br>
<hr>
<br>



## Remoto local

En lugar de escribir:

```
git push origin master
```

Para subir archivos a GitLab, GitHub o algún otro repositorio se puede cambiar el `origin` para que *apunte* a una carpeta en local.

Lo anterior es útil para monitorear archivos que se almacenan en un medio físico, como lo es un disco duro externo.

## De carpeta local a repositorio que almacene el proyecto

Con la terminal ir hasta la carpeta, después escribir:

```
git init --bare
```

En caso de que muestre la ruta del remoto tipo `C:/users/juanmx...` copiar la ruta.

## Agregar el remoto local a un proyecto ya inicializado con *git init*

Con la terminal ir a la carpeta y escribir:

```
git remote add originl C:/users/juanmx...
```

donde:

`originl` es el nombre del remoto, se puede sustituir por cualquier otro nombre.

## Para clonar el proyecto remoto local

```
git clone /c/users/juanmx/proyecto
```


[hilo de GitHub]: https://github.com/github/markup/issues/897

<script type="text/javascript" src="//cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.1/MathJax.js?config=TeX-AMS-MML_HTMLorMML"></script>
<script type="text/x-mathjax-config">
    // Make responsive
    MathJax.Hub.Config({
    "HTML-CSS": { linebreaks: { automatic: true } },
    "SVG": { linebreaks: { automatic: true } },
    });
</script>
