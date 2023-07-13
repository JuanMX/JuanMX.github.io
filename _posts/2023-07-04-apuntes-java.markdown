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

* [Crear un archivo de configuración](#crear-un-archivo-de-configuración)

* [Cambiar el icono de una ventana](#cambiar-el-icono-de-una-ventana)



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

La manera en que yo lo uso es: **Únicamente** en el método `main` poner el tema Nimbus. A las ventanas secundarias (hijas), JOptionPane, JFileChooser y componentes (JButton, JTextField, JScrollPane u otros) se les pondrá el tema automáticamente.

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



<br>
<hr>
<br>



## Crear un archivo de configuración

Para un [proyecto personal de Java](https://github.com/JuanMX/javasimplecrud){:target="_blank"} necesitaba guardar la configuración del usuario. Específicamente el *Look and Feel* que el usuario seleccione.

Un archivo de configuración se puede usar para guardar otras cosas por ejemplo, el idioma preferido o el tema (día ☀️, noche 🌗).

Java cuenta con `java.util.Properties;` usado para crear un archivo de configuración que se maneja como `(clave, valor)`.

Un ejemplo de archivo de configuración es el siguiente:

```
#Fri Jun 30 17:59:36 CST 2023
lookAndFeel=Nimbus
```

### Como yo uso Java Properties

Como nombre de archivo uso `CONFIG.config`.

Para **escribir** (`set`) en el archivo de propiedades hago lo siguiente:

```java
import java.util.Properties;
import java.io.FileInputStream;
import java.io.FileOutputStream;
import java.io.IOException;

import javax.swing.JOptionPane;

public class ConfigManagement {

private static Properties prop = new Properties();
private static final String CONFIG_FILE = "CONFIG.config";

	public void setConfig(String key, String value) {
		
		try{
			
			prop.setProperty(key, value);
			prop.store(new FileOutputStream(CONFIG_FILE), null);
		    
		}catch(IOException e){
			JOptionPane.showMessageDialog( null, "Something went wrong", "Can not save the changes", JOptionPane.ERROR_MESSAGE );
			e.printStackTrace();
		}
	}
}
```

Para **leer** (`get`) del archivo de propiedades hago lo siguiente:

```java
import java.util.Properties;
import java.io.FileInputStream;
import java.io.FileOutputStream;
import java.io.IOException;

import javax.swing.JOptionPane;

public class ConfigManagement {

	private static Properties prop = new Properties();
	private static final  String CONFIG_FILE = "CONFIG.config";
	
	public String getConfig(String key) {
		
		String value = "";
		
		try {
			prop.load(new FileInputStream(CONFIG_FILE));
			value = prop.getProperty(key);
			
		}catch(IOException e) {
			JOptionPane.showMessageDialog( null, "Something went wrong", "Can not read the config file", JOptionPane.ERROR_MESSAGE );
			e.printStackTrace();
		}

		return value;
	}
}

```

[Con confianza pueden ver la clase de Java en la que uso mi propio archivo de configuración.](https://github.com/JuanMX/javasimplecrud/blob/master/javasimplecrud/src/com/juanmx/javasimplecrud/ConfigManagement.java){:target="_blank"} 



<br>
<hr>
<br>



## Cambiar el icono de una ventana

![img]({{ "../assets/apuntes-java/cambiar_icono.png" | absolute_url }})

La clase que crea un JFrame con un icono de ventana distinto es la siguiente:

```java
import javax.swing.JFrame;
import java.awt.Image;
import java.awt.Toolkit;

public class ClaseQueCreaUnJFrame extends JFrame{
	
	public ClaseQueCreaUnJFrame(){
		
		Toolkit myToolkit = Toolkit.getDefaultToolkit();
		Image windowIcon = myToolkit.getImage("./ruta/al/icono.png"); // tal vez acepte otros formatos de imagen, a mi me funciono con .png
		setIconImage(windowIcon);
	}
}
```

La clase con el método `main` que usa la clase anterior es la siguiente:

```java
public class Ejemplo{
	
	public static void main(String[] args) {
			
		ClaseQueCrearaUnJFrame unaVentana = new ClaseQueCrearaUnJFrame();

		unaVentana.setDefaultCloseOperation( JFrame.EXIT_ON_CLOSE );   
		unaVentana.setSize( 800, 600 );
		unaVentana.setVisible( true );
		unaVentana.setLocationRelativeTo( null );
		//aqui tambien se podria usar unaVentana.setIconImage
	}
}
```

**Fuente:** [youtube.com/@pildorasinformaticas &mdash; *Curso Java. Aplicaciones gráficas. Swing III. Colocando el Frame II. Vídeo 57*](https://www.youtube.com/watch?v=zADgVrhtBDs){:target="_blank"}
