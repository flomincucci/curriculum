# Resumen de Quil

## Formas -- (¡Funcionan únicamente dentro de la función draw!)

```clj
(line x1 y1 x2 y2)
```

Dibuja una línea recta comprendida entre dos puntos. `x1`, `y1`, `x2`, e
`y2` son números y se usan para indicar las **coordenadas** de dichos puntos:
la cantidad de pixeles desde el borde superior (`y`) o el borde izquierdo de
la pantalla (`x`).

```clj
(rect x y anchura altura)
```

Dibuja un rectángulo en la pantalla. `x` e `y` son
coordenadas. `anchura` y `altura` también son números y definen el ancho
y el alto del rectángulo en pixeles.

```clj
(ellipse x y anchura altura)
```

Dibuja un óvalo en la pantalla.

## Color

```clj
(color r g b a)
```

Un color consiste en cuatro números que varían entre `0` y `255`. Los primeros tres valores representan los colores rojo, verde y azul que se "mezclan" para formar un nuevo color. El cuarto número define la opacidad. Por ejemplo, `(color 0 0 255 128)` es un color azul con una transparencia del 50% (mitad opaco, mitad transparente).

```clj
(background color)
```

Establece el color del lienzo (o *canvas* en inglés). Es genial para "borrar" la pantalla cada vez que dibujamos (en la función `draw`).

```clj
(fill color)
```

Establece el color con el que se van a pintar las formas que se dibujen después de llamar a esta función.

```clj
(stroke color)
```

Establece el borde que van a tener las formas que se dibujen después de llamar a esta función.

```clj
(no-fill)
(no-stroke)
```

Indica que las figuras que se dibujen luego no van a pintarse, ni van a tener borde, respectivamente. Por ejemplo:

```clj
(background (color 255 0 0))
(fill (color 0 0 255))
(ellipse 100 100 30 30)
```

## Texto

```clj
(text tu-texto x y)
```

Escribe un fragmento de texto en las coordenadas indicadas.

## Mouse

Las siguientes funciones te permiten obtener datos sobre tu mouse. Son indispensables si querés mover cosas por la pantalla.

```clj
(mouse-x) ;=> número
(mouse-y) ;=> número
(mouse-pressed?) ;=> true/false
```

¿Podés adivinar que hace este código?

```clj
(ellipse (mouse-x) (mouse-y) 30 30)
```

## Tiempo

```clj
(frame-count) ;=> número
```

El número de marcos (o *frames* en inglés) que se mostraron desde que el arrancó el programa. Es común utilizar esta función en conjunto con función módulo `(mod número divisor)`. Por ejemplo:

```clj
(ellipse 100 100 (mod (frame-count) 30) (mod (frame-count) 30))
```

## Más funciones de Quil

Las funciones que mencionamos acá son las fundamentales para arrancar, pero ¡Quil tiene un montón de funciones más! Podés conocerlas e investigarlas en la [documentación de la API de Quil](http://quil.info/api).
