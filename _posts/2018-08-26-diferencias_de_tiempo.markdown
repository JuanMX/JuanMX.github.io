---
layout: post
title:  "Arreglar diferencias de la hora entre Windows y Linux en arranque dual"
date:   2018-08-26 18:50:00 -0500
---

Existen escenarios en que se tienen instalados algún sistema operativo de Microsoft Windows y una distribución GNU/Linux en una computadora en arranque dual (*dual boot* en inglés) provocando que el reloj de Windows se retrase unas horas, esto se debe a que la configuración horaria es diferente en los sistemas operativos como lo mencionan en [el foro de microsoft](https://answers.microsoft.com/es-es/windows/forum/windows_10-other_settings-winpc/cambio-de-hora-entre-windows-y-ubuntu/57ac767b-3c37-481d-9256-24efe94b8793). A continuación se muestran los pasos para corregir este problema desde Linux, en mi caso tengo *Linux Mint 18.3 con KDE*.

### Arreglar el problema de diferencias de hora entre Windows y Linux desde Linux

Abrir una terminal y escribir el siguiente comando:

```
timedatectl set-local-rtc 1
```

Probablemente se deba reiniciar para que se apliquen los cambios e ir a windows para ajustar el reloj a la hora.

Una manera de verificar que el comando surtió efecto es escribir en la terminal el comando:

```
timedatectl
```

Y verá la siguiente advertencia.

```
Warning: The system is configured to read the RTC time in the local time zone.
         This mode can not be fully supported. It will create various problems
         with time zone changes and daylight saving time adjustments. The RTC
         time is never updated, it relies on external facilities to maintain it.
         If at all possible, use RTC in UTC by calling
         'timedatectl set-local-rtc 0'.

```

**Fuente**

En el foro de windows [describen brevemente el problema](https://answers.microsoft.com/es-es/windows/forum/windows_10-other_settings-winpc/cambio-de-hora-entre-windows-y-ubuntu/57ac767b-3c37-481d-9256-24efe94b8793) y también presentan un solución que [se hace en Windows](https://answers.microsoft.com/es-es/windows/forum/windows8_1-start/solventar-la-sincronizaci%C3%B3n-de-la-hora-en-un/d106214d-49e5-4296-b24d-aad0650c8cfe).

La solución desde Linux la encontré en una entrada en español en el [foro de Linux Mint](https://forums.linuxmint.com/viewtopic.php?t=240122).

**Contexto**

No había tenido este problema en el pasado, cuando pasó yo pensé que el problema era el sistema operativo de windows pero después busqué el problema y encontré esta solución.
