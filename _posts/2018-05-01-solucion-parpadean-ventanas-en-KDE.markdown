---
layout: post
title:  "Ventanas que parpadean en KDE"
date:   2018-05-01 14:20:00 -0500
categories: KDE kde parpadean compositor vsync
--- 
 
## Problema

Cuando se esta en linux con KDE (en mi caso linux mint 18.3), después de unos minutos se ven las ventanas parpadeantes si se pasan de ventana completa a una ventana más pequeña con el boton maximizar (a veces conocido como restaurar), también se ve el efecto de parpadeo si se realiza un *scroll* con el *mause*.

## Solución

Ir a las **preferencias del sistema** y en la sección de **Hardware** ir a **Pantalla y monitor** después seleccionar **compositor**.

Cambiar la opción que dice *Prevención de efecto bandera (<<vsync>>)* a *Nunca* y aplicar los cambios, se debería solucionar inmediatamente, encaso contrario se puede intentar *logearse* de nuevo o reiniciar. 

También se pueden cambiar las opciones del *Motor de renderizado*

![Configurar_las_preferencias_del_compositor_para_los_efectos_del_escritorio]({{ "../assets/Compositor_Preferencias_del_sistema_001.png" | absolute_url }})

**Fuente**

Lo encontré en un tema en español del [foro de KDE](https://forum.kde.org/viewtopic.php?t=136709)

**Contexto**

Mi laptop necestiaba actualizarse de Ubuntu 12.04, encontré Linux Mint 18.3 con KDE el cual es compatible, en el sentido de *drivers* de la tarjeta gráfica, tarjeta de red, usb 3.0 entre otros.

El único problema eran las ventanas parpadeantes, después de tres dias buscando encontré esta solución.
