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

**Fuente:** [pypi.org &mdash; *python-dotenv*](https://pypi.org/project/python-dotenv/){:target="_blank"} 