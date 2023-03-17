---
layout: post
title:  "Apuntes: Python"
date:   2023-03-15 20:00:00 -0500
categories: python
---

Mi *sabiduría de calle* del Python.

## Contenido

* [env](#env)

* [pip, wheel y setuptools](#pip-wheel-y-setuptools)

* [requirements.txt](#requirements.txt)

* [archivos env y envexample](#archivos-env-y-envexample)

* [Cambiar la versión de Python en Laragon](#cambiarcla-version-de-python-en-laragon)



<br>
<hr>
<br>



## env

Un entorno virtual (env) es un directorio que contiene una instalación de Python de una versión en particular, además de unos cuantos paquetes adicionales.

Diferentes aplicaciones pueden usar entornos virtuales diferentes con diferentes versiones de dependencias. Lo que, para desarrollo, ayuda a solucionar el problema de compatibilidad de dependencias.

Personalmente me resistía a usar los `env`, pensé que para usarlos se tenia que instalar algo extra por ejemplo *Conda* o *Jupyter*. Pero no, los `env` están incluidos en Python. 

## Crear un env

Abrir una terminal y posicionarla en el directorio donde se creará el `env`, después escribir.

```
python -m venv tutorial-env
```

Si se tiene Python2 y Python3 se debe escribir para Python3

```
python3 -m venv tutorial-env
```

## Activar un env

Abrir una terminal y posicionarla en la careta del env creado. Después escribir.

En Windows:

```
tutorial-env\Scripts\activate.bat
```

En Ubuntu y similares:

```
source tutorial-env/bin/activate
```

## Desactivar un env

Escribir lo siguiente o cerrar la terminal.

```
deactivate
```

## Eliminar un env

**Sólo se debe eliminar la carpeta.**


**Fuente:** [docs.python.org &mdash; *Entornos virtuales y paquetes*](https://docs.python.org/es/3/tutorial/venv.html){:target="_blank"}



<br>
<hr>
<br>



## pip, wheel y setuptools

Para librerías modernas de Python es muy común que al instalarlas con `pip` muestre un error con `CPython` o algún otro.

De manera conceptual, para instalar una librería reciente se debe tener `pip` actualizado. Lo mismo aplica para `wheel` y `setuptools`.

Tener actualizados `pip`, `wheel` y `setuptools` evitará errores al instalar librerías.

## Actualizar pip, wheel y setuptools

Abrir una terminal, si esto se hará en un entorno virtual activarlo.

Escribir lo siguiente:

```
pip install -U pip setuptools wheel
```

No parace muy intuitivo usar `pip` para instalar `pip` pero en casi todas las veces lo que hará es actualizarlo a su versión más reciente.

**Fuente:** [spacy.io &mdash; *pip*](https://spacy.io/usage#pip){:target="_blank"} 