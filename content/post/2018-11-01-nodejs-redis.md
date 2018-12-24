---
date: "2018-11-01"
title: "Conexión NodeJS con Redis Cache"
description: "D3.js es una biblioteca de JavaScript para manipular documentos basados ​​en datos. D3 te ayuda a dar vida a los datos usando HTML, SVG y CSS."
author: "Hugo Roca"
image: /images/post/nodejs-redis.svg
imageShared: /images/shared/nodejs-redis.jpg
tags:
 - JS
 - REDIS
categories:
 - JavaScript
---

### Requisitos
- NodeJS (https://nodejs.org/es/)
- Redis (https://redis.io/)
- NPM (https://www.npmjs.com/)

----
### Creando el Package.json
Antes de proceder con cualquier instalación de paquetes npm necesitamos crear nuestro package.json.

- Como primer paso creamos una carpeta donde estarán todos nuestros archivos.
- Luego, levantar la ventana de comandos dentro de la carpeta y ejecutar el siguiente comando `npm init`.
- Podemos personalizar o simplemente precionar la tecla enter hasta terminar.

Al finalizar tendremos un archivo como este:
```
{
  "name": "nodejs-redis-conecction",
  "version": "1.0.0",
  "description": "Connection nodejs with redis for querys",
  "main": "",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "Hugo Roca - hugo.rock20@hotmail.com",
  "license": "MIT"
}
```
----
### Instalando npm Redis
Para este caso utilizaremos al paquete IORedis (https://www.npmjs.com/package/ioredis), en la consola de comandos copiamos y pegamos lo siquiente: `npm i ioredis`, una ves terminado se creará una carpeta por defecto `node_modules`, en donde se guardan todas las dependencias.

### Creando la conexión
