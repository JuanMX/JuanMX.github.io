---
layout: post
title:  "Arreglar diferencias de la hora entre Windows y Linux en arranque dual"
date:   2018-08-26 18:50:00 -0500
---

Puede existir el caso en que se tiene instalado un sistema operativo de Microsoft Windows junto a Linux Mint o Ubuntu en una computadora con arranque dual (*dual boot*) provocando que la hora en Windows se desajuste. Lo anterior se debe a que la configuración horaria es diferente en los sistemas operativos como lo mencionan en una entrada del [foro de microsoft](https://answers.microsoft.com/es-es/windows/forum/windows_10-other_settings-winpc/cambio-de-hora-entre-windows-y-ubuntu/57ac767b-3c37-481d-9256-24efe94b8793). 

Como no había tenido este problema en el pasado decidí escribir sobre como lo arreglé y guardarlo como apunte.

## Arreglar el problema de diferencias de hora entre Windows y Linux desde Linux

Abrir una terminal y escribir el siguiente comando:

```
timedatectl set-local-rtc 1
```

Se recomienda reiniciar la computadora e ir a Windows para ajustar el reloj a la hora.

Una manera de verificar que el comando surtió efecto es escribir en la terminal el comando:

```
timedatectl
```

Y se verá la siguiente advertencia.

```
Warning: The system is configured to read the RTC time in the local time zone.
         This mode can not be fully supported. It will create various problems
         with time zone changes and daylight saving time adjustments. The RTC
         time is never updated, it relies on external facilities to maintain it.
         If at all possible, use RTC in UTC by calling
         'timedatectl set-local-rtc 0'.

```

**Fuentes:**

Descripción de este problema: [answers.microsoft.com - *Cambio de hora entre Windows y Ubuntu*](https://answers.microsoft.com/es-es/windows/forum/windows_10-other_settings-winpc/cambio-de-hora-entre-windows-y-ubuntu/57ac767b-3c37-481d-9256-24efe94b8793) 

Solucionar el problema desde Windows (no lo he probado): [answers.microsoft.com - *Solventar la sincronización de la hora en un sistema de arranque dual Windows/Linux*](https://answers.microsoft.com/es-es/windows/forum/windows8_1-start/solventar-la-sincronizaci%C3%B3n-de-la-hora-en-un/d106214d-49e5-4296-b24d-aad0650c8cfe).

Solucionar el problema desde Linux Mint: [forums.linuxmint.com - *Problema con la hora cuando Windows y Linux dual boot: Solución*](https://forums.linuxmint.com/viewtopic.php?t=240122).
