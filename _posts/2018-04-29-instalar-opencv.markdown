---
layout: post
title:  "Instalar OpenCV"
date:   2018-04-29 17:53:38 -0500
categories: c/c++ opencv truncado shared
--- 

Los pasos mostrados a continuación fueron probados con éxito en los siguientes sistemas operativos:
* Ubuntu 12.04 con Unity
* Ubuntu 16.04 con Unity
* Linux Mint 18.2 con KDE
* Linux Mint 18.3 con KDE

Los pasos mostrados a continuación fueron probados con éxito en las siguientes versiones de OpenCV:
* OpenCV 3.0.0
* OpenCV 3.3.1

Muchos de los pasos mostrados a continuación fueron obtenidos de la [documentación oficial de OpenCV para su instalación](https://docs.opencv.org/master/d7/d9f/tutorial_linux_install.html)

# Instalar los paquetes requeridos

```bash
sudo apt-get install build-essential
sudo apt-get install cmake git libgtk2.0-dev pkg-config libavcodec-dev libavformat-dev libswscale-dev
sudo apt-get install python-dev python-numpy libtbb2 libtbb-dev libjpeg-dev libpng-dev libtiff-dev libjasper-dev libdc1394-22-dev
```

# Obtener el código fuente

Se puede encontrar [aqui](https://opencv.org/releases.html)

# *Compilar* el código fuente

* Descomprimir el archivo del código fuente

* Posicionarse con la terminal en la carpeta descomprimida y crear la carpeta *build*
```bash
cd ~/opencv
mkdir build
cd build
```

* Instalar cmake-gui

`sudo apt install cmake-qt-gui`

* Ejecutar cmake-gui

`cmake-gui`

* Poner la ruta completa al código fuente (ejemplo: /home/user/opencv)
* Poner la ruta completa a la carpeta *build* (ejemplo: /home/user/opencv/build)
* Cambiar algún parámetro si se desea
* *Click*: *Configure*
* *Click*: *Generate*

* Compilar con `make` usando varios hilos (va a tardar, la terminal sigue en la carpeta *build*)
```bash
make -j7
```
tal vez pida hacerlo como super usuario 
```bash
sudo make -j7
```
* Instalar mediante
```bash
sudo make install
```
(la terminal sigue en la carpeta *build*)

# Solución a un par de problemas

# Solución para *loading shared libraries*
Si se complia sin problemas pero al ejecutarse se muestra un mensaje como

```
error while loading shared libraries: libopencv_highgui.so.3.3: cannot open shared object file: No such file or directory
```

A veces cambia la *versión* y nombre de *libopencv*, por ejemplo `libopencv_contours.so.2.4`

Para solucionarlo se debe crear en la ubicación:
```
/etc/ld.so.conf.d
```
el archivo `opencv.conf`
y escribir en él la ruta en dónde se encuentra el archivo
`libopencv_core.so.3.0`
por ejemplo, se puede encontrar en alguna de las siguientes rutas
```
/usr/local/lib/
```
```
/usr/local/localx86_x64/lib/
```

También se puede buscar el archivo `libopencv_core.so.3.0` con la orden de la terminal

```bash
locate libopencv_core.so.3.0
```
Y por último *refrescar* las rutas a las librerías
```bash
sudo ldconfig -v
```

# Solución para archivos truncados

Puede aparecer un error de fichero truncado cuando se deja a medias el `sudo make -j7` como este:
```bash
make[1]: *** [modules/imgproc/CMakeFiles/opencv_test_imgproc.dir/all] Error 2
[ 79%] Built target opencv_calib3d
CMakeFiles/opencv_test_core.dir/test/test_ds.cpp.o: no se reconoce el fichero: Fichero truncado
collect2: error: ld returned 1 exit status
modules/core/CMakeFiles/opencv_test_core.dir/build.make:882: fallo en las instrucciones para el objetivo 'bin/opencv_test_core'
make[2]: *** [bin/opencv_test_core] Error 1
CMakeFiles/Makefile2:1699: fallo en las instrucciones para el objetivo 'modules/core/CMakeFiles/opencv_test_core.dir/all'
make[1]: *** [modules/core/CMakeFiles/opencv_test_core.dir/all] Error 2
Makefile:160: fallo en las instrucciones para el objetivo 'all'
```
Para solucionarlo se debe abrir el `cmake-gui` y seguir los pasos para instalar, pero en las opciones se debe de desactivar esta opcion de cmake:
```
-DENABLE_PRECOMPILED_HEADERS=OFF
```
y seguir los pasos de instación normalmente.

**Contexto**

En la escuela me pideron OpenCV para hacer un par de projectos grandes, además necesité instalarlo en un pc de la escuela y mi laptop después de formatearla varias veces.
