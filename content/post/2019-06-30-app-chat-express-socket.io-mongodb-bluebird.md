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

```js
npm install express body-parser --save
```