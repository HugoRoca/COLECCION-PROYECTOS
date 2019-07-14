---
date: "2019-06-30"
title: "CHAT en tiempo real con NodeJS, Express, BlueBirdJS, Socket.IO y mongoDB"
description: "En este pequeño post te explicaré como crear una aplicación de chat en tiempo real paso a paso. Para entender todo este proceso se requiere que tengas conocimientos en nodeJS, mongoDB, javascript, html5 y css3."
author: "Hugo Roca"
image: /images/post/app-chat-express-socket.io-mongodb-bluebird.svg
imageShared: /images/shared/app-chat-express-socket.io-mongodb-bluebird.jpg
tag:
 - nodejs
 - mongodb
 - JS
---

En este pequeño post te explicaré como crear una aplicación de chat en tiempo real paso a paso. Para entender todo este proceso se requiere que tengas conocimientos en nodeJS, mongoDB, javascript, html5 y css3.

### Instalando paquetes y configuración
Lo primero que tenemos que hacer es crear un directorio en donde estarán todos nuestros archivos, puedes utilizar el editor de código que mas se adecue a tí. En mi caso usaré *VSCode*. 

En la consola ejecutamos la siguiente linea: `npm init` esto quiere decir que estamos iniciando el directorio como una aplicación nodeJS. Se te pedirá que completes algo de información. Esta se utilizará para configurar el archivo *package.json*.

Utilizaremos **express** para crear nuestro servidor web que alojará nuestros archivos estáticos y **body-parser** para extraer todo el cuerpo de una solicitud entrante.

```cmd
npm install express body-parser --save
```

A continuación, instalamos **mongoose**, esto es un ODM (Object Document Mapper) para MongoDB y hará que nuestro trabajo sea mucho más fácil. Vamos a instalarlo junto a **socket.io** y **bluebird**. Para tener algo de contexto de estas dos ultimas; **Socket.io** es una biblioteca de javascript para aplicaciones web en tiempo real. **Bluebird** es una biblioteca Promise con todas las funciones para javascript.

```cmd
npm install mongoose socket.io bluebird --save
```

> Puedes instalar nodemon para no estar iniciando el servidor con cualquier modificación que hagamos, esto es opcional. `npm install nodemon`

Este será nuestro árbol de archivos para esta app.
```
.
├── client
|   ├── css
|   |   └── style.css
|   ├── js
|   |   ├── chat.js
|   |   ├── fortmatTimeStamp.js
|   |   └── socket.io
|   └── index.html      
├── server
|   ├── controllers
|   |   └── chat.js
|   ├── mongoDB
|   |   ├── chatSchema.js
|   |   └── dbconnection.js
|   └── routes
|       └── chat.js
├── app.js
└── package.json
```

### Creando el lado cliente
```html
<!DOCTYPE html>
<html lang="es">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Chat</title>
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css"
        integrity="sha384-ggOyR0iXCbMQv3Xipma34MD+dH/1fQ784/j6cY/iJTQUOhcWr7x9JvoRxT2MZw1T" crossorigin="anonymous">
    <link rel="stylesheet" href="./css/style.css">
</head>

<body>
    <div class="container">
        <div class="row justify-content-md-center mt-3">
            <div class="col-md-7">
                <div class="card">
                    <div class="card-header">
                        <h4 class="text-center">CHAT</h4>
                    </div>
                    <div class="card-body">
                        <ul class="chat" id="listaMensajes">

                        </ul>
                    </div>
                    <div class="card-footer">
                        <small id="escribiendo">&nbsp;</small>
                        <form id="form">
                            <div class="input-group">
                                <input id="mensaje" type="text" class="form-control"
                                    placeholder="Escribe tu mensaje aquí..." autocomplete="off" />
                                <span class="input-group-append">
                                    <button class="btn btn-warning" id="btn-chat">Enviar</button>
                                </span>
                            </div>
                        </form>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.4.1/jquery.min.js"></script>
    <script src="./js/formatTimeStamp.js"></script>
    <script src="./js/socket.io.js"></script>
    <script src="./js/chat.js"></script>
</body>

</html>
```

Este será nuestro archivo HTML que servirá para la interfaz, para instanciar socket.io en el cliente, puedes obtener el código haciendo click [aquí](https://github.com/socketio/socket.io-client/blob/master/dist/socket.io.js).

> formatTimeStamp.js nos servirá para obtener el momento en que se envio el mensaje, si fue hoy, ayer o la semana pasada. Puedes obtener el código dando click [aquí](https://cdn.jsdelivr.net/gh/rexeze/formatTimeStamp/src/index-cdn.js).

Antes de configurar el archivo **chat.js** debemos de centrarnos en el desarrollo del backend.

### Creando el lado servidor
