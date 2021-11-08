---
layout: post
title:  "KDE: Desactivar el proceso baloo_file para aumentar el rendimiento"
date:   2018-06-14 22:33:00 -0500
---  

Después de instalar en mi laptop *Linux Mint 18.3 con KDE* noté que usaba muchos recursos, el sistema operativo se sentía lento y los ventiladores trabajaban mucho. Al usar el monitor de sistema [KSysGuard](https://www.kde.org/applications/system/ksysguard/){:target="_blank"} me percaté de un proceso que consumía gran parte de la CPU llamado *baloo_file*.


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

Paso 3: Reiniciar la computadora o matar el proceso.

**Fuente:** [lignux.com &mdash; *Solución: Baloo_file_extractor consume toda la CPU (KDE)*](https://lignux.com/solucion-baloo_file_extractor-consume-toda-la-cpu-kde/){:target="_blank"}

