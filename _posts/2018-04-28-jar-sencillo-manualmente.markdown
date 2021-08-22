---
layout: post
title:  "Crear un archivo jar manualmente"
date:   2018-04-28 22:14:38 -0500
categories: java jar
---


En mis clases de Java de la universidad, para hacer puntos extra en un proyecto final, se tenía que entregar un ejecutable `.jar`. Mi compañero de equipo encontró la manera de como crearlo.

## Crear un .jar

En un solo directorio poner al menos todos los archivos `.class` del programa.

Crear un archivo `myManifest` (no lleva extención de archivo) con el siguiente contenido:

```
Manifest-Version: 1.0 
Main-Class: MyMainClass
```

`MyMainClass` es el nombre de la **clase** que tiene el método **main**.

Abrir una terminal y posicionarla en la carpeta donde están los `.class` y `myManifest`, después escribir:

```bash
jar cvfm myResult.jar myManifest *.java *.class
```

**Fuente:** [cis.upenn.edu CIT 597 Executable .jar Files](http://www.cis.upenn.edu/~matuszek/cit597-2002/Pages/executable-jar-files.html)