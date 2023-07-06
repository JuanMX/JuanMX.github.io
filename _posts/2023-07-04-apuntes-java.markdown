---
layout: post
title:  "Apuntes: Java"
date:   2023-07-04 17:00:00 -0500
categories: java swing
---

No tengo ni trabajo ni nada. En lo que se presenta alguna oportunidad se me ocurrió trabajar sobre mis viejos [proyectos de Java](https://github.com/JuanMX?tab=repositories&q=&type=&language=java&sort=){:target="_blank"} para tener la mente fresca en relación a la programación.

Aquí hay apuntes de *Java puro*.

## Contenido

* [Obtener la altura y anchura de la pantalla](#obtener-la-altura-y-anchura-de-la-pantalla)
* [Usar el tema Nimbus en una GUI de Java](#usar-el-tema-nimbus-en-una-gui-de-java)



<br>
<hr>
<br>



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

**Fuente:** [youtube.com/@pildorasinformaticas &mdash; *Curso Java. Aplicaciones gráficas. Swing III. Colocando el Frame II. Vídeo 57*](https://www.youtube.com/watch?v=zADgVrhtBDs){:target="_blank"}



<br>
<hr>
<br>



## Usar el tema Nimbus en una GUI de Java

![oraclenimbusdemo](https://docs.oracle.com/javase/tutorial/figures/uiswing/lookandfeel/nimbus.png)

La manera en que yo lo uso es: **Únicamente** en el método `main` poner el tema Nimbus. A las ventanas secundarias (hijas) se les pondrá el tema automáticamente.

```java
import javax.swing.UIManager.*;

public class EstaEsUnaClase {

	public static void main(String[] args) {

		try {

			for (LookAndFeelInfo info : UIManager.getInstalledLookAndFeels()) {

				if ("Nimbus".equals(info.getName())) {

					UIManager.setLookAndFeel(info.getClassName());
					break;
				}
			}
		} catch (Exception e) {
			// If Nimbus is not available, you can set the GUI to another look and feel.
			//e.printStackTrace();
		}

		/**
		 * Sigue con tu código.
		 */
	}
}
```

De acuerdo con la documentación de Oracle, Nimbus es multiplataforma y fue añadido en la versión 6 actualización 10 de Java (*Java SE 6 Update 10 (6u10) release*).

**Fuente:** [docs.oracle.com/javase/tutorial/ &mdash; *Nimbus Look and Feel*](https://docs.oracle.com/javase/tutorial/uiswing/lookandfeel/nimbus.html){:target="_blank"}