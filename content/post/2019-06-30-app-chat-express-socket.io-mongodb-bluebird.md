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