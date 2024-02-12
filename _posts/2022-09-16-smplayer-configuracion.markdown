---
layout: post
title:  "Mi configuración de SMPlayer"
date:   2022-09-16 22:26:00 -0500
---

Sé que la mejor opción de reproductor multimedia es [VLC Media Player](https://www.videolan.org/vlc/){:target="_blank"} pero mi [laptop]({% post_url 2021-07-18-apuntes-dell-g7-7588 %}) tiene problemas al ejecutarlo.

Entonces elegí [SMPlayer](https://www.smplayer.info/){:target="_blank"}, ya lo conocía porque estaba incluido en la tienda de aplicaciones en viejas versiones de Ubuntu.

Fue muy tardado configurarlo para que me guste y por eso escribí al respecto.



<br>
<hr>
<br>



## Remover la barra de progreso de video

![img]({{ "../assets/smplayer-configuracion/smplayer_barra.png" | absolute_url }})

Para quitar la barra blanca de progreso se debe ir a 

***Ver -> Visualización en pantalla (OSD) -> Solo subtítulos***

![img]({{ "../assets/smplayer-configuracion/smplayer_barra_opciones.png" | absolute_url }})



<br>
<hr>
<br>



## Que el video se reproduzca en un ciclo infinito

Ir a 

***Opciones -> Preferencias***

![img]({{ "../assets/smplayer-configuracion/smplayer_opciones_preferencias.png" | absolute_url }})

En el menú de la izquierda ir a *Avanzadas* después a la pestaña *MPlayer/mpv*.

En el campo de texto que dice *Opciones:* escribir lo siguiente, después dar click en *Aceptar*.

```
--loop-file=inf
```

![img]({{ "../assets/smplayer-configuracion/smplayer_loop_inf.png" | absolute_url }})



<br>
<hr>
<br>



## En pantalla completa que aparezca la barra de navegación al mover el mouse a la parte inferior de la pantalla

Ir a 

***Opciones -> Preferencias***

![img]({{ "../assets/smplayer-configuracion/smplayer_opciones_preferencias.png" | absolute_url }})

En el menú de la izquierda ir a *Interfaz* después a la pestaña *Control flotante*.

Marcar la opción

- [x] *Mostrar solo al mover el ratón en la parte inferior de la pantalla*

![img]({{ "../assets/smplayer-configuracion/smplayer_mostrar_solo_parte_inferior.png" | absolute_url }})



<br>
<hr>
<br>



## Mostrar información del video en la parte inferior de la pantalla

Para mostrar información del video en el reproductor como se ve a continuación se debe hacer lo siguiente.

![img]({{ "../assets/smplayer-configuracion/smplayer_ejemplo_informacion_video.png" | absolute_url }})

Ir a 

***Opciones -> Barra de estado***

Yo tengo las siguientes opciones marcadas.

- [x] *Información del vídeo*
- [x] *Información del formato*
- [x] *Mostrar el tiempo total*

![img]({{ "../assets/smplayer-configuracion/smplayer_informacion_video.png" | absolute_url }})



<br>
<hr>
<br>



## Cambiar lo segundos que adelantan las flechas del teclado

Los segundos que se adelantan en un video o audio usando las flechas del teclado son de 10 segundos.

A mí me gusta que sean 5 segundos, como en su tiempo tenía por defecto YouTube. En SMPlayer eso se puede cambiar haciendo lo siguiente:

**Ir a Opciones -> Preferencias**

![smplayer-opciones->preferencias]({{ "../assets/smplayer-configuracion/smplayer_opciones_preferencias.png" | absolute_url }})

En la columna de la izquierda seleccionar **Interfaz**.

En la pestaña **Búsqueda** cambiar los segundos del **Salto corto** a 5, despúes aceptar los cambios.

![img]({{ "../assets/smplayer-configuracion/salto-corto.png" | absolute_url }})