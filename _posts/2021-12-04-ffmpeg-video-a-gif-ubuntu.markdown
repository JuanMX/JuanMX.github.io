---
layout: post
title:  "Hacer un gif a partir de la grabación de la pantalla en video con ffmpeg en ubuntu"
date:   2021-12-04 12:26:00 -0500
---  

![gifmuestra]({{ "../assets/ffmpeg-video-gif/output2.gif" | absolute_url }})

En ubuntu, grabar la pantalla y que sea un archivo gif era complicado para mí. Sé que una opción es usar [vokoscreen](https://linuxecke.volkoh.de/vokoscreen/vokoscreen.html){:target="_blank"} pero el resultado que me daba era un gif con errores.

Mi método para hacer un gif a partir de la grabación de la pantalla en video es:

1. Grabar la pantalla, puede ser con obs, vokoscreen, ffmpeg u otros. El objetivo es tener un archivo de video (mp4 por ejemplo).

2. Convertir el video a gif con [ffmpeg](http://www.ffmpeg.org/){:target="_blank"}, que es un programa por terminal.

La instrucción que uso es:

```
ffmpeg -i archivo_de_entrada.mp4 -vf "fps=10,scale=800:-1:flags=lanczos" -c:v pam -f image2pipe - | convert -delay 10 - -loop 0 -layers optimize archivo_de_salida.gif
```

donde:
* `archivo_de_entrada.mp4` es el archivo de video de entrada.
* `archivo_de_salida.gif` es el archivo gif de salida.
* `scale=800` es el ancho en pixeles del gif de salida.

ffmpeg y vokoscreen se encuentran en la tienda de aplicaciones de kubuntu18.04.

![vokoscreentienda]({{ "../assets/ffmpeg-video-gif/vokoscreen_y_ffmpeg.png" | absolute_url }})

En windows para grabar la pantalla y que sea un gif uso [CloudShot](https://cloudshot.com/){:target="_blank"}.

**Fuente:** [superuser.com/questions/556029 &mdash; *How do I convert a video to GIF using ffmpeg, with reasonable quality?*](https://superuser.com/questions/556029/how-do-i-convert-a-video-to-gif-using-ffmpeg-with-reasonable-quality){:target="_blank"}