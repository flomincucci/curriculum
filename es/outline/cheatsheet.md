## Estructuras de Datos - Vector

### Creando un vector

```clj
(vector 5 10 15)
[1 2 3 4 5]
[56.9 60.2 61.8 63.1 54.3 66.4 66.5 68.1 70.2 69.2 63.1 57.1]
[]
```

#### Funciones para vectores

```clj
(vector? [5 10 15])
;=> true

(vector 5 10 15)
;=> [5 10 15]

(conj [5 10] 15)
;=> [5 10 15]

(count [5 10 15])
;=> 3

(nth [5 10 15] 1)
;=> 10

(first [5 10 15])
;=> 5
```

## Estructuras de datos 2 - Palabras claves, Mapas

#### Creando un mapa

```clj
{:nombre "Alicia" :apellido "Brown"}
{:a 1 :b "two"}
{}
```


#### Funciones para Mapas

```clj
; determina si el valor es un mapa
(map? {:nombre "Alicia" :apellido "Brown"})
;=> true

; usa la palabra clave :nombre para obtener el valor
(get {:nombre "Alicia" :apellido "Brown"} :nombre)
;=> "Sally"

; usa la palabra clave :nombre para obtener el valor y devuelve :PERDIDO si la clave no existe en el mapa
(get {:nombre "Alicia"} :apellido :PERDIDO)
;=> :PERDIDO

; agrega el par clave/valor al mapa (la función se llama así por "associate")
(assoc {:nombre "Alicia"} :apellido "Brown")
;=> {:nombre "Alicia", :apellido "Brown"}

; elimina el par clave/valor con clave :apellido (la función se llama así por "disassociate")
(dissoc {:nombre "Alicia" :apellido "Brown"} :apellido)
;=> {:nombre "Alicia"}

; mezcla dos mapas
(merge {:nombre "Alicia"} {:apellido "Brown"})
;=> {:nombre "Alicia", :apellido "Brown"}

; obtiene el número de pares calve/valor que hay en el mapa
(count {:nombre "Alicia" :apellido "Brown"})
;=> 2

; obtiene todas las claves que hay en el mapa
(keys {:nombre "Alicia" :apellido "Brown"})
;=> (:nombre :apellido)

; obtiene todos los valores que hay en el mapa
(vals {:nombre "Alicia" :apellido "Brown"})
;=> ("Alicia" "Brown")
```

## Definiendo Funciones

```clj
(defn nombre-de-la-funcion
  "descripción de la función, opcional"
  [parametro1 parametro2]
  (cuerpo-de-la-funcion))
```

* La nombres de las funciones que devuelven true o false--conocidas como  "predicados"--generalmente terminan con un signo de pregunta "?"
* map y reduce - Funciones que reciben otras funciones

## Map y Reduce

```clj
; aplica una función a cada elemento de una colección
(map inc [1 2 3 4])
;=> (2 3 4 5)
; Similar a [(inc 1) (inc 2) (inc 3) (inc 4)]
```
**`map`** recibe una función y una colección, luego aplica la función a cada elemento de la colección en el orden en que aparecen. Devuelve una nueva colección que contiene los resultados.

```clj
; "reduce" una colección a un valor usando una función
(reduce + [1 3 5 7])
;=> 16
; Similar a (+ 1 3) ;=> 4
;           (+ 4 5) ;=> 9
;           (+ 9 7) ;=> 16
```

**`reduce`** recibe una función y una colección. Primero, aplica la función al primer y al segundo elemento. Después aplica la función al *resultado* de la operación anterior y al tercer elemento. El proceso continua hasta que llega al último elemento de la colección y devuelve el resultado de esa última operación.


## Control de flujo

```clj
(if expresion-condicional
  expresion-que-se-evalua-cuando-es-verdadera
  expresion-que-se-evalua-cuando-es-falsa)
```

## Lógica Booleana con and, or y not

| x     | y     | (and x y) | (or x y) | (not x) | (not y) |
| ----- | ----- | --------- | -------- | ------- | ------- |
| false | false | false | false | true  | true  |
| true  | false | false | true  | false | true  |
| true  | true  | true  | true  | false | false |
| false | true  | false | true  | true  | false |

## let
Asgina nombres a valores dentro de una función.

```clj
(let [nombre (:nombre usuario)             ; asigna a `nombre`
      mensaje (str "Hola, " nombre "!")]   ; asigna a `mensaje`
  (println mensaje))                       ; hace algo con `mensaje`
```
