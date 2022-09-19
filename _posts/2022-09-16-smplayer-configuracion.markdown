---
layout: post
title:  "Mi configuración de SMPlayer"
date:   2022-09-16 22:26:00 -0500
---

Sé que la mejor opción de reproductor multimedia es [VLC Media Player](https://www.videolan.org/vlc/) pero mi [laptop]({% post_url 2021-07-18-apuntes-dell-g7-7588 %}) tiene problemas al ejecutarlo.

Entonces elegí [SMPlayer](https://www.smplayer.info/), ya lo conocía porque estaba incluido en la tienda de aplicaciones en viejas versiones de Ubuntu.

Fue muy tardado configurarlo para que me guste y por eso es escribí al respecto.

## Remover la barra de progreso de video

![img]({{ "../assets/smplayer-configuracion/smplayer_barra.png" | absolute_url }})

Para quitar la barra de color blanco se debe ir a 

Ver -> Visualización en pantalla (OSD) -> Solo subtítulos

![img]({{ "../assets/smplayer-configuracion/smplayer_barra_opciones.png" | absolute_url }})

## Que el video se reproduzca en un ciclo infinito

Ir a Opciones -> Preferencias

![img]({{ "../assets/smplayer-configuracion/smplayer_opciones_preferencias.png" | absolute_url }})

En el menú de la izquierda ir a *Avanzadas* después a la pestaña *MPlayer/mpv*.

En el campo de texto que dice *Opciones:* escribir lo siguiente, después dar click en *Aceptar*

```
--loop-file=inf
```

![img]({{ "../assets/smplayer-configuracion/smplayer_loop_inf.png" | absolute_url }})

## En pantalla completa que apareza la barra de navegacion al mover el mouse a laparte inferior de la pantalla

Ir a Opciones -> Preferencias

![img]({{ "../assets/smplayer-configuracion/smplayer_opciones_preferencias.png" | absolute_url }})

En el menú de la izquierda ir a *Interfaz* después a la pestaña *Control flotante*.

Marcar la opción

- [x] *Mostrar solo al mover el ratón en la parte inferior de la pantalla*

![img]({{ "../assets/smplayer-configuracion/smplayer_mostrar_solo_parte_inferior.png" | absolute_url }})

## Mostrar información del video en la parte inferior de la pantalla

Para mostrar información del video en el reproductor como se ve a continuacón se debe hacer lo siguiente.

![img]({{ "../assets/smplayer-configuracion/smplayer_ejemplo_informacion_video.png" | absolute_url }})

Ir a Opciones -> Barra de estado

Yo tengo marcado las siguientes opciones.

- [x] *Información del vídeo*
- [x] *Información del formato*
- [x] *Mostrar el tiempo total*

![img]({{ "../assets/smplayer-configuracion/smplayer_informacion_video.png" | absolute_url }})