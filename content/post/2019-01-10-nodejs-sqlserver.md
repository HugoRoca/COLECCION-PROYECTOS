---
date: "2019-01-10"
title: "Conexión NodeJS con SQLServer"
description: "Microsoft SQL Server es un sistema de gestión de base de datos relacional (RDBMS) producido por Microsoft. Su principal lenguaje de consulta es Transact-SQL, una aplicación de las normas ANSI / ISO estándar Structured Query Language (SQL) utilizado por ambas Microsoft y Sybase."
author: "Hugo Roca"
image: /images/post/nodejs-sqlserver.svg
imageShared: /images/shared/nodejs-sqlserver.jpg
tags:
 - JS
 - SQLSERVER
categories:
 - JavaScript
---
> Microsoft SQL Server es un sistema de gestión de base de datos relacional (RDBMS) producido por Microsoft. Su principal lenguaje de consulta es Transact-SQL, una aplicación de las normas ANSI / ISO estándar Structured Query Language (SQL) utilizado por ambas Microsoft y Sybase.

Usaremos clases y funcion asincronas con promesas en javascript ES6.

### Creando el Package.json
Antes de proceder con cualquier instalación de paquetes npm necesitamos crear nuestro package.json.

- Como primer paso creamos una carpeta donde estarán todos nuestros archivos.
- Luego, levantar la ventana de comandos dentro de la carpeta y ejecutar el siguiente comando `npm init`.
- Podemos personalizar o simplemente precionar la tecla enter hasta terminar.

Al finalizar tendremos un archivo como este:

<script src="https://gist.github.com/HugoRoca/8997425b507e737ddc2b395cd04491a6.js"></script>

----
### Instalando npm mssql
Para este caso utilizaremos al paquete mssql (https://www.npmjs.com/package/mssql), en la consola de comandos copiamos y pegamos lo siquiente: `npm i mssql`, una ves terminado se creará una carpeta por defecto `node_modules`, en donde se guardan todas las dependencias.

----
### Creando tabla y store procedure
En SQLServer ejecutamos el siguiente script, que nos creará las tablas, creará datos y store procedures.
<script src="https://gist.github.com/HugoRoca/22520d52596da23f5645efc3d2d64932.js"></script>

----
### Paso 1: Archivo de configuración
Empezaremos creando un archivo al cual nombraremos como `config.js`, en este archivo se encontrará la cadena de conexión.
<script src="https://gist.github.com/HugoRoca/4a810876a78cd81d6af38a971ba1fc4a.js"></script>

----
### Paso 2: Conexión y operaciones
Creamos un nuevo archivo al cual nombraremos como `sql.js`, en este archivo crearemos la conexión y las operaciones básicas (select, exec store-procedure).
<script src="https://gist.github.com/HugoRoca/20e7fcc9f5f06d5a04e0b6ab7d5163ae.js"></script>

----
### Paso 3: Ejecuciones
Para ejecutar crearemos una funcion asincrona autoejecutable de la siguiente manera:
<script src="https://gist.github.com/HugoRoca/696e0b9876e7da91c70e8bb8915ff88c.js"></script>

- Para verlo en acción solo debemos de ejecutar lo siguiente en la consola: `node [nombre-archivo].js` 
- El retorno siempre es en formato JSON

> Para obtener el código completo dar click [aquí](https://github.com/PORTAFOLIO-PROYECTOS/NODE_JS_SQLSERVER/archive/master.zip)
#### Comenta, disfruta y comparte! 