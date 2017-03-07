---
layout: default
title: Secuencias
permalink: /es/outline/sequences.html
---

{::options parse_block_html="true" /}

{% comment %}

http://clojurebridge.github.io/curriculum/es/outline/sequences.html

{% endcomment %}

<section>
[BONUS]

Secuencias
-------------------------
{: .slide-title .chapter}

* Qué es una secuencia
* Funciones para secuencias
    * `doseq`
    * `dotimes`
</section>

<section ng-controller="NarrativeController">
### Qué es una secuencia?
{: .slide_title .slide}

#### Estructuras de datos de Clojure <button class="link" ng-bind-html="details" ng-model="block11" ng-click="block11=!block11"></button>

> En Clojure, podemos decir que cada estructura de datos es una secuencia.
> Hasta ahora, aprendimos sobre `vector` y `map`, ambas de las cuales son secuencias.
> String también es una secuencia. Cuando algo es **seq-uenciable**, es una secuencia.
{: ng-show="block11" .description}

#### `first` para verificar secuencias <button class="link" ng-bind-html="details" ng-model="block12" ng-click="block12=!block12"></button>

> Si algo es **seq-uenciable**, aplicando `first` obtenemos el primer elemento de la secuencia.
> Ésta es una buena forma de probar si algo es o no es una secuencia.
{: ng-show="block12" .description}
</section>

<section ng-controller="NarrativeController">
#### Resultados de `first`

```clojure
(turtle-names)
;=> [:trinity :neo :oracle :cypher] ; vector
(first (turtle-names))
;=> :trinity                        ; primer elemento

(:trinity (state))
;=> {:x 0, :y 0, :angle 90, :color [30 30 30]}  ; map
(first (:trinity (state)))
[:x 0]                                          ; primer elemento

(first "Hello, World!")  ; string
;=> \H                   ; primer elemento

(first :trinity)         ; la palabra clave no es seq-uenciable
;=> IllegalArgumentException Don't know how to create ISeq from:
clojure.lang.Keyword  clojure.lang.RT.seqFrom (RT.java:528)
```
</section>

<section ng-controller="NarrativeController">
### Funciones para secuencias
<button class="link" ng-bind-html="details" ng-model="block21" ng-click="block21=!block21"></button>

> Clojure es muy bueno para *iterar* sobre una secuencia.
> Hay muchas funciones que interactúan con secuencias.
> Por ejemplo, `doseq`, `dotimes`, `for`, `loop`, `doall`, o `dorun`.
>
> Ya vimos las funciones `map` y `reduce` en la sección "Funciones cuyos parámetros son otras funciones". Éstas también son funciones para secuencias.
{: ng-show="block21" .description}
</section>

<section ng-controller="NarrativeController">
#### `doseq`

<button class="link" ng-bind-html="details1" ng-model="block31" ng-click="block31=!block31"></button>
<button class="link" ng-bind-html="details2" ng-model="block32" ng-click="block32=!block32"></button>

> La función `doseq`("hacer una secuencia" - **do a sequence**) es una de las funciones frecuentemente utilizadas
>  para secuencias, y funciona de manera similar a la función `map`.
> La función evalúa el cuerpo repetidamente, con cada elemento de la secuencia
> que se le pasa como argumento.
{: ng-show="block31" .description}

> La función `doseq` recibe como argumento un vector de asociaciones de
> nombre-valor, que puede presentar un aspecto extraño: `[nombre secuencia]`. Al iterar sobre cada elemento
> de `secuencia`, el elemento iterado se asigna a `nombre`.
{: ng-show="block32" .description}

```clojure
;; ejemplo de doseq
(doseq [n (turtle-names)] (forward n 40))
```
</section>

<section>
#### EJERCICIO 1

* [Turtles Walk](https://github.com/ClojureBridge/welcometoclojurebridge/blob/master/outline/TURTLE-SAMPLES.md) (más estudio de funciones)
    - sección 5 y posteriores
* [Snowflakes](https://github.com/ClojureBridge/drawing/blob/master/curriculum/create-something.md) (animación)
    - paso 4 y siguientes
* [Twinkle Twinkle Little Star](https://github.com/ClojureBridge/tones/blob/master/curriculum/01-piano-chords.md) (haciendo sonido)
    - función `chord` y más adelante
</section>

<section ng-controller="NarrativeController">
#### `dotimes`

<button class="link" ng-bind-html="details1" ng-model="block41" ng-click="block41=!block41"></button>
<button class="link" ng-bind-html="details2" ng-model="block42" ng-click="block42=!block42"></button>

> La función `dotimes`("**hacer n veces**") es otra función de secuencias
> ampliamente utilizada. Como `doseq`, la función evalúa repetitivamente
> la forma pasada como cuerpo. La diferencia está en la asociación con el 
> argumento. `dotimes` recibe: `[nombre max-entero]`.
{: ng-show="block41" .description}

> La función `dotimes` es lo más parecido a un bucle `for` en otros lenguajes
> de programación. Esta función nos permite acceder mediante un índice a cualquier
> elemento de la secuencia utilizando la función `nth`.
{: ng-show="block42" .description}

```clojure
;; asumiendo que hay más de una tortuga
(def names (turtle-names))
(dotimes [n (count names)] (right (nth names n) (* 45 n)))
```
</section>

<section>
#### EJERCICIO 2

* [Tortugas caminando](https://github.com/ClojureBridge/welcometoclojurebridge/blob/master/outline/TURTLE-SAMPLES.md) (más estudio de funciones)
    - sección 6 y siguientes
* [Copos de nieve ](https://github.com/ClojureBridge/drawing/blob/master/curriculum/create-something.md) (animación)
    - paso 5-4 y siguientes
* [Estrellita que brillas](https://github.com/ClojureBridge/tones/blob/master/curriculum/01-piano-chords.md) (haciendo sonidos)
    - sección Twinkle Little Star completa
</section>


{% comment %}

:star2: Un enlace inferior es sólo para una diapositiva. Ve a [README.md](../README.md) :star2:

{% endcomment %}

<section>
Regresar a la <a href="javascript:;" onClick="Reveal.slide(1);">primera diapositiva</a>,
o ir al [índice](/curriculum/#/1).
</section>
	