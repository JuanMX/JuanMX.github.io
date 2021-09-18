---
layout: post
title:  "BusyBox v1.22.1 (Ubuntu 1:1.22.0-15ubuntu1) built-in shell (ash): Una posible solución"
date:   2018-09-02 18:57:00 -0500
---

En una ocasión apagué mi computadora por 20 minutos y la encendí de nuevo, en lugar de iniciar mi sistema operativo
*Linux Mint 18.2 con KDE* apareció la siguiente linea de comandos:

```
BusyBox v1.22.1 (Ubuntu 1:1.22.0-15ubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) _
```

## Posible solución

Investigando un poco desde una computadora portátil encontré la siguiente solución.

**Escribir el comando `exit`**

```
# Escribir el comando 'exit'
(initramfs) exit

/dev/sda6 contains a file system with errors, checked forced.
Invalid inode number for '.' in directory inode 6425099.

/dev/sda6 UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
            (i.e., without -a or -p options)
            
fsck exited with status code 4
The root filesystem on /dev/sda6 requires a manual fsck

BusyBox v1.22.1 (Ubuntu 1:1.22.0-15ubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands

(initramfs) _
```
Parece que `/dev/sda6` es la partición en el disco duro donde esta el root (`/`) de *Linux Mint* que pide que se repare (`The root filesystem on /dev/sda6 requires a manual fsck`)

**Escribir el comando `fsck PARTCIÓN DONDE PIDIÓ EL COMANDO ANTERIOR QUE SE REPARE`, en mi caso `fsck /dev/sda6`**

```
(initramfs) fsck /dev/sda6
fsck from util-linux 2.27.1
e2fsck 1.42.13 (17-May-2015)
/dev/sda6 contains a filesystem with errors, checked forced.

Pass 1: Checking inodes, blocks, and sizes

Pass 2: Checking directory structure
Invalid inode number for '.' in directory inode 6425099
Fix<y>?
# ME MARCÓ VARIOS ERRORES DE ESTE TIPO, PARA REPARARLOS PULSÉ LA TECLA [y]

Pass 3: Checking directory connectivity
'..' in /tmp/.XIM-unix (6425099) is <6425111> (6425111), should be /tmp (6422529).
Fix<y>?
# PARA REPARAR ESTE ERROR PULSÉ LA TECLA [y]

Pass 4: Checking reference counts
Inode 6422529 ref count is 11, should be 10. Fix<y>?
# ME MARCÓ VARIOS ERRORES DE ESTE TIPO, PARA REPARARLOS PULSÉ LA TECLA [y]

Pass 5: Checking group summary information
Block bitmap differences -16832000 +48320514
Fix<y>? yes
Free blocks count wrong for group #513 (4667, counted=4668).
Fix<y>?
# ME MARCÓ VARIOS ERRORES DE ESTE TIPO, PARA REPARARLOS PULSÉ LA TECLA [y]

/dev/sda6: ***** FILE SYSTEM WAS MODIFIED *****
/dev/sda6: 422907/12500992 files (0.1% non-contiguous), 5873860/50000128 blocks
(initramfs) _
```

Si después de esto no inicia el sistema operativo va a ser necesario reiniciar la computadora. El problema debería estar resuelto.

**Fuente**

Foro de [*ask ubuntu*](https://askubuntu.com/questions/741109/ubuntu-15-10-busybox-built-in-shell-initramfs-on-every-boot)
