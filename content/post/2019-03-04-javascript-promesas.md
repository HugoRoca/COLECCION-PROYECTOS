---
date: "2019-04-03"
title: "Javascript: Promesas"
description: "A una promesa, como su propio nombre lo dice, es simplemente un objeto que puede o no devolver algún valor en la línea de tiempo presente y futuro. Me gusta describir una promesa como una especie de Karma: Tú haces algo, y en consecuencia obtendrás algo, ahora o en un futuro."
author: "Hugo Roca"
image: /images/post/javascript-promesas.svg
imageShared: /images/shared/javascript-promesas.jpg
tags:
 - JS
categories:
 - JavaScript
---

> A una promesa, como su propio nombre lo dice, es simplemente un objeto que puede o no devolver algún valor en la línea de tiempo presente y futuro. Me gusta describir una promesa como una especie de Karma: Tú haces algo, y en consecuencia obtendrás algo, ahora o en un futuro. Esto aplica igual a las promesas, tu ejecutas código asíncrono y obtienes la promesa de que obtendrás una respuesta, que puede ser en ese instante o en un futuro.

Tenemos el siguiente código

```
"use strict";

const request = require("request");

(async () => {
    let url1 = "https://jsonplaceholder.typicode.com/posts";
    let url2 = "https://jsonplaceholder.typicode.com/comments?postId={id}";
    
    request(url1, (err, response, body) => {
        if (err) console.error(err);
        console.log(body);

        request(url2, (err2, response2, body2) => {

        })
    });

})();
```