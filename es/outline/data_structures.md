---
layout: default
title: Vectores y Mapas
permalink: /es/outline/data_structures.html
---

{::options parse_block_html="true" /}

{% comment %}

http://clojurebridge.github.io/curriculum/outline/data_structures.html

{% endcomment %}

<section>
Estructuras de Datos
----------------------------------------
{: .slide-title .chapter}

* Vectores
* Mapas
</section>

<section>
### Grupo de datos - Colecciones
{: .slide_title .slide}

#### <button class="link" ng-model="block11" ng-click="block11=!block11">Introducción</button>

> Hasta ahora, vimos piezas discretas de datos: un número, una
string, un valor. Cuando programamos, es más frecuente que
queramos trabajar con grupos de datos.
{: ng-show="block11" .description}

> Clojure tiene excelentes herramientas para trabajar con estos grupos,
o *colecciones*, de datos. No solo nos proveé con cuatro tipos distintos
de colecciones, sino también de una manera uniforme de usarlas.
{: ng-show="block11" .description}
</section>

<section ng-controller="NarrativeController">
### Vectores
{: .slide_title .slide}

#### Colección secuencial <button class="link" ng-bind-html="details" ng-model="block21" ng-click="block21=!block21"></button>

> Un vector es una colección secuencial de valores. Un vector puede
estar vacío. Un vector puede contener valores de tipos distintos.
Cada valor en un vector está numerado empezando en 0, a ese número
se lo llama su índice. El índice se usa para referenciar a cada valor
cuando se lo quiere buscar.
{: ng-show="block21" .description}

#### Estructura como compartimento <button class="link" ng-bind-html="details" ng-model="block22" ng-click="block22=!block22"></button>

> Para imaginarte un vector, imaginá una caja dividida en algún número
de compartimentos del mismo tamaño. Cada compartimento tiene un número.
Podes poner un dato adentro de cada compartimento y siempre saber donde
encontrarlo, ya que tiene un número.
{: ng-show="block22" .description}

> Notá que los números empiezan en el 0. Esto puede resultar extraño,
pero es común contar desde 0 cuando programamos.
{: ng-show="block22" .description}

![Vector](/outline/img/vector.png)

</section>

<section ng-controller="NarrativeController">
#### Sintaxis <button class="link" ng-bind-html="details" ng-model="block31" ng-click="block31=!block31"></button>

> Los vectores se escriben usando corchetes, con cualquier cantidad de
datos adentro, separados por espacios. Estos son algunos ejemplos de vectores:
{: ng-show="block31" .description}

```clojure
[1 2 3 4 5]
[56.9 60.2 61.8 63.1 54.3 66.4 66.5 68.1 70.2 69.2 63.1 57.1]
[]
```
</section>

<section ng-controller="NarrativeController">
#### Ejemplo <button class="link" ng-bind-html="details" ng-model="block41" ng-click="block41=!block41"></button>

> Cuando hay una pareja de tortugas, el comando `(turtle-names)`
devuelve los nombres de las tortugas como un vector:
{: ng-show="block41" .description}

```clojure
(turtle-names)
;=> [:trinity :neo :oracle :cypher]
```
</section>


<section ng-controller="NarrativeController">
#### Creación <button class="link" ng-bind-html="details" ng-model="block61" ng-click="block61=!block61"></button>

> Las siguientes dos funciones se usan para crear vectores. La función
`vector` toma cualquier cantidad de elementos y los pone en un
nuevo vector. `conj` es una función interesante que verás siendo usada
con todas las estructuras de datos. Con los vectores, toma un vector y un elemento,
y devuelve un nuevo vector con ese elemento agregado al final del vector original.
¿Por qué el nombre `conj`? `conj` es abreviatura de `conjoin`, que significa
unir o combinar. Eso es lo que hacemos: estamos uniendo el nuevo elemento al vector.
{: ng-show="block61" .description}

```clojure
(vector 5 10 15)
;=> [5 10 15]

(conj [5 10] 15)
;=> [5 10 15]
```
</section>

<section ng-controller="NarrativeController">
#### Extracción <button class="link" ng-bind-html="details" ng-model="block81" ng-click="block81=!block81"></button>

> Ahora, mira estas cuatro funciones. `count` nos dice cuantos elementos
hay en un vector. `nth` nos da el enésimo elemento del vector. Notá que
empezamos contando en 0, por lo que en el ejemplo, llamar `nth` con
el número 1 nos devuelve lo que llamaríamos el segundo elemento
cuando no estamos programando. `first` devuelve el primer elemento
en la colección. `rest` devuelve todos excepto el primero. Tratá de
no pensar en eso y `nth` al mismo tiempo, porque puede ser confuso.
{: ng-show="block81" .description}

```clojure
(count [5 10 15])
;=> 3
(nth [5 10 15] 1)
;=> 10
(first [5 10 15])
;=> 5
(rest [5 10 15])
;=> (10 15)
```
</section>

<section>
#### EJERCICIO 1: Ver los nombres de las tortugas
{: .slide_title .slide}

1. Agregá una tortuga con una pieza de código en el archivo
  * Abrí el archivo `walk.clj`
  * Agregá una linea: `(add-turtle :neo)` en la última linea del archivo
  * Seleccioná esta linea y clickeá "Reload Selection"
2. (Opcional) agregá una tortuga usando el REPL
  * Tipeá `(add-turtle :oracle)` seguido de enter en el panel del REPL de abajo
3. Ver los nombres de las tortugas
  * Tipeá `(turtle-names)` en el panel del REPL de abajo y mirá el resultado
</section>

<section>
#### EJERCICIO 2: Crear un vector
{: .slide_title .slide}

* Ve a `core.clj` en `myproject` y prendé el InstaREPL
* Creá un vector de las temperaturas máximas de los próximos 7 días
de la ciudad donde vivís
* Luego usá la función `nth` para obtener la temperatura máxima del próximo
Martes
</section>


<section ng-controller="NarrativeController">
### Mapas

#### Pares clave valor <button class="link" ng-bind-html="details" ng-model="block101" ng-click="block101=!block101"></button>

> Los mapas contienen un conjunto de claves y valores asociados a estas.
Podés pensarlo como un diccionario: buscas cosas usando una palabra
(la palabra clave) y ves la definición (el valor). Si programaste en
otro lenguaje, habrás visto algo como los mapas--quizás llamados
diccionarios, hashes, o arrays asociativos.
{: ng-show="block101" .description}

![Mapa](/outline/img/map.png)
</section>

<section ng-controller="NarrativeController">
#### Sintaxis <button class="link" ng-bind-html="details" ng-model="block102" ng-click="block102=!block102"></button>

> Escribimos los mapas encerrando claves y valores alternados entre llaves, así.
{: ng-show="block102" .description}

> Los mapas son útiles porque contienen datos de la forma que normalmente
lo pensamos. Tomá nuestro ejemplo inventado, Sally Brown. Un mapa puede contener
su nombre y su apellido, su dirección, su comida favorita,
o cualquier otra cosa. Es una forma sencilla de juntar esos datos y hacerlos
fácil de buscar. El último ejemplo es un mapa vacío. Es un mapa listo para
contener cosas, pero que no tiene nada todavía.
{: ng-show="block102" .description}

```clojure
{:first "Sally" :last "Brown"}
{:a 1 :b "two"}
{}
```
</section>

<section ng-controller="NarrativeController">
#### Ejemplo <button class="link" ng-bind-html="details" ng-model="block103" ng-click="block103=!block103"></button>

> Cuando una tortuga recibe un comando como `forward` o `right`,
devuelve el resultado como un mapa con un mapa adentro.
{: ng-show="block103" .description}

```clojure
(forward 40)
;=> {:trinity {:length 40}}
(right 90)
;=> {:trinity {:angle 90}}
```
</section>

<section ng-controller="NarrativeController">
#### Creación <button class="link" ng-bind-html="details" ng-model="block104" ng-click="block104=!block104"></button>

> `assoc` y `dissoc` hacen pareja: asocian y desasocian elementos
de un mapa. Mirá como agregamos el apellido "Brown" al mapa con `assoc`,
y después lo removemos con `dissoc`. `merge` junta dos mapas y crea
uno nuevo.
{: ng-show="block104" .description}

```clojure
(assoc {:first "Sally"} :last "Brown")
;=> {:first "Sally", :last "Brown"}

(dissoc {:first "Sally" :last "Brown"} :last)
;=> {:first "Sally"}

(merge {:first "Sally"} {:last "Brown"})
;=> {:first "Sally", :last "Brown"}
```
</section>

<section ng-controller="NarrativeController">
#### Extracción 1 <button class="link" ng-bind-html="details" ng-model="block105" ng-click="block105=!block105"></button>

> `count`, toda colección tiene esta función. ¿Por qué creés que la respuesta es dos?
`count` devuelve la cantidad de asociaciones.
{: ng-show="block105" .description}

> Ya que un mapa es un par de claves y valores, la clave se usa para
obtener un valor de un mapa. Una de las formas usuales en Clojure
es como en el ejemplo debajo. Podemos usar una clave como una función
para buscar valores en un mapa. En el último ejemplo, pusimos la
clave `:MISS`. Esto funciona para cuando la clave que buscamos no está en el mapa.
{: ng-show="block105" .description}

```clojure
(count {:first "Sally" :last "Brown"})
;=> 2

(get {:first "Sally" :last "Brown"} :first)
;=> "Sally"
(get {:first "Sally"} :last)
;=> nil


(get {:first "Sally"} :last :MISS)
;=> :MISS
```
</section>

<section ng-controller="NarrativeController">
#### Extracción 2 <button class="link" ng-bind-html="details" ng-model="block106" ng-click="block106=!block106"></button>

> Luego tenemos `keys` y `vals`, que son bastante sencillas: devuelven las
claves y los valores en un mapa. El orden no está garantizado,
por lo que podríamos haber obtenido `(:first :last)` o `(:last :first)`.
{: ng-show="block106" .description}

```clojure
(keys {:first "Sally" :last "Brown"})
;=> (:first :last)

(vals {:first "Sally" :last "Brown"})
;=> ("Sally" "Brown")
```
</section>

<section ng-controller="NarrativeController">
#### Actualizar <button class="link" ng-bind-html="details" ng-model="block110" ng-click="block110=!block110"></button>

> Luego de crear un mapa, queremos asignar un nuevo valor a una clave
existente. La función `assoc` se puede usar para esto.
> También, existe la práctica función `update`. Esta toma un mapa, una clave
y una función. El valor de la clave será el primer argumento de la función dada.
> La función `update-in` funciona como `update`, pero toma un vector de claves
como camino en un mapa anidado.
{: ng-show="block110" .description}

```clojure
(def hello {:count 1 :words "hello"})

(update hello :count inc)
;=> {:count 2, :words "hello"}
(update hello :words str ", world")
;=> {:count 1, :words "hello, world"}


(def mine {:pet {:age 5 :name "able"}})

(update-in mine [:pet :age] - 3)
;=> {:pet {:age 2, :name "able"}}
```
</section>


<section>
### Colecciones de Colecciones

#### <button class="link" ng-model="block101" ng-click="block101=!block101">Introducción</button>

> Valores simples como números, claves y strings no son los únicos
tipos de cosas que podes poner en las colecciones, así que podes tener un vector
de mapas, o una lista de vectores, o cualquiera sea la combinación que se ajuste
a tus datos.
{: ng-show="block101" .description}
</section>

<section>
#### Vectores de Mapas

```clojure
(state-all)
;=> [{:trinity {:x -1.7484556000744965E-6, :y 39.99999999999996, :angle 90, :color [106 40 126]}}
{:neo {:x 21.213202971967114, :y 21.213203899225725, :angle 45, :color [0 64 0]}}
{:oracle {:x -49.99999999999981, :y -4.3711390001862375E-6, :angle 180, :color [43 101 236]}}]

(def states (state-all))
;=> #'clojurebridge-turtle.walk/states

(first states)
;=> {:trinity {:x -1.7484556000744965E-6, :y 39.99999999999996,
:angle 90, :color [106 40 126]}}
```
</section>

<section>
#### Mapa de Mapas

```clojure
(def st (first states))
;=> #'clojurebridge-turtle.walk/st

st
;=> {:trinity {:x -1.7484556000744965E-6, :y 39.99999999999996,
;=>            :angle 90, :color [30 30 30]}}

(get st :trinity)
;=> {:x -1.7484556000744965E-6, :y 39.99999999999996,
;=>  :angle 90, :color [30 30 30]}

(get-in st [:trinity :angle])
;=> 90
```
</section>


<section>
#### EJERCICIO 3: Ver los estados de las tortugas
{: .slide_title .slide}

* Abrí el archivo `walk.clj`
* Probá los ejemplos de las dos previas diapositivas en el REPL
* Notá que valores obtenés

> No te olvides de apretar __enter__ cuando escribís código en el REPL


```clojure
(state-all)
(def states (state-all))
(first states)
(def st (first states))
st
(get st :trinity)
(get-in st [:trinity :angle])
```
</section>

<section>
#### EJERCICIO 4: Modelarse a uno mismo
{: .slide_title .slide}

* Ve a `core.clj` en `myproject` y prendé el InstaREPL
* Hacé un mapa que te represente a vos mismo
* Asegurate de que contenga tu nombre y apellido
* Luego, agregá tu ciudad natal al mapa usando [assoc](http://grimoire.arrdem.com/1.6.0/clojure.core/assoc/) o [merge](http://grimoire.arrdem.com/1.6.0/clojure.core/merge/)
</section>

<section>
#### EJERCICIO 5 [BONUS]: Modelar a tus compañeros
{: .slide_title .slide}

* Primero, tomá el mapa que hiciste de vos mismo en el ejercicio anterior
* Luego, creá un vector de mapas que contenga el nombre, apellido y ciudad natal
de dos o tres compañeros cerca tuyo
* Finalmente, añadí tu mapa a esta información usando [conj](http://grimoire.arrdem.com/1.6.0/clojure.core/conj/)
</section>

{% comment %}

:star2: El link siguiente es para un slide solo. Andá al[README.md](../README.md). :star2:

{% endcomment %}

<section>
Volvé al <a href="javascript:;" onClick="Reveal.slide(1);">primer slide</a>,
o andá al [outline del curriculum](/curriculum/es/#/1).
</section>
