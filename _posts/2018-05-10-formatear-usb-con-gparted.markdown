---
layout: post
title:  "Formatear una memoria USB con GParted"
date:   2018-05-10 16:46:00 -0500
categories: gparted
--- 

Una de las cosas que necesitaba aprender al usar Ubuntu era formatear una memoria USB. Para mí, la manera más cómoda de hacerlo es con [GParted](https://gparted.org/download.php).

* GParted -> Dispositivos -> Seleccionar la usb

Para saber que se está seleccionado la memoria usb se puede guiar por la capacidad de almacenamiento del dispositivo.

![paso1]({{ "../assets/formateat-usb-gparted/paso1_seleccionar_memoria.png" | absolute_url }})

* Seleccionar nuevamente la usb de la lista de particiones -> Click derecho -> Desmontar

![paso2]({{ "../assets/formateat-usb-gparted/paso2_desmontar.png" | absolute_url }})

Hay veces que no pide la opción, porque el sistema operativo no monta la memoria de inmediato.

Es normal que al desmontar la memoria realice una búsqueda de todos los discos (extraíbles y no extraíbles) y que tarde mucho.

* Seleccionar nuevamente la usb de la lista de particiones -> Click derecho -> Formatear como -> fat32

![paso3]({{ "../assets/formateat-usb-gparted/paso3_formatear_como_fat32.png" | absolute_url }})

* Aplicar los cambios

![paso4]({{ "../assets/formateat-usb-gparted/paso4_aplicar_cambios.png" | absolute_url }})


Es normal que al aplicar los cambios se realice una búsqueda de todos los dicos (extraíbles y no extraíbles) y que tarde mucho.

### Además se le puede poner un nombre a la memoria USB

* Seleccionar nuevamente la usb de la lista de particiones -> Click derecho -> Etiqueta del sistema de archivos

Va a pedir que se introduzca un nombre.

![paso5]({{ "../assets/formateat-usb-gparted/paso5_renombrar_memoria.png" | absolute_url }})

* Aplicar los cambios

![paso6]({{ "../assets/formateat-usb-gparted/paso6_aplicar_cambios.png" | absolute_url }})

* Al aplicar los cambios se puede mostrar un mensaje como este, se debe dar click en *Cerrar*.

![mensaje]({{ "../assets/formateat-usb-gparted/mensaje_de_completado.png" | absolute_url }})



**Fuente**: [youtube.com &mdash; *formatear usb con GParted ( linux ubuntu )*](https://www.youtube.com/watch?v=hZbfzkb__0Y){:target="_blank"}