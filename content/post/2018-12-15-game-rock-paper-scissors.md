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

```
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <link rel="stylesheet" href="css/style.css">
    <title>Rock Paper Scissors Game</title>
</head>
<body>
    <header>
        <h1>Rock Paper Scissors</h1>  
    </header>

    <div class="score-board">
        <div id="user-label" class="badge">user</div>
        <div id="computer-label" class="badge">comp</div>
        <span id="user-score">0</span>&nbsp;:&nbsp;<span id="computer-score">0</span>
    </div>

    <div class="result">
        <p>Paper covers rock. You win!</p>
    </div>

    <div class="choices">
        <div class="choice" id="r">
            <img src="images/rock.png" alt="">
        </div>
        <div class="choice" id="p">
            <img src="images/paper.png" alt="">
        </div>
        <div class="choice" id="s">
            <img src="images/scissors.png" alt="">
        </div>
    </div>

    <p id="action-message">Make your move</p>

    <script src="js/util.js"></script>
    <script src="js/game.js"></script>
    <script src="js/app.js"></script>
</body>
</html>
```

----
## Paso 2 (Estilos)
Para 


Luego, agregamos una carpeta a la cual llamaremos "js" que es en donde se crearán los archivos javaScript, el primer archivo que crearemos sera `utils.js". En este archivo estarán todos los recursos que reutilizaremos.
```
"use strict";

class Utils {
    getElement(value) {
        return document.getElementById(value);
    }

    getQuerySelector(value) {
        return document.querySelector(value);
    }

    getComputerChoice() {
        const choices = ["r", "p", "s"];
        const randonNumber = Math.floor(Math.random() * 3);
        return choices[randonNumber];
    }

    convertToWord(letter) {
        if (letter === "r") return "Rock";
        if (letter === "p") return "Paper";
        return "Scissors"
    }

    addClassEffect(choice, _class) {
        const etiq = this.getElement(choice);
        etiq.classList.add(_class);
        setTimeout(() => {
            etiq.classList.remove(_class);
        }, 300);
    }
}
```