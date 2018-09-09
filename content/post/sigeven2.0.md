+++
author = "Hugo Roca"
date =  "2018-03-30"
linktitle = "Sistema de gestión de ventas 2.0"
title =  "Sistema de gestión de ventas 2.0"
description = "Como dicen, si hay '1.0' un '2.0' va haber, en esta oportunidad les muestro otro sistema de ventas mas completo en full PHP con jquery y ajax."
weight = "10"
image =  "img/sigeven2.0.jpg"
authorAvatar =  "hugo.jpeg"
nomenu = "main"
tags = [
    "php",
    "mysql",
    "js"
]
+++

Como dicen, si hay '1.0' un '2.0' va haber, en esta oportunidad les muestro otro sistema de ventas mas completo en full PHP con jquery y ajax.

Sistema para el contol de ventas e ingreso de stock, impresion de facturas, boletas y tickets, control de usuarios y permisos. **Desarrollado en PHP7, JQuery y la plantilla AdminLTE.**

## CONTENIDO

      Login
      Dashboard
    ▾ Almacen/
	    Registro de artículo
	    Registro de categorías
    ▾ Compras/
	    Registro de Ingresos
	    Registro de Proveedor
    ▾ Ventas/
	    Registro de Cliente
	    Registro de Ventas
	▾ Impresion en PDF/
	    Factura
		Boleta
		ticket
    ▾ Acceso/
	    Permisos
	    Registro de usuario
    Consulta de Compras
    Consulta de Ventas

## Paso 1
Puedes obtener el codigo fuente de la siguiente forma:

1. Clonar [Sigeven 2.0](https://github.com/PORTAFOLIO-PROYECTOS/SIGEVEN-2.0)
2. Copiarlo a un server WAMP, XAMPP o APACHE

## Paso 2
Ejecutar el script de base de datos ```App/dataBase/dbsistema.sql``` en mysql.

## Paso 3
Configurar el archivo ```App/config/global.php```
```
<?php
//ip de la pc del servidor de la base de datos
define("DB_HOST", "localhost");
//Nombre de la base de datos
define("DB_NAME", "dbsistena");
//Usuario de la base de datos
define("DB_USERNAME","root");
//Contraseña del usuario de la ase de datos
define("DB_PASSWORD","");
//Definimos la codificación de los caracteres
define("DB_ENCODE","utf8");
//Definimos una constante como nombre del proyecto
define("PRO_NOMBRE","ITVentas");
?>
```

## Paso 4
Ingresa a la ruta del servidor donde fue publicado... Comenta, disfruta y comparte! 
