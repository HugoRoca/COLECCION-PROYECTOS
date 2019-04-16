---
date: "2019-04-15"
title: "Handlebars | Parte 2"
description: "Continuando con handlebars, esta vez construiremos plantillas mas avanzadas usando condiciones y bucles."
author: "Hugo Roca"
image: /images/post/handlebars-prt-2.svg
imageShared: /images/shared/handlebars-prt-2.jpg
tags:
 - Handlebars
categories:
 - JavaScript
---

### Condiciones
```html
<script id="mi-plantilla" type="text/x-handlebars-template">
    <h1>¡Hola {{nick}}!</h1>
    {{#if dispositivo}}
        <p>Te has conectado desde: {{dispositivo}}</p>
    {{else}}
        <p>No hemos identificado desde dónde te conectas.</p>
    {{/if}}
</script>

<div id="contenedor"></div>

<script>
    $(document).ready(function() {
        var source   = $("#mi-plantilla").html();		
        var plantilla = Handlebars.compile(source);

        var usuarioDispositivo = { nick: 'Carlos', dispositivo: 'WEB' };			
        var usuarioSinIdentificar = { nick: 'Carlos'};
        var usuarioSinDefinir = { nick: 'Carlos', dispositivo: '' };
        
        $('#contenedor').html( plantilla( usuarioDispositivo ) );
    })
</script>
```
El `if` trabajando sobre una propiedad se cumple solo cuando la propiedad existe y tiene un valor que no es vacio y en caso que sea vacio o que no exita lo interpreta como inexistente.

```handlebars
{{#unless dispositivo}}
    <p>(unless) No hemos identificado desde donde te contectas.</p>
{{else}}
    <p>(unless) Te has conectado desde: {{dispositivo}}</p>
{{/unless}}
```
La expreción `unless` es los contrario del `if`, es decir, se ejecuta igual que el `if`, tiene el mismo formato que el `if` hasta incluso soporta el `else` tambien pero en lugar de comprabar que la condición se cumple, esta se ejecuta cuando la condición no se cumple.

### Bucles
```html
<script id="lista-indice" type="text/x-handlebars-template">
    <h1>Índice</h1>
    <ul class="list-unstyled">
    {{#each elementos}}
        <li><a href="{{enlace}}"><span class="glyphicon glyphicon-ok"></span> {{nombre}}</a></li>
    {{/each}}
    </ul>
</script>

<div id="contenedor"></div>

<script>
    var indice = [
            {nombre:'El problema', enlace:'problema.html'}, 
            {nombre:'Expresiones, sintaxis básica', enlace:'expresiones.html'}, 
            {nombre:'Uso básico', enlace:'usobasico.html'}, 
            {nombre:'Datos o contexto', enlace:'datos.html'}, 
            {nombre:'Comentarios', enlace:'comentarios.html'}, 
            {nombre:'Datos con contenido HTML', enlace:'datoshtml.html'}, 
            {nombre:'Mi primera plantilla', enlace:'miprimeraplantilla.html'}, 
            {nombre:'Estructuras condicionales', enlace:'condicional.html'},
            {nombre:'Estructuras iterativas', enlace:'index.html'},
            {nombre:'Propiedades anidadas', enlace:'propiedadesanidadas.html'},
            {nombre:'Variables @first y @last', enlace:'variables_first_last.html'},
            {nombre:'Variables @index y @key', enlace:'variables_index_key.html'},
            {nombre:'Variable @root', enlace:'variables_root.html'},
            {nombre:'Qué son los helpers', enlace:'quesonloshelpers.html'},
            {nombre:'Trabajando con helpers', enlace:'helper.html'},
            {nombre:'Helpers de bloque', enlace:'blockhelper.html'},
            {nombre:'Partials', enlace:'partial.html'}
        ];

    $(document).ready(function() {
        var origen;
        var plantilla;

        origen = document.getElementById('lista-indice').innerHTML;
        plantilla = Handlebars.compile(origen);

        $('#contenedor').html( plantilla(indice) );
    });
</script>

```
Esta plantilla arranca con un h1 estático con el texto que no coge contenido dinámico también inicializa una lista y la cierra, es una lista desordenada que forma parte del índice, y finalmente tenemos la parte de iteración a través de el array que se le pasa a la plantilla, si nos fijamos en la plantilla se le está pasando el `índice`, el índice es una variable en javascript que directamente es una array por lo tanto la única manera de referencia el contexto de tipo array que queremos recorrer es mediante la palabra `this`, this es una palabra que existe en handlebars y en esta caso `this` tomará el valor del `indice` que es precisamente un array por lo tanto si funcionará la instrucción `each` sobre `this`.

La instrucción `each` se contruye muy parecido a la instrucción `if`.


