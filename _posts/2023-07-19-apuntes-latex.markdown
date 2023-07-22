---
layout: post
title:  "Apuntes: LaTeX"
date:   2023-07-19 17:00:00 -0500
categories: latex beamer
---

Estaba revisando un viejo disco duro que tenía por ahí y me encontré con documentos de todo lo que hice en la universidad referente a LaTeX, es decir, mi tesis, diapositivas y un póster científico.

Al revisar los documentos noté que aprendí algunos trucos sobre LaTeX y eso me motivó a hacer esta entrada de blog.

Probablemente este post contiene conocimiento obsoleto.

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