+++
author = "Hugo Roca"
date =  "2018-09-01"
linktitle = "Programación Orientada a Objetos"
title =  "Programación Orientada a Objetos"
description = "POO es un paradigna de programación que comenzó a desarrollarse en los años 80, en ese momento se dieron cuenta que esta forma de programación facilitaba el desarrollo de sistemas de gran tamaño."
weight = "10"
image =  "https://hugorocaproyectos.js.org/img/POO.jpg"
authorAvatar =  "hugo.jpeg"
nomenu = "main"
tags = [
    "POO"
]
+++

POO es un paradigna de programación que comenzó a desarrollarse en los años 80, en ese momento se dieron cuenta que esta forma de programación facilitaba el desarrollo de sistemas de gran tamaño.

De hecho actualmente este paradigma de programación es el más utilizado, los grandes sistemas que conocemos han sido desarrollados en base a este paradigma.

### Las ventajas de poo

* Es reutilizable, esto quiero decir que si desarrollamos nuestro código de forma adecuada, las clases y lo que creemos se puede reutilizar, en distintas partes del programa la cual nos va a permitir no duplicar código.
* Mantenibilidad, un sistema orientado a objetos va ser mucho mas fácil de leer y comprender para los programadores, ya que para ellos no vas ser necesario adentrarse demasiado al código, basta con ver las clases generales para darse cuenta como funciona .
* Modificable, si nuestro código esta bien implementado va ser muy fácil añadir, modificar  o incluso eliminar las clases u objetos que ya existan en el código.
* Un sistema orientado a objetos también es fiable, es mas fácil detectar errores en este tipo de programas, podemos dividir el sistema en partes e ir las probando de manera independiente 

### Característica principales

* Abstracción
* Encapsulamiento
* Herencia
* Polimorfismo

Para poder desarrollar aplicaciones orientas a objetos de la mejor manera, debemos analizar y entender cada uno de estos conceptos.

## La abstracción
Es un pilar o característica de la programación orienta a objetos, que va permitir que los objetos puedan interactuar sin necesidad de conocer los detalles del funcionamiento, de esta forma el enfoque se centra en aspectos relevantes de las entidades, podemos decir de hecho que estos aspectos son relativos ya que van a depender del enfoque en que se analice. Para entender el concepto vamos a modelar una escuela.
Una escuela puede tener muchas características, pero con la abstracciones me voy a centar o enfocar únicamente en las características que yo necesito, para ellos debo de pensar de que como quiero modelar la escuela, lo puedo modelas desde el punto de vista administrativo, por ejemplo:

-	Control de alumnos
-	Control de empleados
-	Control de asignaturas 

Este seria el caso de un sistema de administración para escuela, también podemos enfocarnos de otra forma en las escuelas; podría ser que yo quisiera un sistema para una constructora,  en este caso puedo ver el enfoque de la escuela es muy diferente; a una constructora le van a interesar las características de la escuela las cuales pueden ser, ventanas, puertas, pisos entre otras aspectos.
Como podemos ver una misma entidad puede analizarse desde varias puntos de vista o enfoque, ademas de acuerdo de este enfoque se van a definir las características o comportamientos.

La abstraccion tambien nos va a permitir eliminar todos aquellos aspectos que forman parte del objeto o entidad pero que no son significatios para el caso que estamos analizando.
