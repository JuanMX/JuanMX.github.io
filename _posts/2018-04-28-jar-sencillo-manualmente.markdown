---
layout: post
title:  "Crear un archivo jar manualmente"
date:   2018-04-28 22:14:38 -0500
categories: java jar
---

En un solo directorio poner al menos todos los archivos `.class` del programa.

Crear un archivo `myManifest` (no lleva extención de archivo) con el siguiente contenido.

```
Manifest-Version: 1.0 
Main-Class: MyMainClass
```

`MyMainClass` es el nombre de la **clase** que tiene el método *main*

Escribir en la terminal

```bash
jar cvfm myResult.jar myManifest *.java *.class
```

**Fuente**

Mi compañero de equipo encontró el *post* en un
[sitio universitario](http://www.cis.upenn.edu/~matuszek/cit597-2002/Pages/executable-jar-files.html)

**Contexto**

Para hacer puntos extra en los primeros proyectos de Java en la escuela, se entrego un ejecutable de un proyecto final.
