---
layout: post
title:  "Instalar Visual Studio Code para todos los usuarios en Windows 10"
date:   2024-05-27 18:00:00 -0500
categories: vscode windows10
---

En mi computadora tengo un usuario llamado *Juan MX*. Es muy común que tenga problemas con programas de computadora porque el nombre de usuario genera una carpeta con espacio en blanco tipo `C:\Users\Juan MX`. Me parece que ese espacio en blanco *rompe* las rutas absolutas hacia archivos y carpetas.

Harto de tener este problema me hice un usuario local con permisos de administrador y sin espacios en blanco como *JuanMX*. Creí que tendría acceso a todos los programas instalados, pero noté que no podia usar Visual Studio Code (vscode), uno de los programas más importantes para mí.

Soy relativamente nuevo usando Windows 10 para programar y esta situación me pareció interesante para escribir al respecto.

## Mi crónica de como intenté solucionar el problema

Primero se me ocurrió buscar como compartir un programa de computadora a todos los usuarios en Windows 10. Llegué a esta entrada del foro de Microsoft titulada [*Windows 10 : ¿Cómo compartir programas en diferentes usuarios de Windows 10?*](https://answers.microsoft.com/es-es/windows/forum/all/windows-10-c%C3%B3mo-compartir-programas-en/66c659cd-52fc-4a51-93af-e5c0cfac1052) pero no solucionó mi problema.

Noté que los programas que se compartían por defecto entre los usuarios estaban instalados en `C:\Program Files` mientras que Visual Studio Code estaba en `C:\Users\Juan MX`. Probé desinstalar vscode e instalarlo en `C:\Program Files` pero me daba un error de que no tenía los permisos para escribir en esa carpeta.

Finalmente se me ocurrió ejecutar el instalador con permisos de administrador para instalar vscode en la carpeta `C:\Program Files`. Me apareció el siguiente mensaje que me ayudó a solucionar mi problema.

<img src='{{ "../assets/vscode-para-todos-los-usuarios/user-installer-as-administrator.png" | absolute_url }}' alt="Mensaje User Instaler ejecutado como administrador" width="450" class="box-shadow" />

Para el caso de que no se pueda ver la imagen, el mensaje dice:

> This User Installer is not meant to run as an Administrator. If you would like to install VS Code for all users in this system, download the System Installer instead from https://code.visualstudio.com. Are you sure you want to continue?

Una traducción propia y no profesional de lo anterior es:

> Este Instalador Para Usuarios no está destinado a ser ejecutado como Administrador. Si deseas instalar VS Code para todos los usuarios en este equipo descarga en su lugar el "*System Instaler*" de https://code.visualstudio.com. ¿Estás seguro de que quieres continuar?

## Solución

Ir a [ https://code.visualstudio.com]( https://code.visualstudio.com){:target="_blank"}.

**1** En la página principal buscar el botón para descargar vscode y dar click en la flecha que está a un lado del botón.

**2** Se abrirá un menú desplegable. Dar click en *Other downloads*.

<img src='{{ "../assets/vscode-para-todos-los-usuarios/other-downloads.png" | absolute_url }}' alt="Seleccionar la opción de Other Downloads"  class="" />

En los descargables para Windows 10 seleccionar "*System Instaler*", en mi caso me bajé el de x64.

<img src='{{ "../assets/vscode-para-todos-los-usuarios/system-instaler.png" | absolute_url }}' alt="Descargar el System Instaler"  class="box-shadow" />