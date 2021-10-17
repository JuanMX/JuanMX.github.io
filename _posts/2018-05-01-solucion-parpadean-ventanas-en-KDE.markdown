---
layout: post
title:  "Ventanas que parpadean en KDE"
date:   2018-05-01 14:20:00 -0500
categories: KDE kde parpadean compositor vsync
--- 


Mi laptop necesitaba actualizarse de Ubuntu 12.04, encontré Linux Mint 18.3 con KDE el cual es compatible, en *drivers* de la tarjeta gráfica, wifi, usb 3.0 entre otros.

El único problema eran las ventanas parpadeantes. Después de unos minutos de iniciar el sistema operativo, se ven las ventanas parpadeantes si se pasa de ventana completa a ventana pequeña con el boton maximizar/restaurar. También se ve el efecto de parpadeo si se realiza *scroll* con el *mouse*.

## Solución

Ir a las **preferencias del sistema** y en la sección de **Hardware** ir a **Pantalla y monitor** después seleccionar **compositor**.

![pantalla-monitor-compositor]({{ "../assets/ventanas-parpadean-kde/pantalla-monitor-compositor.png" | absolute_url }})

Cambiar la opción que dice ***Prevención de efecto bandera (<<vsync>>)*** a ***Nunca*** y aplicar los cambios. Debería solucionarse el problema de inmediato, de lo contrario se puede cerrar e iniciar sesión o reiniciar el equipo. 

También se pueden cambiar las opciones del *Motor de renderizado* y poner una opción que arregle el problema.

![Configurar_las_preferencias_del_compositor_para_los_efectos_del_escritorio]({{ "../assets/ventanas-parpadean-kde/Compositor_Preferencias_del_sistema_001.png" | absolute_url }})

**Fuente:** [forum.kde.org &mdash; *Varias dudas y errores que tengo sobre KDE...*](https://forum.kde.org/viewtopic.php?t=136709){:target="_blank"}
