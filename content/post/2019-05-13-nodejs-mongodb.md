---
date: "2019-05-13"
title: "Conexión NodeJS con MongoDB Atlas"
description: "MongoDB Atlas es la base de datos como servicio que permite implementar, utilizar y escalar una base de datos de MongoDB en la nube haciendo conexión con NodeJS."
author: "Hugo Roca"
image: /images/post/portafolio.svg
imageShared: /images/shared/portafolio.jpg
tag:
 - JavaScript
 - JS
 - mongodb
 - base de datos
---

MongoDB Atlas es la base de datos como servicio que permite implementar, utilizar y escalar una base de datos de MongoDB en la nube haciendo conexión con NodeJS.

Usaremos clases y funcion asincronas con promesas en javascript ES6.

### Creando el Package.json
Antes de proceder con cualquier instalación de paquetes npm necesitamos crear nuestro package.json.

- Como primer paso creamos una carpeta donde estarán todos nuestros archivos.
- Luego, levantar la ventana de comandos dentro de la carpeta y ejecutar el siguiente comando `npm init`.
- Podemos personalizar o simplemente precionar la tecla enter hasta terminar.

Al finalizar tendremos un archivo como este:

```
{
  "name": "[nombre]",
  "version": "[versión]",
  "description": "[descripción]",
  "main": "",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "Hugo Roca - hugo.rock20@hotmail.com",
  "license": "[licencia]"
}
```

----
### Instalando npm mongodb
Para este caso utilizaremos al paquete mongodb (https://www.npmjs.com/package/mongodb), en la consola de comandos copiamos y pegamos lo siquiente: `npm i mongodb`, una ves terminado se creará una carpeta por defecto `node_modules`, en donde se guardan todas las dependencias.

