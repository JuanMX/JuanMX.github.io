---
layout: post
title:  "KDE: Desactivar el proceso baloo_file para aumentar el rendimiento"
date:   2018-06-14 22:33:00 -0500
---  


## Problema

Cuando se esta en *Linux Mint con KDE* se puede tener el problema de que el sistema va lento y los ventiladores trabajan mucho.

Tal vez esto se deba al proceso *baloo_file*.

![CPU_27pct]({{ "../assets/baloo-file/baloo_file_CPU_27pct.png" | absolute_url }})

![CPU_27pct_grafica]({{ "../assets/baloo-file/baloo_file_CPU_27pct_grafica.png" | absolute_url }})

## Solución 

Los pasos mostrados fueron probados con éxito en:

* *Linux Mint 18.3 con KDE*.
* *Linux Mint 18.2 con KDE*.

Paso 1: Ir a las *preferencias del sistema* e ingresar al apartado *buscar*.

![CPU_27pct]({{ "../assets/baloo-file/preferencias-buscar.png" | absolute_url }})

Paso 2: **Desactivar** la opción *Activar la búsqueda de archivos*.

![CPU_27pct_grafica]({{ "../assets/baloo-file/baloo_file_CPU_27pct_solucion.png" | absolute_url }})

Paso 3: Reiniciar o matar el proceso.

**Fuente**

Lo encontré en una página de [entusiastas de linux](https://lignux.com/solucion-baloo_file_extractor-consume-toda-la-cpu-kde/), se puede ver que la publcación es de finales del año 2015 pero me funcionó.

**Contexto**

Después de instalar en mi laptop *Linux Mint 18.3 con KDE* e instalar *Linux Mint 18.2 con KDE* en una PC noté que usaba muchos recursos, al usar el monitor de sistema [KSysGuard](https://www.kde.org/applications/system/ksysguard/) vi que el proceso que consumía recursos se llamaba *baloo-file*.
