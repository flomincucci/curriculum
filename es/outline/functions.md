---
layout: default
title: Funciones
permalink: /es/outline/functions.html
---

{::options parse_block_html="true" /}

{% comment %}

http://clojurebridge.github.io/curriculum/outline/functions.html

{% endcomment %}

<section>
Funciones
-------------------------------
{: .slide-title .chapter}

* ¿Qué son las funciones?
* Nombrando funciones
* [bonus] Funciones que reciben otras funciones
    - `map` y `reduce`
* [bonus] Funciones anónimas
* [bonus] Asignación con `let`
</section>

<section ng-controller="NarrativeController">
### ¿Qué son las funciones?
{: .slide_title .slide}

#### <button class="link" ng-model="block11" ng-click="block11=!block11">Introducción</button>

> Ya has visto algunas funciones, como `count`, `conj`,
> `first`, y `rest`. También usamos funciones en toda la arimética que 
> hicimos hasta ahora: `+`, `-`, `*`, y `/`. 
> ¿Pero qué significa ser una función?
{: ng-show="block11" .description}

> Una *función* es una porción de código discreta e independiente, que recibe algunos
> valores (llamados *parámetros* o *argumentos*)), y devuelve un valor.
{: ng-show="block11" .description}

> Referencia: [Basics of Function](http://clojurebridge.github.io/community-docs/docs/clojure/function-creation/)
{: ng-show="block11" .description}

* `count`, `conj`, `first`
* `+`, `-`, `*`, `/`
* Una porción de código que recibe valores y devuelve un valor
</section>

<section ng-controller="NarrativeController">
#### Un ejemplo de función <button class="link" ng-bind-html="details" ng-model="block21" ng-click="block21=!block21"></button>

> * `defn` indica que vamos a definir una función.
> * `forward-right` es el *nombre* de esta función.
> * La cadena de texto en la siguiente línea es la documentación de la función,
>   que explica qué hace la función. Esta línea es opcional.
> * `[turtle]` es la lista de *argumentos*. Aquí tenemos un argumento llamado `turtle`.
> * `(forward turtle 60) (right turtle 135)` es el *cuerpo* de la función.
>   Esto es lo que se ejecuta cuando usamos la función.
{: ng-show="block21" .description}

```clojure
(defn forward-right
  "Mueve la tortuga especificada a la derecha e inclina su cabeza"
  [turtle]
  (forward turtle 60)
  (right turtle 135))
```
</section>

<section ng-controller="NarrativeController">
#### Cómo usar la función `forward-right` <button class="link" ng-bind-html="details" ng-model="block31" ng-click="block31=!block31"></button>

> Para usar `forward-right`, *invocamos* la función, como hicimos con todas las funciones que ya hemos utilizado.
{: ng-show="block31" .description}

```clojure
(forward-right :trinity)  ;=> {:trinity {:angle 135}}
(forward-right :neo) ;=> {:neo {:angle 135}}
```
</section>

<section ng-controller="NarrativeController">
#### Una función con múltiples argumentos <button class="link" ng-bind-html="details" ng-model="block41" ng-click="block41=!block41"></button>

> Las funciones también pueden tomar más de un argumento. Hagamos
> una función `forward-right-with-len` que además de la tortuga,
> recibe una distancia hacia adelante.
{: ng-show="block41" .description}

```clojure
(defn forward-right-with-len
  "Dados turtle y length, adelanta turtle e inclina su cabeza"
  [turtle len]
  (forward turtle len)
  (right turtle 135))

(forward-right-with-len :trinity 90) ;=> {:trinity {:angle 135}}
(forward-right-with-len :neo 80)  ;=> {:neo {:angle 135}}
```
</section>

<section>
#### EJERCICIO 1: Mover tortugas con funciones
{: .slide_title .slide}

1. Escribir una función
  * Ve a `walk.clj`
  * En el editor, escribe la función `forward-right` que apareció en la presentación (abajo).
  * (Optional) Guarda `walk.clj`
  * Selecciona la función `forward-right` entera y pulsa "Eval Selection"
2. Usa una función
  * Escribe `(forward-right :trinity)` en el panel del REPL.
  * Repite el paso anterior al menos 8 veces (utiliza la flecha hacia arriba y pulsa Enter).

```clojure
(defn forward-right
  "Mueve a la derecha a la tortuga especificada e inclina su cabeza"
  [turtle]
  (forward turtle 60)
  (right turtle 135))
```
</section>

<section>
#### EJERCICIO 2: Mover tortugas usando funciones con parámetros
{: .slide_title .slide}

* Ve a `walk.clj`
* En el editor, escribe la función `forward-right-with-len-ang` que recibe tres 
  argumentos: turtle, len, y angle (extensión de `forward-right-with-len`)
* Selecciona la función `forward-right-with-len-ang` entera y pulsa Reload Selection.
* En el panel del REPL, escribe `(forward-right-with-len-ang :trinity 60 120)`
* Repite lo anterior, evaluando varias veces la función en el REPL..
</section>


<section ng-controller="NarrativeController">
### Nombrando funciones
{: .slide_title .slide}

#### Los nombres son símbolos <button class="link" ng-bind-html="details" ng-model="block61" ng-click="block61=!block61"></button>

> Los nombres de funciones son símbolos, al igual que los símbolos definidos con `def`
> cuando asignamos nombres a valores.
{: ng-show="block61" .description}

> Los símbolos deben comenzar con un carácter no numérico, y pueden contener 
> carácteres alfanuméricos, *, +, !, -, _, y ?.
> Esta flexibilidad es importante con las funciones, ya que hay ciertas formas de 
> expresiones que usaremos.
{: ng-show="block61" .description}

#### Dos clases de funciones <button class="link" ng-bind-html="details" ng-model="block62" ng-click="block62=!block62"></button>

> Clojure tiene dos clases de funciones:
> 1. función que devuelve un valor
> 2. función que devuelve true o false
> A las funciones de la segunda clase se las llama *predicado*s.
{: ng-show="block62" .description}


##### Ejemplos de funciones predicado <button class="link" ng-bind-html="details" ng-model="block63" ng-click="block63=!block63"></button>

> En Clojure, `=` es una función predicado, lo cual puede ser un hecho
> sorprendente. Además, como muchos otros lenguajes, Clojure tiene funciones
> predicado para probar mayor o igual, menor o igual, etc.
> Mayormente las funciones predicado terminan con `?`.
{: ng-show="block63" .description}

> * `=`, `not=`
> * `>`, `<`, `>=`, `<=`
> * `true?`, `false?`, `empty?`, `nil?`, `vector?`, `map?`

</section>

<section ng-controller="NarrativeController">
#### [Bonus ]

### Funciones que reciben otras funciones
{: .slide_title .slide}

#### <button class="link" ng-model="block71" ng-click="block71=!block71">Introducción</button>

> Algunas de las funciones más poderosas que puedes utilizar con colecciones
> pueden tomar otras funciones como argumentos.
> Ésta es una de las cosas más mágicas acerca de Clojure--y varios otros lenguajes de programación.
> Ésta es una idea complicada, así que puede no parecer tener mucho sentido al principio.
> Veamos un ejemplo para aprender más sobre esto.
{: ng-show="block71" .description}

> Referencia: [Higher-order Function](http://clojurebridge.github.io/community-docs/docs/clojure/higher-order-function/)
{: ng-show="block71" .description}
</section>

<section ng-controller="NarrativeController">
#### La función `map`

#### <button class="link" ng-bind-html="details" ng-model="block101" ng-click="block101=!block101"></button>

> `map` es una función que recibe otra función y una colección.
> `map` invoca la función recibida en cada elemento de la colección, y luego
> devuelve una nueva colección con los resultados de esas invocaciones.
> Éste es un concepto extraño, pero es uno de los conceptos más importantes
> de Clojure y de la programación funcional en general.
{: ng-show="block101" .description}

```clojure
(map inc [1 2 3]) ;=> (2 3 4)
(map (partial + 90) [0 30 60 90]) ;=> (90 120 150 180)
```

> Referencias:
> [partial](http://clojuredocs.org/clojure.core/partial)
</section>

<section ng-controller="NarrativeController">
#### La función `reduce`

#### <button class="link" ng-bind-html="details" ng-model="block111" ng-click="block111=!block111"></button>

> Veamos otra función que recibe una función. Esta función es
> `reduce`, y se usa para convertir colecciones en un único valor.
{: ng-show="block111" .description}

> `reduce` recibe los dos primeros elementos de la colección que recibió,
> e invoca la función provista sobre esos elementos. Luego, vuelve a invocar
> la misma función -- sólo que esta vez lo hace usando el resultado de la 
> invocación anterior, junto con el siguiente elemento de la colección.
> `reduce` hace esto repetidamente hasta que finalmente llega al final de la
> colección.
{: ng-show="block111" .description}

```clojure
(reduce str (turtle-names)) ;=> ":trinity:neo:oracle:cypher"
(reduce + [30 60 90])       ;=> 180
```
</section>

<section>
#### EJERCICIO 3 [BONUS]: Calcular el promedio
{: .slide_title .slide}

* Crea una función llamada `average` que reciba un vector de mapas.
* Usa `[{:angle 30} {:angle 90} {:angle 50}]` como vector de entrada.
* Calcula el valor de :angle.

* Pista: Necesitarás utilizar las funciones `map`, `reduce` y `count`.
</section>


<section ng-controller="NarrativeController">
#### [Bonus]

### Funciones anónimas

#### Funciones sin nombre <button class="link" ng-bind-html="details" ng-model="block201" ng-click="block201=!block201"></button>

> Hasta ahora, todas las funciones que vimos tenían nombres, como `+`,
> `str` y `reduce`. Pero las funciones no necesitan nombres, de la misma 
> manera que los valores no necesitan nombres.
> A las funciones que no tienen nombre las llamamos *funciones anónimas*.
> Una función anónima se crea con `fn`, de esta forma:
{: ng-show="block201" .description}

> Referencia: [Anonymous Function](http://clojurebridge.github.io/community-docs/docs/clojure/anonymous-function/)
{: ng-show="block201" .description}


```clojure
(fn [s1 s2] (str s1 " " s2))
```

#### vs. funciones no anónimas <button class="link" ng-bind-html="details" ng-model="block202" ng-click="block202=!block202"></button>

> Antes de continuar, debes entender que _siempre_ eres libre de 
> nombrar tus funciones. Hacer eso no tiene nada de malo.
> Sin embargo, hay muchísimo código Clojure con funciones anónimas,
> por lo que deberías ser capaz de entenderlo.
{: ng-show="block202" .description}

```clojure
(defn join-with-space
  [s1 s2]
  (str s1 " " s2))
```
</section>

<section ng-controller="NarrativeController">
#### Ejemplos de uso de funciones anónimas <button class="link" ng-bind-html="details" ng-model="block203" ng-click="block203=!block203"></button>

> Por qué querrías usar funciones anónimas?
> Las funciones anónimas pueden ser muy útiles cuando tenemos
> funciones que reciben otras funciones, como `map` o `reduce`, 
> de las cuales ya aprendimos en la sección sobre Funciones.
> Veamos ejemplos de uso de funciones anónimas:
{: ng-show="block203" .description}

```clojure
(map (fn [t] (forward t 45)) (turtle-names))
;=> ({:trinity {:length 45}} {:neo {:length 45}} {:oracle {:length
45}} {:cypher {:length 45}})

(reduce (fn [x y] (+ x y)) [1 2 3]) ;=> 6

(reduce (fn [a b] (str a ", " b)) (map name (turtle-names)))
;=> "trinity, neo, oracle, cypher"
```
</section>

<section ng-controller="NarrativeController">
#### [Bonus]

### Asignación con `let`
{: .slide_title .slide}

#### <button class="link" ng-model="block301" ng-click="block301=!block301">Intro</button>

> Cuando estás creando funciones, puedes querer asignar nombres a
> valores para poder reutilizar esos valores o hacer tu código más
> legible. Sin embargo, dentro de una función, _no_ deberías usar 
> `def` como lo harías fuera de una función. En lugar de eso, 
> deberías usar una forma especial llamada `let`.
{: ng-show="block301" .description}
</section>

<section ng-controller="NarrativeController">
#### Asignando nombres a valores: `let`
{: .slide_title .slide}

#### <button class="link" ng-bind-html="details" ng-model="block305" ng-click="block305=!block305"></button>

> Podemos asignar un nombre a un valor utilizando `let`, como `def`.
> Cuando un nombre es asignado a un valor, el nombre se llama *símbolo.
{: ng-show="block305" .description}

> Referencia: [Assignment let](http://clojurebridge.github.io/community-docs/docs/clojure/let/)
{: ng-show="block305" .description}

```clojure
(let [mangoes 3
      oranges 5]
  (+ mangoes oranges))
;=> 8
```
</section>

<section ng-controller="NarrativeController">
#### Ejemplo de `let`

<button class="link" ng-bind-html="details1" ng-model="block311" ng-click="block311=!block311"></button>
<button class="link" ng-bind-html="details2" ng-model="block312" ng-click="block312=!block312"></button>
<button class="link" ng-bind-html="details3" ng-model="block313" ng-click="block313=!block313"></button>
<button class="link" ng-bind-html="exercise" ng-model="block314" ng-click="block314=!block314"></button>

> Esta es la función más complicada que hemos visto hasta ahora, así que 
> vamos paso por paso. Primero, tenemos el nombre de la función, el string
> de documentación, y los argumentos, igual que en otras funciones.
{: ng-show="block311" .description}

> Luego, vemos `let`. `let` recibe un vector de nombres y valores intercalados.
> `t1` es le primer nombre, y le asignamos el resultado de `(first names)`.
> También le asignamos el resultado de `(last names)` a `t2`.
{: ng-show="block312" .description}

> Luego del vector de nombres y valores, está el cuerpo del `let`.
> Igual que el cuerpo de una función, éste se ejecuta y devuelve un valor
> Dentro del `let`, `t1` and `t2` están definidos.
{: ng-show="block313" .description}

> Ve a `walk.clj` y escribe la función `opposite`.
> Luego, evalúa la función `opposite` en la última línea de la definición de la función.
> También, evalúa el ejemplo de uso de la función `opposite`.
{: ng-show="block314" .description}

```clojure
;; function definition
(defn opposite
  "Dada una coleción de nombres de tortugas, mueve dos de ella en direcciones diferentes."
  [names]
  (let [t1 (first names)
        t2 (last names)]
    (forward t1 40)
    (backward t2 30)))

;; function usage
(opposite (turtle-names))
```
</section>

{% comment %}

:star2: Un enlace más abajo es únicamente para una diapositiva. Ve a [README.md](../README.md)
:star2:

{% endcomment %}

<section>
Vuelve a la <a href="javascript:;" onClick="Reveal.slide(1);">primera diapositiva</a>,
o ve al [outline del currículum](/curriculum/#/1).
</section>
