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
        let source   = $("#mi-plantilla").html();		
        let plantilla = Handlebars.compile(source);

        let usuarioDispositivo = { nick: 'Carlos', dispositivo: 'WEB' };			
        let usuarioSinIdentificar = { nick: 'Carlos'};
        let usuarioSinDefinir = { nick: 'Carlos', dispositivo: '' };
        
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
La expreción `unless` es lo contrario del `if`, es decir, se ejecuta igual que el `if`, tiene el mismo formato que el `if` hasta incluso soporta el `else` tambien pero en lugar de comprabar que la condición se cumple, esta se ejecuta cuando la condición no se cumple.

### Bucles
```html
<script id="lista-indice" type="text/x-handlebars-template">
    <h1>Índice</h1>
    <ul class="list-unstyled">
    {{#each this}}
        <li><a href="{{enlace}}"><span class="glyphicon glyphicon-ok"></span> {{nombre}}</a></li>
    {{/each}}
    </ul>
</script>

<div id="contenedor"></div>

<script>
    let indice = [
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
        let origen;
        let plantilla;

        origen = document.getElementById('lista-indice').innerHTML;
        plantilla = Handlebars.compile(origen);

        $('#contenedor').html( plantilla(indice) );
    });
</script>

```
Esta plantilla arranca con un h1 estático con el texto que no coge contenido dinámico también inicializa una lista y la cierra, es una lista desordenada que forma parte del índice, y finalmente tenemos la parte de iteración a través de el array que se le pasa a la plantilla, si nos fijamos en la plantilla se le está pasando el `índice`, el índice es una variable en javascript que directamente es una array por lo tanto la única manera de referencia el contexto de tipo array que queremos recorrer es mediante la palabra `this`, this es una palabra que existe en handlebars y en este caso `this` tomará el valor del `indice` que es precisamente un array por lo tanto si funcionará la instrucción `each` sobre `this`.

La instrucción `each` se contruye muy parecido a la instrucción `if`.

### Propiedades anidadas
```html
<script id="mi-plantilla" type="text/x-handlebars-template">
    <h1>{{apellidos}}, {{nombre}}</h1>
    <p>Edad: {{edad}}</p>
    <h2>En la red:</h2>
    <ul class="list-unstyled">
    {{#with social}}
        {{#if twitter}}
        <li><span class="glyphicon glyphicon-chevron-right"></span> <a href="{{twitter}}">En Twitter</a></li>
        {{/if}}
        {{#if facebook}}
        <li><span class="glyphicon glyphicon-chevron-right"></span> <a href="{{facebook}}">En Facebook</a></li>
        {{/if}}
        {{#if web}}
        <li><span class="glyphicon glyphicon-chevron-right"></span> <a href="{{web}}">Web</a></li>
        {{/if}}
        {{#if blog}}
        <li><span class="glyphicon glyphicon-chevron-right"></span> <a href="{{blog}}">Blog</a></li>
        {{/if}}
    {{/with}}
    </ul>
</script>

<div id="contenedor"></div>

<script>
    $(document).ready(function() {

        let registro = {
            nombre: 'Marcos',
            apellidos: 'Gonzalez Sancho',
            edad: '22',
            social: {
                twitter: 'https://twitter.com/qmarcos',
                facebook: 'https://facebook.com/qinteractiva',
                web: 'http://q-interactiva.com',
                blog: 'http://blog.q-interactiva.com'
            }
        };			

        let source   = $("#mi-plantilla").html();		
        let plantilla = Handlebars.compile(source);
        
        $('#contenedor').html( plantilla( registro ) );
    })
</script>
```

Todo ese bloque que acaba con el cierre de la instrucción `with` en su interior entiende que ya está accediendo al objeto social por lo tanto para acceder por ejemplo a la propiedad Facebook ya no hace falta poner el `social.` adelante y de hecho no sería correcto ponerlo delante simplemente ponemos `Facebook` y ya lo está buscando en el contexto de la propiedad `social`.

Por lo tanto es equivalente haber puesto sin el `with => social.Twitter, social.Facebook, social.web, social.blog`. Porque una vez que ponemos `with` podemos ahorrarnos ese camino hasta la propiedad que estamos accediendo porque ya va implícita con el `with`, además en este caso hemos añadido unos condicionales para que podamos apreciar como se pueden mezclar entre ellas las instrucciones tanto el `with` con el `if` y se pueden combinar en base a nuestras necesidades. Por ejemplo, si quitamos el `blog` temporalmente de nuestro objeto de datos veremos como deja de salir debido al `if`. 

Por lo tanto `with` como decíamos sirve para facilitar el acceso a propiedades anidadas dentro del objeto contexto en el que nos encontramos.

`with` se construye muy parecido a las instrucción `each`.

### Variables de datos FIRTS y LAST
```handlebars
<h1>{{apellidos}}, {{nombre}}</h1>
<p>Edad: {{edad}}</p>
<h2>En la red:</h2>
<ul class="list-unstyled">
{{#each social}}
    <li><a href="{{url}}">
        <!-- @firts | @last -->
        {{#if @last}} <span class="glyphicon glyphicon-chevron-right"></span> 
            {{else}} <span class="glyphicon glyphicon-comment"></span> 
        {{/if}}
    {{nombre}}</a></li>
{{/each}}
</ul>
```

Handlebars nos ofrece una serie de variables predefinidas en el sistema que nos dan determinada información dependiendo del contexto en el que se están usando, en este caso vamos a ver dos de ellas (`first y last`), que nos van a servir para conocer cuando estamos en el primer o último elemento de un bucle que estamos recorriendo mediante `each`, esto su aplicación directa es en un escenario de maquetacion web por lo tanto la aplicación de estas dos variables se suele usar dentro de lo que es la plantilla de handlebars, la plantilla que es la parte dedicada en específico a la presentación y por lo tanto como decimos vamos a tener un mecanismo de diferenciar el primer elemento del último y del resto de los elementos de esa iteración y eso nos va a permitir por lo que en muchas situaciones nos encontramos que tenemos que aplicar por ejemplo una clase diferente al primer elemento de una lista o al último como podría ser en el caso de un menú web.

### Variables de datos INDEX y KEY

```handlebars
<h1>{{apellidos}}, {{nombre}}</h1>
<p>Edad: {{edad}}</p>
<h2>En la red:</h2>
<ul class="list-unstyled">
{{#each social}}
    <li><a href="{{url}}"><span class="glyphicon glyphicon-chevron-right"></span> {{nombre}}</a> ({{@index}})</li>
{{/each}}
</ul>

<!-- Resultado: 
twitter (0)
facebook (1)
web (2)
blog (3) -->


<h2>Propiedades del contexto:</h2>
<ul class="list-unstyled">
{{#each this}}
    <li>{{@key}}</li>
{{/each}}
</ul>

<!-- Resultado:
nombre
apellidos
edad
social -->

```

Handlebars tambien nos ofrece a través de sus variables predefinidas `index` y `key` la posibilidad de tener más conocimiento cuando recorremos un objeto o un array mediante la estructura de iteración `each` esto es así porque nos va a permitir saber el índice en el que nos encontramos y nos va a permitir también en el caso de que no sea un array saber la propiedad en la que nos encontramos es decir mediante la estructura de iteración `each` no solamente podemos recorrer array sino que también podemos recorrer objetos a través de cada una de sus propiedades y precisamente estas variables predefinidas `index` y `key` nos van a servir para tener esa información.

`@key` esta variable va ir tomando como valores en la iteración los nombres de las propiedades sobre la que va iterando.

Y vemos que por tanto podemos saber en qué interacción nos encontramos en cuanto a número y también podemos saber qué propiedad estamos recorriendo de un objeto que a priori no tenemos porque conocer, por lo tanto estas dos variables predefinidas son muy útiles a la hora de utilizar bucles `each` porque nos dan un dinamismo y una flexibilidad muy interesante a la hora de interpretar como renderizar nuestra plantilla para cada uno de los elementos que recorremos pero sí que es cierto que estas dos variables predefinidas más que en un `each` de una plantilla convencional de handlebars van a tener mucho más sentido en un `each` que empleemos en un helper que es una estructura especial que nos permite renderizar la plantilla totalmente adaptada a nuestras necesidades.

### Variables de datos ROOT

`Root` es una variable predefinida que nos ofrece handlebars que es realmente útil para acceder a la raíz del contexto en el que estamos trabajando no obstante tiene alguna particularidad que es muy interesante tener en conocimiento porque nos puede ahorrar unos cuantos dolores de cabeza cuando trabajamos con ella.

```html
<script id="mi-plantilla" type="text/x-handlebars-template">
    <h1>{{apellidos}}, {{nombre}}</h1>
    <p>Edad: {{edad}}</p>
    <h2>En la red:</h2>
    <ul class="list-unstyled">
    <p>@root: {{@root.nombre}} / {{this.nombre}}</p>
    {{#each social}}
        <li><a href="{{url}}"><span class="glyphicon glyphicon-chevron-right"></span> {{nombre}}</a> ({{@index}} - {{@root.nombre}} / {{this.nombre}}) </li>
    {{/each}}
    </ul>
</script>

<div id="contenedor"></div>

<script>
    $(document).ready(function() {

        var registro = {
                nombre: 'Marcos',
                apellidos: 'Gonzalez Sancho',
                edad: '22',
                social: [
                    { nombre: 'twitter', url: 'https://twitter.com/qmarcos'},
                    { nombre: 'facebook', url: 'https://facebook.com/qinteractiva'},
                    { nombre: 'web', url: 'http://q-interactiva.com'},
                    { nombre: 'blog', url: 'http://blog.q-interactiva.com'}
                ]
            };		

        var source   = $("#mi-plantilla").html();		
        var plantilla = Handlebars.compile(source);
        
        $('#contenedor').html( plantilla( registro ) );
    })
</script>
```
`root` es una variable predefinida que nos permite acceder siempre al contexto raíz de la plantilla estemos dentro de un bucle o estemos dentro de una instrucción with o en cualquier otro escenario, siempre nos va referenciar el objeto principal o contexto de la plantilla.
