---
layout: post
title:  "Apuntes: Heroku - Python - FastApi"
date:   2022-02-26 12:26:00 -0500
---   

En este post supone que se usa Heroku CLI.

## Renombrar un remoto

Renombrar el remoto de `heroku` a `heroku-staging`

```
git remote rename heroku heroku-staging
```

**Fuente:** [devcenter.heroku.com/articles &mdash; *Rename a Remote*](https://devcenter.heroku.com/articles/git#rename-a-remote){:target="_blank"}

<br>
<hr>
<br>

## Realizar el deploy de una subcarpeta

Logearse a heroku con `heroku login`.

Agregar el remoto si no esta agreagdo `heroku git:remote -a my-app`.

Pushear la subcarpeta

```
git subtree push --prefix NOMBRE_SUBDIRECTORIO heroku master
```

**Fuente:** [janessagarrow.com &mdash; *How to Deploy a Subdirectory to Heroku*](https://janessagarrow.com/blog/how-to-deploy-a-subdirectory-to-heroku/){:target="_blank"}

<br>
<hr>
<br>

## Archivo de configuración Procfile para FastApi en Heroku

Se necesita un archivo de configuración llamado `Procfile` que no lleva extención de archivo.

Su conenido se muestra a continuación.

```
======= Procfile =======

web: uvicorn main:app --host=0.0.0.0 --port=${PORT:-5000}
```

donde:
* `main` es el nombre del archivo principal de tu proyecto de FastApi.
* `app` es el nombre de la variable de FastApi en `main` ( `app = FastAPI()` ).

**Fuente:** [youtube.com &mdash; *Desplegando (Deploy) una aplicación FastAPI en Heroku.*](https://www.youtube.com/watch?v=4hS0YOZD-g4){:target="_blank"}

<br>
<hr>
<br>

## Archivo de configuración requirements.txt para FastApi en Heroku

Heroku reconocerá que la app es de Python si incluye un archivo `requirements.txt` en el directorio raíz del proyecto.

El archivo `requirements.txt` contiene una lista de elementos que se instalarán usando 

```
pip install -r requirements.txt
```

Una manera rápida de crear este archivo es con la instrucción

```
pip freeze > requirements.txt
```

Como consejo personal, si es un proyecto pequeño que incluye tensorflow en conveniente usar la versión cpu para no rebasar el limite de 500MB que brinda Heroku en su plan gratuito. Un ejemplo se muestra a continuación.

```
======= requirements.txt =======

fastapi==0.66.1
uvicorn==0.14.0
tensorflow-cpu==2.5.0
```

**Fuentes:** 

`requirements.txt` en Heroku: [devcenter.heroku.com/articles &mdash; *Recognizing a Python app*](https://devcenter.heroku.com/articles/python-support#recognizing-a-python-app){:target="_blank"}

Información  sobre `requirements.txt`: [pip.pypa.io &mdash; *Requirements Files*](https://pip.pypa.io/en/stable/user_guide/#requirements-files){:target="_blank"}