---
layout: post
title:  "Instalar Visual Studio Code para todos los usuarios en Windows 10"
date:   2024-05-27 18:00:00 -0500
categories: vscode windows10
---

En mi computadora tengo un usuario llamado *Juan MX*. Es muy común que tenga problemas con programas de computadora porque el nombre de usuario genera una carpeta con espacio en blanco tipo `C:\Users\Juan MX`. Me parece que ese espacio en blanco *rompe* las rutas absolutas hacia archivos y carpetas, causando problemas con algunos programas.

Harto de tener este problema me hice un usuario local con permisos de administrador y sin espacios en blanco como *JuanMX*. Creí que tendría acceso a todos los programas instalados, pero noté que no podia usar Visual Studio Code (vscode), uno de los programas más importantes para mí.

Soy relativamente nuevo usando Windows 10 para programar y esta situación me pareció interesante para escribir al respecto.

## Mi crónica de como intenté solucionar el problema

Primero se me ocurrió buscar como compartir un programa de computadora a todos los usuarios en Windows 10. Llegué a esta entrada del foro de Microsoft titulada [*Windows 10 : ¿Cómo compartir programas en diferentes usuarios de Windows 10?*](https://answers.microsoft.com/es-es/windows/forum/all/windows-10-c%C3%B3mo-compartir-programas-en/66c659cd-52fc-4a51-93af-e5c0cfac1052){:target="_blank"} pero no solucionó mi problema.

Revisando en mi PC noté que los programas que se compartían por defecto entre los usuarios estaban instalados en `C:\Program Files` mientras que Visual Studio Code estaba en `C:\Users\Juan MX`. Probé desinstalar vscode e instalarlo en `C:\Program Files` pero me daba un error de que no tenía los permisos para escribir en esa carpeta.

Finalmente se me ocurrió ejecutar el instalador con permisos de administrador para instalar vscode en la carpeta `C:\Program Files`. Me apareció el siguiente mensaje que me ayudó a solucionar mi problema.

<img src='{{ "../assets/vscode-para-todos-los-usuarios/user-installer-as-administrator.png" | absolute_url }}' alt="Mensaje del User Installer ejecutado como administrador" class="box-shadow" />

Para el caso de que no se pueda ver la imagen, el mensaje dice:

> This User Installer is not meant to run as an Administrator. If you would like to install VS Code for all users in this system, download the System Installer instead from https://code.visualstudio.com. Are you sure you want to continue?

Una traducción propia, adaptada y no profesional de lo anterior es:

> Este "*User Installer*" no está destinado a ser ejecutado como Administrador. Si deseas instalar VS Code para todos los usuarios en este equipo mejor descarga el "*System Installer*" de https://code.visualstudio.com. ¿Estás seguro de que quieres continuar?

## Solución

Ir a [https://code.visualstudio.com]( https://code.visualstudio.com){:target="_blank"}.

**1** En la página principal buscar el botón para descargar vscode y dar click en la flecha que está a un lado del botón.

**2** Se abrirá un menú desplegable. Dar click en *Other downloads*.

<img src='{{ "../assets/vscode-para-todos-los-usuarios/other-downloads.png" | absolute_url }}' alt="Seleccionar la opción de Other Downloads"  class="" />

En los descargables para Windows 10 seleccionar "*System Installer*", en mi caso me bajé el de *x64*.

<img src='{{ "../assets/vscode-para-todos-los-usuarios/system-instaler.png" | absolute_url }}' alt="Descargar el System Installer"  class="box-shadow" />

<br>

<div style="background: #cff4fc;padding: 20px;">
    <p>
        El "System Installer" permitirá instalar Visual Studio Code para todos los usuarios en el equipo. Sugiero instalarlo en la carpeta <code>C:\Program Files</code>.
    </p>
</div>





<br>
<hr>
<br>



## Actualización Febrero 2026

Siendo consumidor de mi propio contenido noté que están un poco desactualizadas las instrucciones anteriores.

## Ir a la sección de ***descargas*** de Visual Studio Code desde su página de inicio

**Paso 1.** Ir a [https://code.visualstudio.com]( https://code.visualstudio.com){:target="_blank"}.

**Paso 2.** Ubicar un botón que dice *Download for Windows* y **debajo** de él se verán tres opciones: *Web*, *Insiders edition* y *Other platforms*.

**Paso 3.** Dar click en *Other platforms*.

**Paso 4.** Después de dar click en **Other platforms** redirigirá a [https://code.visualstudio.com/Download]( https://code.visualstudio.com/Download){:target="_blank"} seleccionar para descargar el *System Installer* para Windows10.

Las siguientes imágenes muestran mejor que hacer.

<img src='{{ "../assets/vscode-para-todos-los-usuarios/other-downloads-febrero-2026.png" | absolute_url }}' alt="Seleccionar la opción Other platforms"  class="" />

<img src='{{ "../assets/vscode-para-todos-los-usuarios/system-instaler-febrero-2026.png" | absolute_url }}' alt="Descargar el System Installer"  class="" />