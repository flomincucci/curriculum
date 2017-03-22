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
* ¿Qué tal se ve Clojure?
* Qué es el REPL?
* El REPL en acción
</section>

<section ng-controller="NarrativeController">
## ¿Por qué Clojure?
{: .slide_title .slide}

#### <button class="link" ng-model="block11" ng-click="block11=!block11">Intro</button>

> Si nunca programaste antes, puede que no sepas que hay muchos lenguages
> de dónde elegir. Puede que hayas escuchado de otros lenguajes
> (o escucharás de ellos!) como C, JavaScript, Python y
> Java.
{: ng-show="block11" .description}

> Entonces ¿por qué estamos enseñando Clojure? Aunque no es tan popular
> como algunos de esos lenguajes, estamos usando Clojure por tres cualidades
> que tiene que lo hacen ideal como primer lenguaje para aprender
> (o un gran lenguaje para aprender!) además de otros que tal vez ya conozcas:
{: ng-show="block11" .description}

#### Clojure es _simple_ <button class="link" ng-bind-html="details" ng-model="block12" ng-click="block12=!block12"></button>

> Clojure es _simple_. Esto no quiere decir que no sea poderoso; lo es. El
> número de conceptos que tienes que saber para programar en Clojure es muy
> pequeño y fácil de entender. Clojure crece con vos mientras lo
> estas aprendiendo, y puedes ser muy productivo con un pequeño subconjunto
> del lenguaje.
{: ng-show="block12" .description}

#### Clojure es de _propósito general_ <button class="link" ng-bind-html="details" ng-model="block13" ng-click="block13=!block13"></button>

> Clojure es de _propósito general_. Algunos lenguajes tienen un foco específico.
> JavaScript, por ejemplo, fue tradicionalmente usado solo en páginas web
> (aunque eso ha cambiado de alguna manera). Objective-C es usado principalmente
> para aplicaciones iPhone. Hoy vamos a hacer una aplicación para dibujar,
> pero puedes usar Clojure para cualquier tipo de aplicación facilmente.
{: ng-show="block13" .description}

#### Clojure es _divertido_ <button class="link" ng-bind-html="details" ng-model="block14" ng-click="block14=!block14"></button>

> Clojure es _divertido_. Esto es una cuestión de opinión, por supuesto, pero
> pensamos que es verdad. Esperamos que durante este curso experimenten
> la alegría de construir un programa hecho en Clojure y hacer algo
> poderoso y sorprendente.
{: ng-show="block14" .description}
</section>

<section ng-controller="NarrativeController">
## ¿En qué es bueno Clojure?
{: .slide_title .slide}

#### <button class="link" ng-model="block21" ng-click="block21=!block21">Intro</button>

> Entonces, dijimos que Clojure es de propósito general, y lo es. Eso no significa
> que no tenga puntos fuertes.
{: ng-show="block21" .description}

#### Procesamiento de datos <button class="link" ng-bind-html="details" ng-model="block22" ng-click="block22=!block22"></button>

> Clojure es reconocido por ser bueno para el procesamiento de datos. Esto es
> porque tiene un buen set de estructuras de datos. Es decir, que tiene muchas
> maneras incorporadas de representar datos que lo hacen fácil y poderoso.
{: ng-show="block22" .description}

#### Concurrencia <button class="link" ng-bind-html="details" ng-model="block23" ng-click="block23=!block23"></button>

> Clojure es reconocido por su concurrencia. Pensá acerca de escribir
> instrucciones para cuatro de tus amigos sobre cómo construir una casa del
> árbol, pero en vez de escribirlas de manera que un sólo paso es realizado
> a la vez, cada uno de tus amigos hace parte del trabajo. Entonces, ellos
> coordinan el momento exacto para ensamblar esas partes en partes más
> grandes, y hacen esto una y otra vez hasta el final, cuando todas
> las partes se juntan. Estas instrucciones pueden ser realmente complicadas
> y difíciles de escribir (y probablemente difíciles de leer también).
> Clojure nos da algunas maneras fáciles de escribir este tipo de
> instrucciones para computadoras.
{: ng-show="block23" .description}

#### Todo! <button class="link" ng-bind-html="details" ng-model="block24" ng-click="block24=!block24"></button>

> Clojure también sirve para construir aplicaciones de dibujo con
> [Quil](https://github.com/quil/quil), con el cual vamos a hacer algo
> juntos.
{: ng-show="block24" .description}
</section>

<section ng-controller="NarrativeController">
## ¿Qué tal se ve Clojure?
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

> Después de los paréntesis, veremos las instrucciones para la computadora.
> Esa instrucción es lo que normalmente llamamos una _función_.
> Las funciones hacen todo el trabajo duro en Clojure.
> `print-str`, `+` y `forward` son funciones.
> Cuando estas funciones se ejecutan, ellas retornan algún tipo de valor.
> En Clojure las funciones siempre retornan un valor.
{: ng-show="block32" .description}

#### Argumentos <button class="link" ng-bind-html="details" ng-model="block33" ng-click="block33=!block33"></button>

> La mayoria de las funciones usan _argumentos_ (es todo aquello dentro de los
> parentesis después de la función).
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

> Cuando escribimos código, trataremos de que sea lo más claro posible. Esto es
> un gran avance porque nuestro código puede ser leido por otros (a veces
> más que por nosotros mismos!), o podemos volver a leer nuestro propio código
> más tarde, y puede ser que hayamos olvidado cada detalle
> del código. Una manera de clarificar nuestro código es haciendo
> anotaciones con comentarios. Los comentarios son notas que agregamos al código,
> para nuestro propio bien, y que la computadora ignora.
{: ng-show="block41" .description}

> En Clojure, los comentarios pueden ser comenzados con un punto y coma. Todo lo
> que va después de un punto y coma hasta el final de la línea es un comentario que
> es ignorado por la computadora. Solo un punto y coma es necesario, pero
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
## ¿Qué es el REPL?
{: .slide_title .slide}

#### <button class="link" ng-model="block51" ng-click="block51=!block51">Intro</button>

> "REPL" significa "Leer-Evaluar-Imprimir-Loop" (del inglés "Read-Eval-Print-Loop")
> lo cual no tieme mucho sentido sin el contexto.
> Muchos lenguajes de programación, incluyendo Clojure,
> tienen una manera de escribir código interactivamente, con el cual puedes
> tener una respuesta instantanea. En otras palabras, el código es leído,
> luego es evaluado,
> el resultado es impreso en pantalla, y comienza nuevamente: un loop.
{: ng-show="block51" .description}

**R**ead, **E**val, **P**rint, **L**oop

![El repl de Nightcode](/curriculum/outline/img/repl.png)

</section>

<section ng-controller="NarrativeController">
## El REPL en acción
{: .slide_title .slide}


#### Nightcode InstaREPL <button class="link" ng-bind-html="details" ng-model="block61" ng-click="block61=!block61"></button>

> Para interactuar con Clojure, podemos usar el InstaREPL de Nightcode.
> esta es una buena manera de jugar con Clojure interactivamente.
{: ng-show="block61" .description}


#### Usando el REPL <button class="link" ng-bind-html="details" ng-model="block62" ng-click="block62=!block62"></button>

> Nightcode tiene un seteo de proyecto conectado con el REPL en el panel de abajo.
> Cuando el botón "Run with REPL" es clickeado, el REPL empieza.
{: ng-show="block62" .description}

> Alternativamente, podemos iniciar un  REPL usando leiningen en una terminal (sin
> Nightcode).
> En una terminal, escribe `lein repl`, entonces el REPL iniciará.
> Si ejecutamos `lein repl`  en el directorio del proyecto (carpeta), verás
> la configuración.
{: ng-show="block62" .description}


#### Evaluar un programa y una línea <button class="link" ng-bind-html="details" ng-model="block63" ng-click="block63=!block63"></button>

<!-- TODO project_name should probably be defined somewhere, right? -->
> Nightcode nos deja evaluar un archivo entero (programa) o una línea(s).
> En Nightcode, después que el REPL ha iniciado "Reload File" y "Reload Selection"
> funcionan.
{: ng-show="block63" .description}
</section>

<section>
#### EJERCICIO 1: Prueba el InstaREPL de Nightcode

1. Inicia Nightcode
2. Importa `myproject` <br/> (el cual creaste mientras testeabas el setup de leiningen)
3. Abrí `core.clj` <br/>(`myproject` -> `src` -> `myproject` -> `core.clj`
4. Hacé click en el botón  __InstaREPL__
5. Escribí las funciones Clojure escritas abajo y observa qué pasa

```clojure
(print-str "Hola, Mundo!")
(print-str "Hola, Mundo!" " " "desde Clojure")
(+ 3 4)
(- 3 4)
(* 3 4)
```
> Asegurate de tipear las líneas  <em>exactamente</em> como las ves,
> teniendo cuidado de poner los paréntesis en el lugar correcto.
</section>

<section>
#### EJERCICIO 2: Evaluar un archivo y una línea - Parte 1

* Abrí el archivo `welcometoclojurebridge/src/clojurebridge_turtle/walk.clj`
* Evaluá todo el archivo presionando "Run with REPL" seguido de "Reload File"
* Mirá qué pasa después
* Tipeá `(forward 40)` al fondo del archivo `walk.clj` en el editor. Evaluá esta línea eligiendo la línea y presionando "Reload Selection"
* Mirá qué pasa después

(Continúa en el EJERCICIO 3)
</section>

<section>
#### EJERCICIO 3: Evaluar el archivo y la línea - Parte 2

(Suponiendo que el EJECICIO 2 está terminado)

* Tipeá `(right 90)` y "enter" en el REPL (al fondo) ![Run with REPL pane](/curriculum/outline/img/run-with-repl.png)
* Mirá qué pasa con la tortuga
* Pegale una mirada a [Tortugas App API](https://github.com/ClojureBridge/welcometoclojurebridge/blob/master/outline/TURTLE.md) y
[Cómo pasear Tortugas](https://github.com/ClojureBridge/welcometoclojurebridge/blob/master/outline/TURTLE-SAMPLES.md)
[sección 1 y 2], y prueba más comandos para pasear tu tortuga
</section>

<section>
#### EJERCICIO 4: Mirar los docs de Clojure

* En el fondo del REPL, intentá mirar la documentación para las funciones usadas
* Podés usar el comando `(doc function-name)` para esto
* Probá `(doc +)` y `(doc forward)` en el REPL
* Probá alguna otra función que hayamos usado, por ejemplo, `-`, `*`, o `doc`
</section>

{% comment %}

:star2: El link siguiente es para un slide solo. Andá al[README.md](../README.md). :star2:

{% endcomment %}

<section>
Volvé al <a href="javascript:;" onClick="Reveal.slide(1);">primer slide</a>,
o andá al [outline del curriculum](/curriculum/es/#/1).
</section>
