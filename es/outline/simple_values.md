---
layout: default
title: Valores simples
permalink: /es/outline/simple_values.html
---

{::options parse_block_html="true" /}

{% comment %}

http://clojurebridge.github.io/curriculum/es/outline/simple_values.html

{% endcomment %}

<section>
Valores Simples
----------------------------------------
{: .slide-title .chapter}

* Cadenas de caracteres
* Booleanos y nil
* Palabras clave
* Números
  - Aritmética

* Asignación: `def`
</section>

<section>
## Valores simples

#### <button class="link" ng-model="block71" ng-click="block71=!block71">Introducción</button>

> Antes de poder hacer algo con un lenguaje de programación, necesitamos tener
> datos para manipular. En Clojure, los datos se representan con valores, y los
> tipos más simples de valores son los números, las cadenas de caracteres,
> los booleanos, nil y las palabras claves.
{: ng-show="block71" .description}
</section>

<section ng-controller="NarrativeController">
### Cadenas de caracteres
{: .slide_title .slide}

#### <button class="link" ng-bind-html="details" ng-model="block21" ng-click="block21=!block21"></button>

> ¿Qué es una cadena de caracteres? Es un fragmento de texto. Para crear una
> cadena es necesario delimitar los caracteres con comillas dobles.
>
> El último ejemplo muestra como incluir comillas en una cadena: es necesario
> escribir una barra invertida antes de las comillas. Asegurate siempre de usar
> comillas dobles para crear una cadena.
{: ng-show="block21" .description}

> Referencia: [String](http://clojurebridge.github.io/community-docs/docs/clojure/string/)
{: ng-show="block21" .description}

```clojure
"Hola, Mundo!"
"Las cadenas pueden contener muchos, muchos caracteres"
"Alicia dijo, \"Podemos ir a tomar el té.\""
```
</section>

<section ng-controller="NarrativeController">
### Booleanos y nil
{: .slide_title .slide}

#### <button class="link" ng-bind-html="details" ng-model="block31" ng-click="block31=!block31"></button>

> Un booleano indica que algo es verdadero o es falso y en Clojure los
> escribimos como `true` o `false`, respectivamente. Cuando programamos, es
> común hacer preguntas del tipo "¿Hoy es el cumpleaños de tal persona?" o
> "¿Esta materia se dicta en el primer cuatrimestre?"  para saber si algo es
> cierto. La respuesta a estas preguntas, es un valor booleano.
{: ng-show="block31" .description}

> `nil` es un valor especial que se utiliza para representar la _ausencia de
> un valor_. Una particularidad de `nil` es que se comporta como `false` cuando
> lo usamos donde normalmente usaríamos un booleano mientras que  el resto de
> los tipos de datos se comportan como `true`.
{: ng-show="block31" .description}

> Referencia: [Truthiness](http://clojurebridge.github.io/community-docs/docs/clojure/truthiness/)
{: ng-show="block31" .description}


```clojure
true
false
nil
```
</section>

<section ng-controller="NarrativeController">
### Palabras clave
{: .slide_title .slide}

#### <button class="link" ng-bind-html="details" ng-model="block41" ng-click="block41=!block41"></button>

> Las palabras clave son el tipo de dato que puede resultar más extraño porque,
> a diferencia de los números, las cadenas de caracteres y los booleanos, no
> tienen un análogo en el mundo real.
> A veces ayuda pensar que son un tipo especial de cadena de caracteres que se
> usa para _etiquetar_ cosas. Es común ver (y usar) palabras clave para las
> claves de un mapa (un mapa es una estructura de datos que vamos a estudiar en
> breve).
{: ng-show="block41" .description}


```clojure
:trinity
:first
:last
```
</section>

<section ng-controller="NarrativeController">
### Números

#### Enteros <button class="link" ng-bind-html="details" ng-model="block81" ng-click="block81=!block81"></button>

> Clojure tiene varios tipos de números.
{: ng-show="block81" .description}

> Empecemos con los enteros que incluyen al cero y tanto números positivos como
> negativos. Se escriben como los escribimos en cualquier otro lado.
{: ng-show="block81" .description}

```clojure
0
12
-42
```
</section>

<section ng-controller="NarrativeController">
#### Números decimales <button class="link" ng-bind-html="details" ng-model="block91" ng-click="block91=!block91"></button>

> Seguimos con los decimales, a los que también se los llama _"de punto
> flotante"_. Los podemos identificar porque contienen un punto decimal.
{: ng-show="block91" .description}

```clojure
0.0000072725
10.5
-99.9
```
</section>

<section ng-controller="NarrativeController">
#### Fracciones <button class="link" ng-bind-html="details" ng-model="block101" ng-click="block101=!block101"></button>

> Por último, tenemos las fracciones. Una computadora no puede representar
> perfectamente a todos los números decimales y es posible que utilice una misma
> representación para más de un número. Esto no ocurre con las fracciones que
> son siempre exactas. Las podemos reconocer por la barra inclinada "/":
{: ng-show="block101" .description}

> Es importante tener en cuenta que, al igual que en la clase de matemática, el [denominador](https://es.wikipedia.org/wiki/Fracci%C3%B3n) de una fracción no puede ser igual a `0`.
{: ng-show="block101" .description}

```clojure
1/2
-7/3
```
</section>

<section>
### Aritmética
{: .slide_title .slide}

#### <button class="link" ng-model="block111" ng-click="block111=!block111">Intro</button>

> En Clojure, es posible sumar, restar, multiplicar y dividir números. Sin
> embargo, estas operaciones aritméticas no se escriben en la forma que las
> escribimos en papel. Veamos algunos ejemplos:
{: ng-show="block111" .description}

```clojure
(+ 1 1)  ;=> 1 + 1 = 2
(- 12 4) ;=> 12 - 4 = 8
(* 13 2) ;=> 13 * 2 = 26
(/ 27 9) ;=> 27 / 9 = 3
```
</section>

<section ng-controller="NarrativeController">
### Notaciones infija y prefija
{: .slide-title .slide}

<button class="link" ng-bind-html="details1" ng-model="block121" ng-click="block121=!block121"></button>
<button class="link" ng-bind-html="details2" ng-model="block122" ng-click="block122=!block122"></button>

> En _notación prefija_, los operadores `+`, `-`, `*` y `/` aparecen antes que
> los números. Esta notación se ve distinta a la notación a la que estamos
> acostumbrados, conocida como _notación infija_, en donde los operadores
> aritméticos aparecen entre los operandos.
{: ng-show="block121" .description}

> Lenguajes como **JavaScript** utilizan notación **infija**, mientras
> que **Clojure** utiliza notación **prefija** exclusivamente. La
> notación prefija es útil por varias razones, pero antes de
> enumerarlas, veamos un ejemplo de una expresión infija y su
> equivalente en notación prefija:
{: ng-show="block122" .description}

```clojure
Infija:  1 + 2 * 3 / 4 + 5 - 6 * 7 / 8 + 9

Prefija: (+ (- (+ (+ 1 (/ (* 2 3) 4)) 5) (/ (* 6 7) 8)) 9)
```
</section>

<section ng-controller="NarrativeController">
### Por qué la notación prefija es mejor?

#### Precedencia explícita <button class="link" ng-bind-html="details" ng-model="block131" ng-click="block131=!block131"></button>

> Hacé de cuenta que te olvidaste el orden en el que tienen que realizarse las
> operaciones aritméticas. En la expresión infija, vamos a obtener resultados
> diferentes dependiendo qué operación realicemos primero: la suma o la
> división. Esto no es un problema con la notación prefija porque la
> _"precedencia" es explícita_. En otras palabras, hay un único orden de
> evaluación posible debido a que cada expresión está delimitada por paréntesis
> y el operador está siempre delante de los operandos.
{: ng-show="block131" .description}

```clojure
Infija:  1 + 2 / 3
Prefija: (+ 1 (/ 2 3))
```

#### Menos repetitiva <button class="link" ng-bind-html="details" ng-model="block132" ng-click="block132=!block132"></button>

> Otra ventaja de la notación prefija es que no hace falta repetir el
> operador cuando lo aplicamos sobre varios operandos.
{: ng-show="block132" .description}

```clojure
Infix:  1 + 2 + 3 + 4 + 5 + 6 + 7 + 8 + 9
Prefix: (+ 1 2 3 4 5 6 7 8 9)
```
</section>

<section ng-controller="NarrativeController">
### Aritmética con distintos tipos de números

<button class="link" ng-bind-html="details" ng-model="block141" ng-click="block141=!block141"></button>

> Hasta ahora estuvimos realizando operaciones aritméticas con enteros
> únicamente. Sin embargo, nada nos impide utilizar decimales o fracciones:
{: ng-show="block141" .description}

```clojure
(+ 4/3 7/8)   ;=> 53/24
(- 9 4.2 1/2) ;=> 4.3
(/ 27/2 1.5)  ;=> 9.0
```
</section>


<section ng-controller="NarrativeController">
## Asignación: `def`

#### <button class="link" ng-model="block161" ng-click="block161=!block161">Intro</button>

> Es muy difícil escribir un programa si tenemos que escribir los mismos valores
> una y otra vez. A través de una _asignación_ podemos darle un nombre a un
> valor que es mucho más fácil de escribir ¡y recordar! que el valor en sí.
{: ng-show="block161" .description}
</section>

<section ng-controller="NarrativeController">
#### Asginando nombres a valores: `def`

#### <button class="link" ng-bind-html="details" ng-model="block171" ng-click="block171=!block171"></button>

> Podemos asignar un nombre a un valor usando `def`. El nombre que se le asigna
> al valor se llama _símbolo_.
{: ng-show="block171" .description}

> Referencia: [Assignment def](http://clojurebridge.github.io/community-docs/docs/clojure/def/)
{: ng-show="block171" .description}

```clojure
(def mangos 3)
(def naranjas 5)
(+ mangos naranjas)
;=> 8
```
</section>

<section ng-controller="NarrativeController">
#### Asignando resultados a símbolos <button class="link" ng-bind-html="details" ng-model="block181" ng-click="block181=!block181"></button>

> Como se puede ver en el ejemplo de abajo, las asignaciones no están limitadas
> a valores simples. Es posible asignar un nombre al resultado de cualquier
> operación. Además, la última línea del ejemplo muestra cómo utilizar un
> símbolo para referirse al valor que le fue asignado.
{: ng-show="block181" .description}

```clojure
(def frutas (+ mangos naranjas))
(def promedio-frutas (/ frutas 2))
promedio-frutas
;=> 4
```
</section>

<section>
#### EJERCICIO 1: Aritmética básica

* ¿Cuántos minutos pasaron desde que llegaste al curso?
* Convertir el resultado de minutos a segundos.
</section>

<section>
#### EJERCICIO 2 [BONUS]: Minutos y segundos

* Convertir 1000 segundos a minutos y segundos.
* Utilizar números separados para los minutos y los segundos.
* `(quot x y)` te da el cociente de dividir x por y.
* `(rem x y)` te da el resto de dividir x por y.
</section>

{% comment %}

:star2: El link siguiente es sólo para para los slides. Andá al[README.md](../README.md). :star2:

{% endcomment %}

<section>
Volvé al <a href="javascript:;" onClick="Reveal.slide(1);">primer slide</a>,
o andá al [outline del curriculum](/curriculum/es/#/1).
</section>
