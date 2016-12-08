---
layout: default
title: Introducción
permalink: /es/outline/intro.html
---

{::options parse_block_html="true" /}

{% comment %}

http://clojurebridge.github.io/curriculum/es/outline/intro.html

{% endcomment %}

<section>
Introducción a la Programación en Clojure
----------------------------------------
{: .slide-title .chapter}

* ¿Por qué Clojure?
* ¿En qué es bueno Clojure?
* ¿A qué se parece Clojure?
    - Comments
* Qué es El REPL?
* REPL en acción
</section>

<section ng-controller="NarrativeController">
## ¿Por qué Clojure?
{: .slide_title .slide}

#### <button class="link" ng-model="block11" ng-click="block11=!block11">Intro</button>

> si vos no programaste antes, puede que no sepas que hay muchos lenguages 
> de donde elegir. Puede de que hayas escuchado de otros lenguajes
> (o escucharás de ellos!) como C, JavaScript, Python y
> Java.
{: ng-show="block11" .description}

> Entonces ¿por qué estamos enseñanado Clojure? Aunque no es tan popular
> como alguno de estos lenguajes, estamos usando Clojure por tres cualidades
> es ideal como primer lenguaje para aprender (o un gran lenguaje 
> para aprender) además de otros que tal vez ya conozcas:
{: ng-show="block11" .description}

#### Clojure es _simple_ <button class="link" ng-bind-html="details" ng-model="block12" ng-click="block12=!block12"></button>

> Clojure es _simple_. Esto no quiere decir que no sea poderoso; lo es. El
> número de conceptos que tienes que saber para programar en Clojure es muy
> pequeño y fácil de entender. Clojure crece con vos mientras lo
> estas aprendiendo, y puedes ser muy productivo con un pequeño subconjunto 
> del lenguaje.
{: ng-show="block12" .description}

#### Clojure es de _proposito-general_ <button class="link" ng-bind-html="details" ng-model="block13" ng-click="block13=!block13"></button>

> Clojure es de _proposito-general_. Algunos lenguajes tienen un foco específico.
> JavaScript, por ejemplo, fue tradicionalmente usado solo en páginas web
> (aunque eso ha cambiado de alguna manera). Objective-C es usado principalmente 
> para applicaciones iPhone. Hoy vamos a hacer una aplicación para dibujar, 
> pero puedes usar Clojure para cualquier tipo de aplicación facilmente.
{: ng-show="block13" .description}

#### Clojure es _diversión_ <button class="link" ng-bind-html="details" ng-model="block14" ng-click="block14=!block14"></button>

> Clojure es _diversión_. Eso es una cuestión de opinión, por supuesto, pero
> pensamos que es verdad. Espero que durante este curso experimenten
> la alegria de ver un programa hecho en Clojure ejecutarse y hacer algo 
> poderoso y sorprendente.
{: ng-show="block14" .description}
</section>

<section ng-controller="NarrativeController">
## ¿En qué es bueno Clojure?
{: .slide_title .slide}

#### <button class="link" ng-model="block21" ng-click="block21=!block21">Intro</button>

> Entonces, dijimos que Clojure es de propósito-general, y lo es. Eso no significa
> que no tenga puntos fuertes.
{: ng-show="block21" .description}

#### Procesamiento de datos <button class="link" ng-bind-html="details" ng-model="block22" ng-click="block22=!block22"></button>

> Clojure es reconocido por hacer un buen procesamiento de datos. Esto es 
> porque tiene un buen set de estructura de datos--eso es, Es que tiene muchas
> maneras incorporadas de representar datos que lo hacen fácil y poderoso.
{: ng-show="block22" .description}

#### Concurrencia <button class="link" ng-bind-html="details" ng-model="block23" ng-click="block23=!block23"></button>

> Clojure es reconocido por su concurrencia. Pensá acerca de escribir 
> instrucciones para cuatro de tus amigos sobre como construir una casa del 
> árbol, pero en vez de escribirlas de manera que un sólo paso es realizado 
> a la vez, cada uno de tus amigos hace parte del trabajo. entonces, ellos
> coordinan el momento exacto como construir esas partes en partes más
> grandes, y ellos haces esto uno y otra vez hasta el final, cuando todas
> las partes se juntan. Estas instrucciones pueden ser realmente complicadas
> y difíciles de escribir--y probablemente difíciles de escribir también.
> Clojure nos da algunas fáciles maneras de escribir ese tipo de
> instrucciones para computadoras.
{: ng-show="block23" .description}

#### Todo! <button class="link" ng-bind-html="details" ng-model="block24" ng-click="block24=!block24"></button>

> Clojure también sirve para construir aplicaciones de dibujo con
> [Quil](https://github.com/quil/quil), con el cual vamos a hacer algo
> juntos.
{: ng-show="block24" .description}
</section>

<section ng-controller="NarrativeController">
## ¿A qué se parece Clojure?
{: .slide_title .slide}

```clojure
(print-str "Hello, World!")
(+ 3 4)
(forward :trinity 40)
```

#### Paréntesis <button class="link" ng-bind-html="details" ng-model="block31" ng-click="block31=!block31"></button>

> Viste los paréntesis?. Los paréntesis encierran instrucciones para la 
> computadora en Clojure. Un paréntesis izquierdo
> es el comienzo de una instrucción, y su respectivo paréntesis derecho es
> el final de una instrucción. Normalmente, el código Clojure tiene un montón
> de paréntesis anidados, en otras palabras, los paréntesis anidados encierran 
> instrucciones.
{: ng-show="block31" .description}

#### Funciones <button class="link" ng-bind-html="details" ng-model="block32" ng-click="block32=!block32"></button>

> después de los paréntesis, veremos las instrucciones de la computadora.
> Esa instrucción es lo que normalmente llamamos una _función_.
> las funciones hacen todo el trabajo duro en Clojure.
> `print-str`, `+` y `forward` son todas funciones.
> Cuando estas funciones se ejecutan, ellas retornan algún tipo de valor.
> En Clojure las funciones siempre retornan un valor.
{: ng-show="block32" .description}

#### Argumentos <button class="link" ng-bind-html="details" ng-model="block33" ng-click="block33=!block33"></button>

> La mayoria de las funciones usan _argumentos_--es todo aquello dentro de los
> parentesis después de la función--.
> `print-str` utiliza "Hello, World!" y retorna una cadena de caracteres.
> `+` utiliza 3 y 4, los suma, y devuelve 7.
> `forward` utiliza :trinity y 40, mueve la tortuga en 40 y retorna
> el resultado.
{: ng-show="block33" .description}
</section>

<section ng-controller="NarrativeController">
### Comentarios

<button class="link" ng-bind-html="details1" ng-model="block41" ng-click="block41=!block41"></button>
<button class="link" ng-bind-html="details2" ng-model="block42" ng-click="block42=!block42"></button>

> Cuando escribimos código, trataremos de que sea lo más claro posible. esto es
> un gran avance porque nuestro código puede ser leido por otros (a veces
> por más que nosotros!), o podemos volver a leer nuestro propio código
> después, llegado el caso nosotros podemos olvidar cada detalle que hemos hecho 
> en nuestro código. Una manera de clarificar nuestro código es haciendo 
> acotaciones con comentarios. Los Comentarios son notas que agregamos al código,  
> por nuestro propio bien, la computadora los ignora.
{: ng-show="block41" .description}

> En Clojure, comentarios pueden ser comenzados con un punto y coma. Todo
> después de un punto y coma hasta el final de la línea es un comentario que
> ignorado por la computadora. Solo un punto y coma es necesario, pero 
> a veces puedes ver dos punto y coma en una fila, dependiendo del estilo
> usado.
{: ng-show="block42" .description}

> Referencia: [Comment](http://clojurebridge.github.io/community-docs/docs/clojure/comment/)
{: ng-show="block42" .description}

```clojure
;; ejemplo de funciones de un slide anterior
(print-str "Hola, Mundo!")   ; el bien-conocido "hola mundo"
(+ 3 4)                      ; ¿por qué no 3 + 4? lo veremos después
```
</section>

<section>
## ¿Qué es El REPL?
{: .slide_title .slide}

#### <button class="link" ng-model="block51" ng-click="block51=!block51">Intro</button>

> "REPL" significa "Leer-Evaluar-Imprimir-Loop," lo cual no tieme mucho sentido
> sin el contexto. Muchos lenguajes de progrmación, inclujendo Clojure,
> hay una manera de escribir código interactivamente, con el cual puedes
> tener una respuesta instantanea. En otras palabras, el código es leido,  
> cuando es evaluado,
> el resultado es impreso en pantalla, y comienza nuevamente, un loop.
{: ng-show="block51" .description}

**R**ead, **E**val, **P**rint, **L**oop

![El repl de Nightcode](img/repl.png)

</section>

<section ng-controller="NarrativeController">
## REPL en acción
{: .slide_title .slide}


#### Nightcode InstaREPL <button class="link" ng-bind-html="details" ng-model="block61" ng-click="block61=!block61"></button>

> Para interactuar con Clojure, podemos usar el InstaREPL de Nightcode.
> esta es una buena manera de juagr Clojure interactivamente.
{: ng-show="block61" .description}


#### Usando el REPL <button class="link" ng-bind-html="details" ng-model="block62" ng-click="block62=!block62"></button>

> Nightcode tiene un seteo de projecto conectado con REPL en el fondo del panel.
> Cuando el botón "Run with REPL" es clickeado, el REPL empieza.
{: ng-show="block62" .description}

> Alternativamente, podemos iniciar un  REPL usando leiningen en una terminal (sin
> Nightcode).
> En una terminal, escribe `lein repl`, entonces, el REPL inicará.
> Si ejecutamos`lein repl`  en el directorio del projecto (carpeta), veras
> la configuración.
{: ng-show="block62" .description}


#### Evaluar un programa y línea <button class="link" ng-bind-html="details" ng-model="block63" ng-click="block63=!block63"></button>

<!-- TODO project_name should probably be defined somewhere, right? -->
> Nightcode nos deja evaluar un archivo entero (programa) o una línea(s).
> En Nightcode, después que el REPL ha iniciado "Realod File" y "Reload Selection"
> funcionan.
{: ng-show="block63" .description}
</section>

<section>
#### EJERCICIO 1: Prueba el InstaREPL de Nightcode 

1. inicia Nightcode
2. Importa `myproject` <br/> (el cual creaste mientras testeabas el setup de leiningen)
3. Abrí `core.clj` <br/>(`myproject` -> `src` -> `myproject` -> `core.clj`
4. Hace click en el  __InstREPL__ botón
5. Escribí las funciones Clojure funciones escritas abajo y ve que pasa

```clojure
(print-str "Hola, Mundo!")
(print-str "Hola, Mundo!" " " "desde Clojure")
(+ 3 4)
(- 3 4)
(* 3 4)
```
> Asegurate de tipiar la lineas  <em>exactamente</em> como las vez,
> teniedo cuidado de poner los paréntesis en el lugar correcto.
</section>

<section>
#### EXERCISE 2: Evaluate file and line - Part 1

* Abrí el archivo `welcometoclojurebridge/src/clojurebridge_turtle/walk.clj`
* Evaluá todo el archivo presionando "Run with REPL" seguido de "Reload File"
* Mirá que pasa después
* Tipiá `(forward 40)` al fondo del archivo `walk.clj` en el editor. Evaluar esta linea elijiendo la linea y presionando "Reload Selection"
* Mirá que pasa después

(Continua en el EJERCICIO 3)
</section>

<section>
#### EJERCICIO 3: Evaluar el archivo y línea - Parte 2

(Suponiendo que el EJECICIO 2 está terminado)

* Tipiá `(right 90)` y "enter" en el REPL (al fondo) ![Run with REPL pane](img/run-with-repl.png)
* Mirá que pasa con la tortuga
* Pegale una mirada a [Tortugas App API](https://github.com/ClojureBridge/welcometoclojurebridge/blob/master/outline/TURTLE.md) y
[Como pasear Tortugas](https://github.com/ClojureBridge/welcometoclojurebridge/blob/master/outline/TURTLE-SAMPLES.md)
[sección 1 y 2], y prueba más comandos para pasear tu tortuga
</section>

<section>
#### EJERCICIO 4: Mirar los docs de Clojure

* En el fondo del REPL, intentá mirar la  documentación por las funciones usadas
* Podes usar el  `(doc function-name)` comando para esto
* Probá `(doc +)` y `(doc forward)` en el REPL
* Probá algun otra función que hemos usado, por ejemplo, `-`, `*`, ó `doc`
</section>

{% comment %}

:star2: El link siguiente es para un slide solo. Andá al[README.md](../README.md). :star2:

{% endcomment %}

<section>
Volvé al <a href="javascript:;" onClick="Reveal.slide(1);">primer slide</a>,
or andá al [curriculum outline](/curriculum/#/1).
</section>
