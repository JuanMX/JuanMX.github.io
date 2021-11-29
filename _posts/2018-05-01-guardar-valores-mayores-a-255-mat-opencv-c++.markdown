---
layout: post
title:  "Guardar valores mayores a 255 en Mat de OpenCV para C++"
date:   2018-05-05 16:38:00 -0500
categories: Mat C++ OpenCV
---

Necesitaba una estructura de datos para el *tablero de regiones* del algoritmo [*Connected-component labeling*](https://en.wikipedia.org/wiki/Connected-component_labeling){:target="_blank"} y se me ocurrió usar el tipo de dato `Mat` de OpenCV para evitar implementar una matriz con su apuntador. Pero me encontré con un problema.

## El tipo de dato *Mat* de OpenCV no permite guardar valores mayores a 255

Cuando se guardan valores mayores a 255 en un `Mat` de OpenCV el resultado es el siguiente:

Valor a guardar en *Mat* | Resultado esperado | Resultado obtenido
-------------------------| -------------------| ---------------------
254                      | 254                | 254
255                      | 255                | 255
256                      | 256                | 0
257                      | 257                | 1

OpenCV intenta *recuperarse del error* reiniciando la cuenta a 0, después del número 255, pero esto puede provocar problemas en el código que se quiera ejecutar, obteniendo resultados no deseados.

Además no se avisa que se reinicia la cuenta después del número 255 y encontrar la falla en el código puede ser tardado.

Pero lo anterior tiene sentido porque `Mat` es de 8 bits que le permite guardar 256 valores. De 0 hasta 255 incluyendo el 0 y el 255.

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

Esto provoca que la variable `imagen` de tipo `Mat` guarde valores mayores a 255 y sea del mismo tamaño que la imagen que se abre con `imread`. En el caso que se quiera un `Mat` de tamaño distinto puede consultar [la siguiente documentación](https://docs.opencv.org/2.4/modules/core/doc/basic_structures.html#mat){:target="_blank"}.

**Fuente:** [answers.opencv.org/question/64279 &mdash; *Large Integer in cv::Mat*](http://answers.opencv.org/question/64279/large-integer-in-cvmat/){:target="_blank"}


