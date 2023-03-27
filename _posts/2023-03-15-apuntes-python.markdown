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

* [requirements.txt](#requirementstxt)

* [archivos .env y .env.example](#archivos-env-y-envexample)

* [Python en Laragon](#python-en-laragon)



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

Abrir una terminal y posicionarla en la carpeta del env creado. Después escribir.

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


**Fuente:** [docs.python.org/es &mdash; *Entornos virtuales y paquetes*](https://docs.python.org/es/3/tutorial/venv.html){:target="_blank"}



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



<br>
<hr>
<br>



## requirements.txt

El archivo `requirements.txt` contiene una lista de librerías para instalar usando `pip`.

```
pip install -r requirements.txt
```

El archivo es parecido al siguiente.

```
fastapi==0.66.1
uvicorn==0.14.0
tensorflow-cpu==2.5.0
```


## Crear requirements.txt con pip freeze

```
pip freeze > requirements.txt
```

## Consejos para requirements.txt

<mark>1</mark> 

Se aconseja que el archivo siempre se llame *requirements.txt*.

<mark>2</mark> 

Es recomendado crear el archivo manualmente sin usar `freeze > requirements.txt`.

La manera de hacerlo es usar `pip freeze` y ver la salida, después agregar manualmente las dependencias.

Ejemplo, si en un `env` recién hecho se usa `pip install tensorflow` y después `pip freeze > requirements.txt` mostrará tensorflow junto con muchas otras dependencias.

Lo que se aconseja hacer es, usar `pip freeze`, ubicar tensorflow, crear el archivo requirements.txt y agregar manualmente tensorflow.

<mark>3</mark> 

Es posible agregar cosas poco comunes desde este archivo.

Ejemplo, para **spacy y un modelo entrenado de reconocimiento de entidades multilenguaje** el archivo requirements.txt se ve como:

```
spacy==3.1.2
xx-ent-wiki-sm @ https://github.com/explosion/spacy-models/releases/download/xx_ent_wiki_sm-3.1.0/xx_ent_wiki_sm-3.1.0-py3-none-any.whl
```

<mark>4</mark> 

Para desplegar a producción un proyecto de Python en un servicio en la nube como Heroku, **si se tienen problemas con las dependencias** se sugiere agregar a requirements.txt las versiones de pip, wheel y setuptools usadas en el desarrollo.

**Fuentes** 

Información de requirements.txt: [pip.pypa.io &mdash; *Requirements Files*](https://pip.pypa.io/en/stable/user_guide/#requirements-files){:target="_blank"}

Información de pip freeze: [pip.pypa.io &mdash; *pip freeze*](https://pip.pypa.io/en/stable/cli/pip_freeze/#pip-freeze){:target="_blank"}



<br>
<hr>
<br>



## Archivos .env y .env.example

De manera conceptual, un archivo `.env` contiene variables de gran importancia que se pueden acceder desde cualquier parte de un proyecto de desarrollo.

Un archivo `.env` se genera de un archivo `.env.example` que contiene las variables *vacías* o con indicaciones de su contenido.

En Laravel, por ejemplo, estos archivos se ven así:

![img]({{ "../assets/apuntes-python/env-envexample.PNG" | absolute_url }})

No se recomienda subir a un repositorio el archivo `.env` sólo el `.env.example`. Cada vez que se clone el proyecto del repositorio se debe generar un nuevo `.env` a partir de `.env.example`.

## La manera en que yo uso un .env en Python

Se necesita [python-dotenv](https://pypi.org/project/python-dotenv/){:target="_blank"}.

Lo siguiente es el contenido de un `.env` de ejemplo:

```
MY_APP_NAME="Un nombre de ejemplo"
```

Lo siguiente es código de Python que usa el `.env` anterior:

```python
from dotenv import load_dotenv
import os

load_dotenv()

def get_env(env_variable):
    return os.environ.get(env_variable)

get_env("MY_APP_NAME") # Obtiene "Un nombre de ejemplo" del archivo .env
```





<br>
<hr>
<br>



## Python en Laragon

[*Laragon provee un moderno y poderoso entorno de desarrollo que incontables personas aman y usan cada día.*](https://laragon.org/about/){:target="_blank"}

En palabras propias y usando terminos de Python: Es como un [env](#env) de Python para diferentes desarrollos, por ejemplo, diferentes versiones del *framework* de Laravel. Donde cada uno está separado. Lo que permite desarrollar con distinas versiones del *framework* con sus dependencias sin que se *estorben* entre éstas.

Yo tenía entendido que Laragon era únicamente para Laravel pero en [versiones recientes](https://laragon.org/download/index.html){:target="_blank"} han añadido mediante  ***Quick add*** frameworks y lenguajes de programación, entre ellos Python.

A veces se necesita una versión en particular de Python, que difiere de la proveída por Laragon, por ejemplo, [para FastAPI se necesita Python 3.7+](https://fastapi.tiangolo.com/#requirements){:target="_blank"}. Y en mi caso la versión de Python proveída era 3.6.1.

En este caso se necesita cambiar la versión de Python en Laragon para usar FastAPI.

La explicación corta para lograrlo es: Instalar Python en modo personalizado en la carpeta `bin\python\` de Laragon en lugar de `C:\Archivos de Programa\`.

La explicación larga se muestra a continuación.

## Cambiar la versión de Python en Laragon

**Se usan imágenes del sitio https://programmerclick.com/article/12232400613/**

Ir a [python.org/downloads/](https://www.python.org/downloads/){:target="_blank"} y descargar alguna versión, en micaso, la 3.9.10.

Dar doble click para iniciar el instalador, desmarcar los *checkbox* de:

* [ ] *Install launcher for all users* 
* [ ] *Add PYthon to PATH*.

Después dar click en *Customize installation*.

![img]({{ "https://images2.programmerclick.com/414/81/8137952de1ef61fd36c67610d5f3fb36.png" }})

Desmarcar los *checkbox* de:

* [ ] *tcl/tk and IDLE* 
* [ ] *py launcher*.

Después dar click en *Next*

![img]({{ "https://images3.programmerclick.com/738/8a/8a2858be5b3290d5e8455addbb676f92.png" }})

En la ruta de instalación se debe poner la ruta `bin\python\` de Laragon. En mi caso es `C:\laragon\bin\python\python-3.9.10`. Para otra versión de Python cambiará, ejemplo `bin\python\python-3.8.1`.

![img]({{ "../assets/apuntes-python/laragon-bin-python.PNG" | absolute_url }})

Finalmente se debe hacer click en *Install* para empezar la instalación. Al finalizar la instalación cerrar la ventana.

Para escoger que versión de Python usar en Laragon yo lo que hago es.

Click derecho -> Python -> Version -> Python 3.9.10.

![img]({{ "../assets/apuntes-python/laragon-python-version.png" | absolute_url }})



**Fuente:** [programmerclick.com &mdash; *Añadir una nueva versión de Python en Laragon*](https://programmerclick.com/article/12232400613/){:target="_blank"} 
