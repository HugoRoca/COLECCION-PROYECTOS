---
date: "2018-11-01"
title: "Conexión NodeJS con Redis Cache"
description: "Redis se utiliza como base de datos y para caché, ya que es súper rápido debido a que los datos se almacenan 'en memoria', a diferencia de otras bases de datos en las que los datos generalmente se almacenan 'en disco'."
author: "Hugo Roca"
image: /images/post/nodejs-redis.svg
imageShared: /images/shared/nodejs-redis.jpg
tags:
 - JS
 - REDIS
categories:
 - JavaScript
---
> Redis se utiliza como base de datos y para caché, ya que es súper rápido debido a que los datos se almacenan "en memoria", a diferencia de otras bases de datos en las que los datos generalmente se almacenan "en disco".

Redis es una gran base de datos para usar con Node.js. Tanto Redis como Node.js comparten convenciones de tipo y modelos de subprocesos similares, lo que lo convierte en una experiencia de desarrollo muy predecible. Al asociar Node.js y Redis, puede lograr una plataforma de desarrollo escalable y productiva.   

### Requisitos
- NodeJS (https://nodejs.org/es/)
- Redis (https://redis.io/)
- NPM (https://www.npmjs.com/)

----
### Instalación de Redis en windows
Para obtener Redis da click al siguiente enlace: https://github.com/dmajkic/redis/downloads

----
### Creando el Package.json
Antes de proceder con cualquier instalación de paquetes npm necesitamos crear nuestro package.json.

- Como primer paso creamos una carpeta donde estarán todos nuestros archivos.
- Luego, levantar la ventana de comandos dentro de la carpeta y ejecutar el siguiente comando `npm init`.
- Podemos personalizar o simplemente precionar la tecla enter hasta terminar.

Al finalizar tendremos un archivo como este:

<script src="https://gist.github.com/HugoRoca/8997425b507e737ddc2b395cd04491a6.js"></script>

----
### Instalando npm Redis
Para este caso utilizaremos al paquete IORedis (https://www.npmjs.com/package/ioredis), en la consola de comandos copiamos y pegamos lo siquiente: `npm i ioredis`, una ves terminado se creará una carpeta por defecto `node_modules`, en donde se guardan todas las dependencias.

----
### Creando la conexión (get, set)
Empezaremos creando un archivo de configuración (config.js) en donde estará las credenciales y otras cosas:
<script src="https://gist.github.com/HugoRoca/598080014996016233d3db17831e996c.js"></script>

Luego, empezamos a crear la conexión, para esta ocación haremos uso de ES6, el nuevo archivo tendra el nombre de "redis-connection.js", adicional a esto agregaremos dos métodos más que serían asincronos, uno para obtener y el otro para asignar.
<script src="https://gist.github.com/HugoRoca/bd8ea1b88ad9d8628d4e3a9a699be60e.js"></script>

Creamos el siguiente archivo "redisSet.js" en donde se codificará una función autoejecutala asincrona instanciando al objeto "redis-connection.js".
<script src="https://gist.github.com/HugoRoca/75570f290bc894011c307a497c07a52b.js"></script>

Hacemos lo mismo que el código de arriba, pero esta vez vamos a obtener lo registrado. Este nuevo archivo tendrá de nombre "redisGet.js".
<script src="https://gist.github.com/HugoRoca/4d0bb973312967393e3a1eeda675d106.js"></script>

### Ejecutando lo codificado
- Para ejecutar solo hay que tener levantado el Redis.
- Ejecutar la siguiente línea `node redisSet.js` en la consola
    - Esto registrará en redis el JSON.
- Para obtener lo registrado ejecutar la siguiente línea `node redisGet.js`
    - Esto retornará el JSON registrado pero en formato STRING, simplemente formateamos a json(`JSON.parse()`) y listo!

> Para obtener el código completo dar click [aquí](https://github.com/PORTAFOLIO-PROYECTOS/NODE_JS_REDIS_CACHE/archive/master.zip)
#### Comenta, disfruta y comparte! 