---
date: "2019-04-03"
title: "Javascript: Promesas"
description: "A una promesa, como su propio nombre lo dice, es simplemente un objeto que puede o no devolver algún valor en la línea de tiempo presente y futuro. Me gusta describir una promesa..."
author: "Hugo Roca"
image: /images/post/javascript-promesas.svg
imageShared: /images/shared/javascript-promesas.jpg
tags:
 - JS
categories:
 - JavaScript
---

> A una promesa, como su propio nombre lo dice, es simplemente un objeto que puede o no devolver algún valor en la línea de tiempo presente y futuro. Me gusta describir una promesa como una especie de Karma: Tú haces algo, y en consecuencia obtendrás algo, ahora o en un futuro. Esto aplica igual a las promesas, tu ejecutas código asíncrono y obtienes la promesa de que obtendrás una respuesta, que puede ser en ese instante o en un futuro.

<script src="https://gist.github.com/HugoRoca/1a10f65a97445fa25f23a1dc8e1afc4f.js"></script>

El `promise` objeto resultante tiene propiedades internas:

- `state` - inicialmente "pendiente", luego cambia a "cumplido" o "rechazado",
- `result` - Un valor arbitrario de su elección, inicialmente undefined.

Cuando el ejecutor finaliza el trabajo, debe llamar a una de las funciones que obtiene como argumentos:

- `resolve(value)` - para indicar que el trabajo terminó con éxito:
    - establece stateque "fulfilled",
    - establece resulta value.
- `reject(error)` - para indicar que ocurrió un error:
    - establece stateque "rejected",
    - establece resulta error.


![promise](https://i.ibb.co/QD7GSkd/promise-resolve-reject.png)

### Problema

Se requiere mostrar por consola los post con sus respectivos comentarios consumiendo la siguientes urls:

<script src="https://gist.github.com/HugoRoca/7747acc3bc930d5c05b00d47761a8ae4.js"></script>

La posible solucion que se nos viene a la mente es la siguiente:

<script src="https://gist.github.com/HugoRoca/3666fb89bbe1789a90708a1be8f8232b.js"></script>

Pero tenemos un problema, el request que esta dentro del bucle `for` no esperara a que responda, eso causaría un enredo, la solución que se plantea será la siguiente en la cual usaremos promesas con funciones asincronas.

<script src="https://gist.github.com/HugoRoca/a460bd24314e90ff0965e22c137f1ee1.js"></script>

#### Comenta, disfruta y comparte! 
