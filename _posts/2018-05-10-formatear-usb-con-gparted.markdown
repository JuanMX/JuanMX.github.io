---
layout: post
title:  "Formatear una memoria USB con GParted"
date:   2018-05-10 16:46:00 -0500
categories: gparted
--- 

* GParted -> Dispositivos -> Seleccionar la usb

![paso1]({{ "../assets/formateat-usb-gparted/paso1_seleccionar_memoria.png" | absolute_url }})

* Seleccionar nuevamente la usb de la lista de particiones -> Click derecho -> Desmontar

![paso2]({{ "../assets/formateat-usb-gparted/paso2_desmontar.png" | absolute_url }})

*Hay veces que no pide la opción, ya que el sistema operativo puede no montar de inmediato la memoria*

*Es normal que al desmontar la memoria realice una búsqueda de todos los dicos (extraíbles y no extraíbles) y que tarde mucho*

* Seleccionar nuevamente la usb de la lista de particiones -> Click derecho -> Formatear como -> fat32

![paso3]({{ "../assets/formateat-usb-gparted/paso3_formatear_como_fat32.png" | absolute_url }})

* Aplicar los cambios

![paso4]({{ "../assets/formateat-usb-gparted/paso4_aplicar_cambios.png" | absolute_url }})


*Es normal que al aplicar los cambios se realice una búsqueda de todos los dicos (extraíbles y no extraíbles) y que tarde mucho*

**Además se le puede poner un nombre a la memoria USB**

* Seleccionar nuevamente la usb de la lista de particiones -> Click derecho -> Etiqueta del sistema de archivos

Va a pedir que se introduzca un nombre

![paso5]({{ "../assets/formateat-usb-gparted/paso5_renombrar_memoria.png" | absolute_url }})

* Aplicar los cambios

![paso6]({{ "../assets/formateat-usb-gparted/paso6_aplicar_cambios.png" | absolute_url }})

* Al aplicar los cambios se puede mostrar un mensaje como este, sólo cierralo

![mensaje]({{ "../assets/formateat-usb-gparted/mensaje_de_completado.png" | absolute_url }})



**Fuente**

Lo enconré accidentalmente en un video en [YouTube](https://www.youtube.com/watch?v=hZbfzkb__0Y).

GParted se puede descargar [aqui](https://gparted.org/download.php).

También se puede encontrar en su gestor de *software* de su preferencia.

**Contexto**

Una de las cosas que necesitaba aprender en sistemas operativos de GNU/Linux era formatear una memoria USB y esta manera se me hace muy cómoda ya que uso GParted para *jugar* con mi disco duro.
