---
layout: default
title: Control de Flujo
permalink: /es/outline/flow_control.html
---

{::options parse_block_html="true" /}

{% comment %}

http://clojurebridge.github.io/curriculum/es/outline/flow_control.html

{% endcomment %}

<section>
Control de Flujo
-------------------------
{: .slide-title .chapter}

* `if`
* `cond`
* Lógica booleana
</section>

<section ng-controller="NarrativeController">
### Qué es el Control de Flujo?
{: .slide_title .slide}

#### Decidir y reaccionar <button class="link" ng-bind-html="details" ng-model="block11" ng-click="block11=!block11"></button>

> "Control de Flujo" es el término usado en programación para decidir cómo
> reaccionar ante una dada circunstancia. Tomamos decisiones de esta manera
> todo el tiempo. *Si* (if) es un lindo día, *entonces* (then) deberíamos
> ir la parque. *Si no* (else) deberíamos quedarnos y jugar juegos de mesa.
> *Si* el tanque está vacío, *entonces* deberías ir a cargar nafta, *si no*
> deberías continuar hasta tu lugar de destino.
{: ng-show="block11" .description}

#### Testeando condiciones para reaccionar <button class="link" ng-bind-html="details" ng-model="block12" ng-click="block12=!block12"></button>

> El software está lleno de este tipo de decisiones. *Si* el input del
> usuario es válido, *entonces* guardamos sus datos; *si no* le
> mostramos un mensaje de error. El patrón común es que verificás una
> condición y reaccionás de forma diferente basado en si la condición
> da *verdadero* (true) o *falso* (false).
{: ng-show="block12" .description}
</section>

<section ng-controller="NarrativeController">
### `if`
{: .slide_title .slide}

<button class="link" ng-bind-html="details1" ng-model="block21" ng-click="block21=!block21"></button>
<button class="link" ng-bind-html="details2" ng-model="block22" ng-click="block22=!block22"></button>

> En Clojure, la herramienta más básica que tenemos para Control de Flujo es
> el operador *if*. Acá hay un ejemplo de cómo podrías programar un escenario
> de validación de ciertos datos de entrada:
{: ng-show="block21" .description}

> Ejemplo: Si luego de sumar 40 a `y` da menos de 150, entonces se debe retornar
> `(+ y 40)`; si no, retornar -150. (esto es para la app de la tortuga,
> el borde superior del marco está en 150 en y, y el inferior en -150 en y.)
{: ng-show="block22" .description}

> Referencia: [Condicional `if`](http://clojurebridge.github.io/community-docs/docs/clojure/if/)
{: ng-show="block22" .description}

```clojure
(if (< (+ y 40) 150)
  (+ y 40)
  -150))
```
</section>

<section ng-controller="NarrativeController">
#### Forma general del operador `if`

```clojure
(if conditional-expression
  expression-to-evaluate-when-true
  expression-to-evaluate-when-false)
```
</section>

<section ng-controller="NarrativeController">
#### Ejemplos de `if`

```clojure
(if (> 3 1)
  "3 es mayor que 1"
  "3 no es mayor que 1")
;=> "3 es mayor que 1"

(if (> 1 3)
  "1 es mayor que 3"
  "1 no es mayor que 3")
  ;=> "1 no es mayor que 3"
```
</section>

<section ng-controller="NarrativeController">
#### Valor de verdad (Truthiness?) <button class="link" ng-bind-html="details" ng-model="block51" ng-click="block51=!block51"></button>

> Al testear el valor de verdad de una expresión, Clojure considera los
> valores `nil` y `false` como falso y cualquier otro valor como verdadero.
> Acá hay algunos ejemplos:
{: ng-show="block51" .description}

> Referencia: [Truthiness/Valor de verdad](http://clojurebridge.github.io/community-docs/docs/clojure/truthiness/)
{: ng-show="block51" .description}


```clojure
(if "cualquier valor aparte de nil y false es considerado verdadero"
  "Un string es considerado verdadero"
  "Un string no es considerado verdadero")
;=> "Un string es considerado verdadero"

(if nil
  "nil es considerado verdadero"
  "nil no es considerado verdadero")
;=> "nil no es considerado verdadero"

(if (get {:a 1} :b)
  "las expresiones que evalúan a nil son consideradas verdaderas"
  "las expresiones que evalúan a nil no son consideradas verdaderas")
;=> "las expresiones que evalúan a nil no son consideradas verdaderas"
```
</section>

<section>
#### Ejercicio 1: Valor de y dentro de un marco
{: .slide_title .slide}

* Escribir una función `y-within-frame` que recibe y (posición vertical) como argumento.
* Podés usar alguno de los ejemplos de if del slide.
* La función debe devolver un valor de y que no sea mayor a 150.

    - Ver: [x, y en valores absolutos](https://github.com/ClojureBridge/welcometoclojurebridge/blob/master/outline/TURTLE.md#x-and-y-in-absolute-values)

```clojure
;; ejemplo de if
(if (< (+ y 40) 150)
  (+ y 40)
  -150))
```

```clojure
;; uso de la función y-within-frame
(y-within-frame 80)    ;=> 120
(y-within-frame 180)   ;=> -150
```
</section>

<section ng-controller="NarrativeController">
### `cond`
{: .slide_title .slide}

<button class="link" ng-bind-html="details1" ng-model="block61" ng-click="block61=!block61"></button>
<button class="link" ng-bind-html="details2" ng-model="block62" ng-click="block62=!block62"></button>

> El operador `if` toma un sólo predicado.
> Cuando queremos usar múltiples predicados, `if` no es una buena opción.
> Tenemos que anidar, anidar... y anidar condiciones `if`.
> Para contemplar múltiples situaciones, el operador `cond` funciona bien.
{: ng-show="block61" .description}

> Acá va el ejemplo. Si sumando 40 a `y` da más que 150, evaluar la primer
> forma. En este caso, devuelve -150. Si sumando 40 a `y` da menos que -150,
> evaluar la segunda forma. En este caso, devuelve 150. Si los dos
> predicados retornan falso, evaluar la forma `:else`. In este caso,
> retorna `y` más 40. Si usamos esta función en la app de la tortuga,
> podemos mantener a nuestra tortuga entre el borde superior e inferior
> del marco.
{: ng-show="block62" .description}

> Referencia: [Condicional `cond`](http://clojurebridge.github.io/community-docs/docs/clojure/cond/)
{: ng-show="block62" .description}

```clojure
(cond
  (> (+ y 40) 150) -150
  (< (+ y 40) -150) 150
  :else (+ y 40)))
```
</section>

<section ng-controller="NarrativeController">
#### Forma general del operador `cond`

```clojure
(cond
  predicate1 expression-to-evaluate-when-predicate1-is-true
  predicate2 expression-to-evaluate-when-predicate2-is-true
  ...
  :else expression-to-evaluate-when-all-above-are-false)
```
</section>

<section>
#### Ejercicio 2: Valor de y dentro del marco - parte 2
{: .slide_title .slide}

> La función que escribimos en el ejercicio anterior, `y-within-frame`,
> tiene un problema. Si el valor de y es -1000, la función retorna -960.
> Dado que el valor de y del borde inferior del marco es -150, -960 queda
> afuera del marco. Tu tortuga va a quedar en un área invisible. Hagamos
> que la función sea realmente within-frame usando `cond`.

* Escribir una función `y-within-frame-cond` que recibe y (posición vertical) como argumento.
* Podés usar el ejemplo de `cond` del slide.
* La función debe retornar un valor de y entre -150 y 150.

    - Ver: [x e y en valores absolutos](https://github.com/ClojureBridge/welcometoclojurebridge/blob/master/outline/TURTLE.md#x-and-y-in-absolute-values)

```clojure
;; uso de la función y-within-frame-cond
(y-within-frame-cond 200)    ;=> -150
(y-within-frame-cond -200)   ;=> 150
(y-within-frame-cond 0)      ;=> 40
```
</section>

<section ng-controller="NarrativeController">
### Lógica booleana con `and`, `or`, y `not`
{: .slide_title .slide}

#### <button class="link" ng-model="block81" ng-click="block81=!block81">Intro</button>

> Las sentencias `if` no están limitadas a verificar sólo una cosa. Podés
> verificar múltiples condiciones usando lógica booleana. La _Lógica booleana_ se refiere
> a combinar y cambiar el resultado de predicados usando `and`, `or`, y `not`.
{: ng-show="block81" .description}

> Si nunca antes viste este concepto en programación, recordá que sigue
> el sentido común de cómo ves las cosas normalmente. Es esto y aquello verdadero?
> Sólo si ambos son verdaderos. Es esto o aquello verdadero? Sí, si cualquiera
> de ellos -- o ambos! -- lo son. Es esto _no_ verdadero? Sí, si es falso.
{: ng-show="block81" .description}
</section>

<section ng-controller="NarrativeController">
### Tabla de verdad <button class="link" ng-bind-html="details" ng-model="block91" ng-click="block91=!block91"></button>

> `and`, `or`, y `not` funcionan como otras funciones (no son
> exactamente funciones, pero funcionan como si lo fueran), entonces
> se usan con _notación prefija_, tal como vimos con los operadores
> aritméticos.
{: ng-show="block91" .description}

| x     | y     | (`and` x y) | (`or` x y) | (`not` x) | (`not` y) |
| ----- | ----- | --------- | -------- | ------- | ------- |
| false | false | false | false | true  | true  |
| true  | false | false | true  | false | true  |
| true  | true  | true  | true  | false | false |
| false | true  | false | true  | true  | false |

</section>

<section ng-controller="NarrativeController">
#### Combinaciones de `and`, `or`, y `not` <button class="link" ng-bind-html="details" ng-model="block101" ng-click="block101=!block101"></button>

> `and`, `or`, y `not` pueden ser combinados. Esto a veces puede ser
> difícil de leer. Veamos un ejemplo:
{: ng-show="block101" .description}

```clojure
(defn año-bisiesto?
  "Cada cuatro años, excepto en años divisibles por 100,
  pero sí para años divisibles por 400."
  [year]
  (and (zero? (mod year 4))
       (or (zero? (mod year 400))
           (not (zero? (mod year 100))))))
```
</section>

<section ng-controller="NarrativeController">
#### [Bonus] Combinando `cond`, `and`, `or`, y `not` <button class="link" ng-bind-html="details" ng-model="block110" ng-click="block110=!block110"></button>

> Aprendimos sobre `cond`, `and`, `or`, y `not`. Pensemos qué función podemos
> escribir combinando todos.
> Un ejemplo:
{: ng-show="block110" .description}

```clojure
(defn true-or-false?
  "Dado op, retorna true o false"
  [op]
  (let [x true
        y false]
    (cond
      (= op :and) (and x y)
      :else false)))

(defn correct?
  "Dados op y ans, retorna un mensaje indicando si ans fue correcta o no"
  [op ans]
  (if (= ans (true-or-false? op))
      "Ganaste"
      "Perdiste"))
```
</section>

<section>
#### Ejercicio 3: [Bonus] Completar la función `true-or-false?`
{: .slide_title .slide}

> La función `true-or-false?` en el slide anterior sólo "ve" la
> operación `:and`. Agregá las operaciones `:or` y `:not`.

* Usá `core.clj` de `myproject` e InstaREPL
* Agregá `(= op :or)` y `(= op :not)` en el `cond`
* Para `:not`, elegí x o y como argumento

```clojure
;; uso de la función correct?
(correct? :and false)   ;=> "Ganaste"
(correct? :or false)    ;=> "Perdiste"
(correct? :not true)    ;=> "Ganaste"  (aunque podría ser "Perdiste")
```
</section>

{% comment %}

:star2: A link below is for a slide only. Go to [README.md](../README.md)
instead. :star2:

{% endcomment %}

<section>
Volvé al <a href="javascript:;" onClick="Reveal.slide(1);">primer slide</a>,
o andá al [outline del curriculum](/curriculum/es/#/1).
</section>
