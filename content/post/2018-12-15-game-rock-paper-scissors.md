---
date: "2018-12-15"
title: "Creación de un juego con JavaScript puro N° 1"
description: "En esta oportunidad crearemos un juego del clásico piedra, papel o tijeras. Utilizaremos JavaScript puro y HTML5 y CSS3 para el diseño."
author: "Hugo Roca"
image: /images/post/juego-piedra-papel-tijeras.svg
imageShared: /images/shared/juego-piedra-papel-tijeras.jpg
tags:
 - JS
categories:
 - JavaScript
---
> En esta oportunidad crearemos un juego del clásico piedra, papel o tijeras. Utilizaremos JavaScript puro y HTML5 y CSS3 para el diseño.

#### El diseño final del juego es el siguiente:
![](https://i.ibb.co/306TGPz/Captura.png)

### Recursos (Imagenes)
- [Puño](https://www.significadoemojis.es/img/emojis-es/puno-alto-whatsapp-270A.png)
- [Mano](https://www.significadoemojis.es/img/emojis-es/mano-levantada-whatsapp-270B.png)
- [Tijera](https://www.significadoemojis.es/img/emojis-es/mano-victoria-whatsapp-270C.png)

----

## Paso 1 (Estructura del diseño)
Empezaremos creando el archivo `index.html` y codificamos lo siguiente:
<script src="https://gist.github.com/HugoRoca/fe41000f0b4c632a504660fb8c026be7.js"></script>

----
## Paso 2 (Estilos)
Crearemos una carpeta "css" para llevar un orden y no tener los archivos sueltos. Dentro de la carpeta agregar un archivo `style.css` y codificar lo siguiente:
<script src="https://gist.github.com/HugoRoca/e6a806ce99d15889c20ac9f5919876f5.js"></script>

----
## Paso 3 (funcionalidad)
Luego, agregamos una carpeta a la cual llamaremos "js" que es en donde se crearán los archivos javaScript, el primer archivo que crearemos sera `utils.js". En este archivo estarán todos los recursos que reutilizaremos.
<script src="https://gist.github.com/HugoRoca/fb8f1ebf90cc501fe9ffaf3bcae97086.js"></script>

Agregar archivo `game.js`, aquí estará la funcionalidad general del juego.
<script src="https://gist.github.com/HugoRoca/0b59031305017d28929096716b66e95f.js"></script>

Y para terminar, agregaremos un archivo `app.js`, aquí crearemos un funcion autoejecutable:
<script src="https://gist.github.com/HugoRoca/400e23f5de176ef6099794d884eb0601.js"></script>

Para probar el resultado final, no esta de más decir que solo hay que dar doble click a `index.html` y listo!

### Creditos 
- whatsdev [(YouTube)](https://www.youtube.com/channel/UC0tRdbXVDbhaRvZPKsRgmxg)

> Para obtener el código completo dar click [aquí.](https://github.com/PORTAFOLIO-PROYECTOS/JAVASCRIPT-GAME-ROCK-PAPER-SCISSORS/archive/master.zip)

#### Comenta, disfruta y comparte! 