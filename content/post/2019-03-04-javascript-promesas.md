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

Tenemos el siguiente código que muestra por consola la lista de post y comentario por cada una de ellas.

```
"use strict";

const request = require("request");

(async () => {
    let url1 = "https://jsonplaceholder.typicode.com/posts";
    let url2 = "https://jsonplaceholder.typicode.com/comments?postId={id}";

    request(url1, (err, res, bodyPost) => {
        if (err) console.error(err);
        console.log("bodyPost", bodyPost);

        for (const key in bodyPost) {
            const element = bodyPost[key];
            let url = url2.replace("{id}", element.id);

            request(url, (e, r, bodyComments) => {
                if (e) console.error(e);
                console.log("bodyComments", bodyComments);
            })
        }
    });
})();
```
Pero tenemos un problema, el request que esta dentro del bucle `for` no esperara a que responda, eso causará un enredo, la solución que se plantea sera la siguiente usando promesas con funciones asincronas.
