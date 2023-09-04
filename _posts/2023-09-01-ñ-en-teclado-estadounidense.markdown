---
layout: post
title:  "Usar la Ñ de un teclado estadounidense en Windows 10 y Kubuntu 22.04"
date:   2023-09-01 17:00:00 -0500
categories: windows10 kubuntu teclado
---

Necesitaba un teclado nuevo y se me ocurrió comprar un teclado mecánico en Amazon, sería mi primer teclado mecánico.

Cuando llegó lo noté raro. Al verlo detenidamente noté que **no** era un teclado latinoamericano, era un teclado inglés.

Para evitar conflictos con Amazon decidí conservar el teclado intentado aprender a usar los caracteres especiales del idioma español (Ñ, Á, É, Í, Ó, Ú, Ü, entre otros).

Con el tiempo descubrí que a un teclado inglés se le puede agregar la distribución de teclado *Estados Unidos Internacional* que resuelve mi problema de uso de caracteres especiales.

## Teclado de Estados Unidos Internacional

Un teclado de Estados Unidos se ve asi:

![eu](https://upload.wikimedia.org/wikipedia/commons/thumb/5/51/KB_United_States-NoAltGr.svg/2560px-KB_United_States-NoAltGr.svg.png)

Un teclado de Estados Unidos **Internacional** se ve asi:

![euint](https://upload.wikimedia.org/wikipedia/commons/thumb/2/22/KB_US-International.svg/2560px-KB_US-International.svg.png)

En este teclado se debe seguir una secuencia de teclas para obtener los caracteres especiales.

Para sacar la Ñ:
* Minúscula: [Alt Gr] + [N]
* Mayúscula: [Alt Gr] + [Shift] + [N]

Vocales acentuadas:
* Minúscula: [Alt Gr] + [A] (o la tecla de otra vocal) 
* Mayúscula: [Alt Gr] + [Shift] + [A] (o la tecla de otra vocal)

## Teclado de Estados Unidos Internacional en Windows 10

En el **menu inicio** escribir *Configuracion* y dar click en el primer resultado.

En el menú de Configuración ir a la opción *Hora e idioma*.

![img]({{ "../assets/ñ-teclado-windows-kubuntu/ñ-windows10-1.png" | absolute_url }})

Ir a la sección *Idioma* y en la parte *Idiomas preferidos* dar click en *Agregar un idioma*.

El idioma que se tiene que agregar es el de *Inglés Estados Unidos*.

![img]({{ "../assets/ñ-teclado-windows-kubuntu/ñ-windows10-2.png" | absolute_url }})

Con el idioma *Inglés (Estados Unidos)* agregado darle click para abrir el menú, depués dar click en *Opciones*.

![img]({{ "../assets/ñ-teclado-windows-kubuntu/ñ-windows10-3.png" | absolute_url }})

En las opciones de idioma dar click en *Agregar un teclado*, después seleccionar *Estados Unidos - Internacional*.

![img]({{ "../assets/ñ-teclado-windows-kubuntu/ñ-windows10-4.png" | absolute_url }})

Sugiero que únicamente se tenga agregado el teclado *Estados Unidos - Internacional*. Si hay otro teclado agregado se debe quitar.

Eso es todo. Un atajo rápido para cambiar de idioma que también cambiará el teclado es: <br>
[Windows] + [Barra de espacio].

**Fuente:** [youtube.com/@TorotochoReviews &mdash; *Acentos, tecla ñ y mas en teclados chinos con QWERTY Ingles*](https://www.youtube.com/watch?v=F7q7ZG9cKlA){:target="_blank"}


## 🚧 Teclado de Estados Unidos Internacional en Kubuntu 22.04 🚧