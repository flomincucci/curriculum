Configuración en Ubuntu
==========

* Iniciar una terminal
* Instalar Git
* Configurar Git
* Instalar Java
* Instalar Leiningen
* Instalar Nightcode
* Testear tu configuración

## Iniciando una terminal

Para estas instrucciones, y para la mayor parte de la clase, vas a necesitar una terminal o línea de comandos. Esta es una interfaz basada en texto para "hablarle" a tu computadora. La podés abrir haciendo click en "Dash Home" y tipeando `Terminal`. También podés abrir una terminal en cualquier momento apretando `Ctrl-Alt-T`. Si nunca usaste una terminal antes, puede que convenga invertir algo de tiempo leyendo [lo básico acerca de la línea de comandos](http://blog.teamtreehouse.com/command-line-basics).

Ahora, andá y abrí tu primera terminal. Debería ser algo así como:

![terminal en blanco](/outline/img/ubuntu/blank_terminal.png)

El símbolo de sistema (donde vas a tipear tus comandos) puede verse distinto en tu computadora: suele mostrar el nombre de la computadora y el nombre de usuario, junto con el directorio o carpeta en la cual estás.

Para completar la configuración, te voy a ir pidiendo que ejecutes comandos en tu terminal. Lo que quiere decir: "tipeá el comando `<X>` en la terminal y apretá la tecla `Enter`".

## Instalando Git

Mirá si ya tenés Git instalado con `git version`.
Si el comando `git` no es encontrado, instalalo con este comando en la terminal:

```bash
sudo apt-get install git
```

## Configurando Git

Si ya has usado Git antes, ya deberías tener configurados los valores `user.name` y `user.email`.
Si no, tipeá en la terminal:

```bash
git config --global user.name "Tu nombre"
git config --global user.email "Tu email"
```

CONSEJO: Usá la misma dirección de mail para `git`, GitHub y `ssh`.

Verificá que todo está bien tipeando lo siguiente en la terminal:

`git config --get user.name`
Deberías obtener:
`Tu nombre`

`git config --get user.email`
Deberías obtener:
`Tu email`


## Instalar Java

Ubuntu viene con OpenJDK instalado.
Sin embargo, las versiones más nuevas de Nightcode tienen un problema para correr sobre OpenJDK.
Oracle JDK 8 es el mejor Java para usar nuestro material.

```bash
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java8-installer
(seguí las instrucciones)
```

A esta altura, ya tenés instalado Oracle JDK 8 en tu sistema Ubuntu.
Hay un paso más para usar el Oracle JDK 8 que acabás de instalar.

```bash
sudo update-alternatives --config java
(elegí /usr/lib/jvm/java-8-oracle/jre/bin/java)
```

Ejecutá en tu terminal `java -version`. Deberías ver algo así como:

![versión de Java](/outline/img/ubuntu/ubuntu-java-version.png)

La versión menor puede diferir de la de arriba; sin embargo, tiene que ser `1.8.0`.
Además, deberías ver `Java(TM) SE Runtime Environment`.


Otra opción es bajar el Java Development Kit (JDK) de Oracle desde
 [las descargas de Java SE](http://www.oracle.com/technetwork/java/javase/downloads/index.html).
En este caso, necesitás definir las variables de entorno `JAVA_HOME` y `PATH` luego de extraer el archivo.


## Instalando Leiningen

Leiningen es una herramienta para administrar proyectos Clojure desde la terminal.

Andá al [sitio de Leiningen](http://leiningen.org/). Vas a ver un enlace al script `lein` en la sección "Install" ("Instalación"). Pinchá en ese enlace con el botón secundario del ratón y elegí "Guardar enlace como...". Guardalo en tu directorio Descargas.

![sitio de Leiningen](/outline/img/leiningen_site.png)
![sitio de Leiningen](/outline/img/lein_install.png)

Luego de eso, ejecutá el siguiente comando en tu terminal. Se te va a pedir tu contraseña.

```
sudo mkdir -p /usr/local/bin/
sudo mv ~/Descargas/lein* /usr/local/bin/lein
sudo chmod a+x /usr/local/bin/lein
export PATH=$PATH:/usr/local/bin
```

Luego de haber ejecutado los comandos de arriba, ejecutá el comando `lein version`. Va a tomar un rato, puesto que, como es la primera vez, va a bajar algunos recursos que necesita. Si lo completa correctamente, ¡genial!. Si no, pedile ayuda a una instructora o instructor.

## Instalando Nightcode

Andá al [sitio de descargas de Nightcode](http://github.com/oakes/Nightcode/releases).
En esa página, deberías ver números de versión y enlaces para bajar versiones específicas de Nightcode (por ejemplo, `Nightcode-2.3.2.jar`).
Pinchá en el enlace que termina en `.jar`; vas a bajar un archivo, `Nightcode-x.y.z.jar`.

> Evitá bajar los binarios específicos para una plataforma.
> Usá el archivo `.jar`.
> Es mucho más fácil al comienzo.

Una vez que la descarga haya terminado, iniciá el editor.
Para eso, andá a tu carpeta `Descargas` (o donde sea que hayas grabado el archivo `Nightcode-x.y.z.jar` con tu navegador y ejecutalo con el comando `java`.


Abrí una terminal y ejecutá los siguientes comandos:

```bash
cd ~/Descargas/
java -jar Nightcode-2.3.2.jar
```

![Nightcode](/outline/img/nightcode-startup.png)


## Testeando tu configuración

Ya configuraste en tu computadora Java, Leiningen, Nightcode y Git --todas las herramientas que vas a necesitar para este curso. Antes de continuar, hay que testearlas.

#### Testeando Leiningen

Abrí una terminal y ejecutá el siguiente comando:

```bash
lein new miproyecto
```

Esto va a crear un nuevo proyecta, `miproyecto`, que tiene archivos para armar un proyecto Clojure. Normalmente, hay código Clojure dentro de tal tipo de proyecto.

Ejecutá los siguientes comandos:


```bash
cd miproyecto
lein repl
```

Puede que esto tome un rato para arrancar la primera vez. Leiningen baja bibliotecas que necesita para correr Clojure. Cuando Leiningen arranque, vas a ver el símbolo `user=>` en tu terminal.

![Testeando lein repl](/outline/img/ubuntu/testing-lein-repl.png)

Ahora, estás lista/o para usar el __REPL__, que vamos a aprender en un ratito.
Es una terminal especial para Clojure.

En el símbolo del REPL, tipeá `(+ 1 1)` y apretá 'Enter'. ¿Obtuviste como respuesta `2`? ¡Genial!

Tu instalación de Leiningen parece bien. Por ahora, apretá las teclas `Control` y `D` al mismo tiempo (abreviadas `Ctrl-D`). Esto te debería sacar del REPL de Clojure y de vuelta a tu símbolo de terminal normal. Luego, la terminal te va a mostrar: `user=> Bye for now!` ("¡Chau (por ahora)!")


#### Clonando el repositorio GitHub

Abrí otra terminal y ejecutá el siguiente comando:

```bash
git clone https://github.com/ClojureBridge/welcometoclojurebridge
```

Esto va a clonar el repositorio `welcometoclojurebridge` que incluye aplicaciones Clojure de muestra.
Tu terminal debería verse parecido a esta imagen:

![Testeando git clone](/outline/img/ubuntu/testing-git-clone.png)

Una vez que termine, tipeá los siguientes comandos en la misma terminal.

```bash
cd welcometoclojurebridge
ls
```

Vas a ver la lista de directorios/archivos, de esta manera:

```
README.md       outline         project.clj     resources       src
```

#### Testeando Nightcode

Si todavía no arrancaste Nightcode (o ya lo cerraste), abrilo tipeando el siguiente comando en la terminal:

```bash
java -jar Nightcode-2.3.2.jar
```

En la ventana de la parte inferior de la pantalla, tipeá `(+ 1 1)`. Debería verse como en la siguiente imagen:

![Testeando Nightcode](/outline/img/nightcode-repl.png)

Si muestra como resultado `2`, ¡genial!


### Testeando aplicaciones

Ahora, vamos a abrir y ejecutar las aplicaciones Clojure de muestra en Nightcode.
En la esquina superior izquierda, pinchá en `[Import]` ("Importar"). Luego, encontrá el directorio `welcometoclojurebridge` creado cuando ejecutaste el comando `git clone`. Pinchá `[Open]` ("Abrir").
En el árbol de directorios del proyecto de la izquierda, pinchá en `src` - `welcometoclojurebridge` - `core.clj`. El archivo `core.clj` se va a abrir en el lado derecho.
Esto es un programa en Clojure.

![Testeando aplicaciones - pinchar en "Import" ("Importar")](/outline/img/nightcode-click-import.png)
![Testeando aplicaciones - abrir welcometoclojurebridge](/outline/img/nightcode-open-project.png)
![Testeando aplicaciones - core.clj](/outline/img/nightcode-welcometoclojurebridge-core.png)


El siguiente paso es ejecutar el código que se muestra en la ventana.
Pinchá abajo en `[Run with REPL]` ("Ejecutar con el REPL").
Puede que tome un tiempo.
Eventualmente, el REPL va a arrancar y te va a mostrar un símbolo, `user=>`.
Una vez que veas ese símbolo, pinchá en el botón `[Reload]` ("Recargar").


![Testeando aplicaciones - arrancar REPL](/outline/img/nightcode-welcometoclojurebridge-run-with-repl.png)
![Testeando aplicaciones - REPL iniciado](/outline/img/nightcode-repl-started.png)
![Testeando aplicaciones - recargar REPL](/outline/img/nightcode-repl-reload.png)


Deberías ver un mensaje de bienvenida gracioso.

![Testeando aplicaciones - bienvenida](/outline/img/testing-welcomeclojurebridge.png)


Probemos una muestra más.
En el árbol de directorios de la izquierda, pinchá en `welcometoclojurebridge` - `src` - `clojurebridge-turtle` - `walk.clj`.
El archivo `walk.clj` se va a abrir en el lado derecho.
Como hicimos antes, pinchá el botón `[Reload]` ("Recargar").

![Testeando aplicaciones - código walk](/outline/img/nightcode-turtle-walk.png)
![Testeando aplicaciones - recargar walk](/outline/img/nightcode-turtle-walk-reload.png)


Debería aparecer una imagen inicial de la aplicación `clojurebridge-turtle`.
La *tortuga* es el triángulo chiquito en el centro.


Tipeá `(forward 40)` en the REPL en la parte inferior de la ventana.
Deberías ver que la tortuga se movió hacia arriba.

![Testeando aplicaciones - forward](/outline/img/nightcode-turtle-forward-40.png)



#### ¡Éxito!

¡Felicitaciones! Has abierto y ejecutado tu primera aplicación en Clojure.
¡La instalación y configuración está lista!

Si querés saber qué puede hacer la tortuga (*el triángulo chiquito*), mirá
[La API de la aplicación Turtle](https://github.com/ClojureBridge/welcometoclojurebridge/blob/master/outline/TURTLE.md) y
[How to Walk Turtles (Cómo hacer caminar tortugas)](https://github.com/ClojureBridge/welcometoclojurebridge/blob/master/outline/TURTLE-SAMPLES.md).
