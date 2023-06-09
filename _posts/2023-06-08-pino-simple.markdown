---
layout: post
title:  "[Demo] El simple y básico programita que dibuja un pino"
date:   2023-06-08 17:00:00 -0500
categories: html, javascript
---

<script>

    let nivelesPino = parseInt(prompt("Niveles del pino"));
    let hojaDePino = "o";

    if (!Number.isInteger(nivelesPino) || nivelesPino <= 0 ){

        document.write("La entrada no es correcta.");
    }
    else{

        if (nivelesPino == 1){

            document.write("&nbsp;&nbsp;" + hojaDePino);
            document.write("<br>");

            document.write("<br>");
            document.write("El pino tiene " + nivelesPino + " nivel.");
        }
        else{
            
            for(let nivel = 1, niveli=nivelesPino; nivel <= nivelesPino; nivel++, niveli--){
                
                hojasNivelPino = (2*nivel)-1;
                espaciosNivelPino = niveli-1;

                for(let espacio = 0; espacio<espaciosNivelPino; espacio++){
                    document.write("&nbsp;&nbsp;");
                }
                
                for(let hoja = 0; hoja<hojasNivelPino; hoja++){
                    document.write(hojaDePino);
                }
                document.write("<br>");
            }
            document.write("<br>");
            document.write("El pino tiene " + nivelesPino + " niveles.");
            
        }
    }
    document.write("<br>");
    document.write("El gist de este programita se encuentra <a href='https://gist.github.com/JuanMX/bb95725d170c09184ba37d9781bc4478' target='_blank'>aquí.</a>");
    document.write("<br>");
    document.write("Para volver a empezar recarga la página.");
</script>