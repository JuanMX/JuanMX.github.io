---
layout: post
title:  "Apuntes: Java"
date:   2023-07-04 17:00:00 -0500
categories: java swing
---

No tengo ni trabajo ni nada. En lo que se presenta alguna oportunidad se me ocurrió trabajar sobre mis viejos [proyectos de Java](https://github.com/JuanMX?tab=repositories&q=&type=&language=java&sort=){:target="_blank"} para tener la mente fresca en relación a la programación.

Aquí hay apuntes de *Java puro*.

## Obtener la altura y anchura de la pantalla

```java
import java.awt.Dimension;
import java.awt.Toolkit;

public class UnaClase {

	public static void main(String[] args) {

		Toolkit pantalla = Toolkit.getDefaultToolkit();
		Dimension tamanoPantalla = pantalla.getScreenSize();

		int ancho = tamanoPantalla.width;
		int alto = tamanoPantalla.height;
	}
}
```