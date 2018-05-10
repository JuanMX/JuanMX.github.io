---
layout: post
title:  "Guardar valores mayores a 255 en Mat de OpenCV para C++"
date:   2018-05-05 16:38:00 -0500
categories: Mat C++ OpenCV
---

## El tipo de dato *Mat* en *OpenCV* no permite guardar valores mayores a 255

Cuando se guardan valores mayores a 255 en la variable *Mat* de OpenCV (que normalmente guardan valores en *escala de grises*) el resultado es parecido al siguiente:

Valor a guardar en *Mat* | Resultado esperado | Resultado obtenido
-------------------------| -------------------| ---------------------
254                      | 254                | 254
255                      | 255                | 255
256                      | 256                | 0
257                      | 257                | 1

## Problema

OpenCV intenta *recuperarse del error* reiniciando la cuenta a 0, después del número 255, pero esto puede provocar problemas en el código que se quiera ejecutar, obteniendo resultados no deseados.

Además no se avisa que se reinicia la cuenta después del número 255 y encontrar la falla en el código puede ser tardado.

## Solución con un código de ejemplo

{% highlight C++ %}

int i,j,valor=250;

Mat imagen2 = imread(argv[1], 0);// abre gris

Mat imagen(imagen2.size(), CV_32S);//copia el tamaño de imagen2 pero usa 32bits en lugar de 8bits

for( i = 0; i< imagen.rows; i++){
    for(j=0;j<imagen.cols;j++){
        imagen.at<int32_t>( i, j ) = valor; // es muy importante el .at<int32_t>(i,j), para que funcione
    }
    valor++;
}

{% endhighlight %}

Esto provoca que el `Mat` que guarde valores mayores a 255 sea del mismo tamaño que una imagen que se abre con `imread`, en el caso que se quiera un `Mat` de tamaño distinto puede consultar [la siguiente documentación](https://docs.opencv.org/2.4/modules/core/doc/basic_structures.html#mat)

**Fuente**

Lo encontré en un tema del [foro de OpenCV](http://answers.opencv.org/question/64279/large-integer-in-cvmat/)

**Contexto**

Necesitaba una estructura de datos para el *tablero de regiones* del algoritmo [*Connected-component labeling*](https://en.wikipedia.org/wiki/Connected-component_labeling) y se me ocurrió usar el tipo de dato *Mat* de OpenCV para ahorrarme implementar una matriz con su apuntador, pero me encontré con el problema de que *Mat* no guarda valores mayores a 255.
