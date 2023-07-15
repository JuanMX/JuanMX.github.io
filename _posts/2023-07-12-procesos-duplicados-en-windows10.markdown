---
layout: post
title:  "Procesos duplicados en Windows 10"
date:   2023-07-12 17:00:00 -0500
categories: windows10
---

![demo]({{ "../assets/windows10/procesos-duplicados-demo.png" | absolute_url }})

Pensaba que era un virus pero no es mi caso.

Al buscar información me encontré con [esta entrada del foro de Microsoft.](https://answers.microsoft.com/es-es/windows/forum/all/servicios-y-procesos-repetidos-windows-10/1e7b4e97-b302-4f64-9dfc-789ce353980e){:target="_blank"} No quedé conforme con la respuesta, pero el post del foro da a entender que no es grave.

Después de buscar en el *Administrador de tareas* encontré a dos usuarios que corresponden a dos sesiones que tengo en Windows 10.

## En mi caso los procesos duplicados suceden por tener dos sesiones en la computadora

Yo tengo dos sesiones en mi computadora:

Una es para 🛠️🗿

La otra es para 🎮🗿

Los procesos duplicados me aparecen por no cerrar la sesión actual antes de cambiarme a otra sesión.

![dossesiones]({{ "../assets/windows10/procesos-duplicados-usuarios.png" | absolute_url }})

## Mi manera de cerrar una sesión

Click derecho en el Inicio de Windows -> Apagar o cerrar sesión -> Cerrar sesión

![cerrarsesion]({{ "../assets/windows10/cerrar-sesion.gif" | absolute_url }})