macOS  Setup
==========

* Abrir una terminal
* Instalar Git
* Configurar Git
* Asegurarse que Java esté instalado
* Instalar Leiningen
* Instalar Nightcode
* Verifica tu setup

## Abrir una Terminal

Para estas instrucciones, y para casi toda la clase, necesitaras tener una terminal, o linea de commando, disponible.
Esta es una interfaz para hablar con tu computadora basada en texto, y puedes abrirla ejecutando Terminal.app, la cual se encuentra en el directorio `/Applications/Utilities`.
Si nunca utilizaste la terminal anteriormente, tal vez quieras [leer lo basico sobre la linea de comandos](http://blog.teamtreehouse.com/command-line-basics).

Ahora ve y abre la terminal. Debería verse algo similiar a esto:

![blank terminal](img/os_x/blank_terminal.png)

El prompt (dónde tipearas tus comandos) puede que luzca diferente: usualmente muestra el nombre de tu computadora y el nombre de usuario, ademas de la carpeta o directorio donde te encuentres actualmente.

Para el resto de este setup, te diré que comandos ejecutar en tu terminal. Cuando diga eso, me refiero a "tipea el comando en la terminal y luego presiona la tecla Enter".

#Instala Git

Para verificar si ya tienes git instalado tipea  `git --version`. Si posees la version `git version 1.9.3 (Apple Git-50)` o una version superior estaras bien.

Si no, visita [git-scm](http://git-scm.com). Haz click en "Downloads para Mac".
El instalador de git debería bajar automaticamente. Si no lo hace, haz click en el link para realizar una descarga manual.
Una vez que la descarga halla finalizado, abre __~/Downloads/__ en Finder y haz doble click en el archivo descargado (con el nombre similar a __git-2.0.1-intel-universal-snow-leopard.dmg__)
Esto montará la imagen y luego abre una ventana de Finder. Haz doble-click en el paquete instalador (con el nombre similar a __git-2.0.1-intel-universal-snow-leopard.pkg__)
Tal vez aparezca un mensaje diciendo que el instalador no puede ser abierto porque el origen es de un desarrollador no identificado.
Si esto ocurre, haz click en "OK", luego click derecho (o control-click) sobre el archivo y selecciona "Open" del menú contextual.
Tal vez un nuevamente aparezca un mensaje diciendo que el origen del instalador es de un desarrollador no indentificado, pero esta vez tendrás la opción de hacer click en "Open". Hazlo.
Esto iniciará el instalador. Sigue sus indicaciones, y ingresa tu contraseña cuando te lo indiqué.
Una vez que halla finalizado este proceso, es seguro desmontar la imagen del disco (haciendo click en el botón de ejectar en Finder") y luego borra el archivo de la carpeta Downloads.

## Configura Git

Si ya haz utilizado Git anteriormente entonces deberias poseer user.name y user.email configurado.
Si no haz utilizado anteriormente, tipea lo siguiente en la terminal:

```bash
git config --global user.name "tu nombre actual"
git config --global user.email "tu e-mail actual"
```
CONSEJO: Utiliza la misma dirección de e-mail para git, github y ssh.

Verifica la configuración tipeando lo siguiente en la terminal:

`git config --get user.name`
Resultado esperado:
`tu nombre`

`git config --get user.email`
Resultado esperado:
`tu e-mail``

## Asegurate que Java esté instalado

> Si posees la version 10.11 de OS X (El Capitan), no tienes Java instalado. Tienes que instalar Java.
> Descarga Java de <http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html> y sigue las instrucciones. Cuando la instalación finalice, setea la variable de entorno `JAVA_HOME` a traves de la terminal
> `export JAVA_HOME=/usr/libexec/java_home -v 1.8`
> 
> Si tienes problema el articulo <http://osxdaily.com/2015/10/17/how-to-install-java-in-os-x-el-capitan/>, puede ayudarte.

Ejecuta `java -version` en tu terminal.  Si no tienes Java instalado, OS X te preguntará si deseas instalarlo (esto si tu version de OS X es 10.10 o más vieja). Sigue todas las instrucciones OS X te dará, luego retoma hasta esta parte del tutorial y ejecuta `java -version` nuevamente.

Si Java está instalado, verás algo como esto en tu terminal:
![Java version](img/os_x/java_version.png)

Los detalles de la version de Java puede que sean diferentes de lo mostrado; está bien.

## Instalar Leiningen

Leiningen es una herramienta usada desde la linea de comando para manejar proyectos de Clojure.
Para instalar `lein` ejecuta los siguientes comandos en tu terminal; se te pedirá que ingreses tu contraseña para al menos el primer comando que comienza con `sudo` (El caracter `%` es un simbolo típico del prompt de la linea de comandos, no hace falta tipearlo):

```bash
% curl https://raw.githubusercontent.com/technomancy/leiningen/stable/bin/lein > lein
% sudo mkdir -p /usr/local/bin/
% sudo mv lein /usr/local/bin/lein
% sudo chmod a+x /usr/local/bin/lein
```
Verifica que ahora puedas ver el comando:

```bash
% which lein
/usr/local/bin/lein
```
Si no lo puedes ver `/usr/local/bin/lein` como parece arriba, haz lo siguiente:
```bash
% export PATH=$PATH:/usr/local/bin
```
Ahora ejecuta `which lein` y ahora deberias ver el comando `lein`.

Luego que hayas configurado como descripto anteriormente, ejecuta el comando `lein version`. Esto puede tomar unos momentos ya que descargará algunos recursos requirados la primera vez. Si este paso completa satisfactoriamente, todo está correcto! Si no, solicita ayuda de un instructor.


## Instalar Nightcode

Ve al [sitio de releases de Nightcode](http://github.com/oakes/Nightcode/releases).
En el sitio, podrás ver números de version de Nightcode y link para descargar versiones especificas de Nightcode, por ejemplo Nightcode-2.1.jar.
Click en el link que termina con `.jar` y descargaras un archivo, `Nightcode-x.y.z.jar`.

> No descargues releases especificos para diferentes plataformas
> Usa el archivo jar
> El archivo jar es sencillo para comenzar.

Una vez que la descarga del archivo finalice, queremos iniciar el editor.
Para inicial el editor, ve a la carpeta Downloads (o donde sea el browser guarda los archivos) y ejecuta el archivo Nightcode-x.y.z.jar utiizando el 
comando `java`

Abre una terminal y ejecuta los siguientes comandos:

```bash
cd ~/Downloads/
java -jar Nightcode-2.1.0.jar
```

![Nightcode](img/nightcode-startup.png)

## Testea tu instalación

Haz instalado y configurado Java, Leiningen, Nightcode y Git en tu computadora -- todas las herramientas que necesitaras para este workshop. Antes de comenzar, cercirnarnos de que esten bien configuradas.


#### Testeando Leiningen

Abre una nueva terminal y corre el siguiente comando:
```bash
lein new myproject
```

Esto creará un nuevo proyecto, `myproject`, el cual contiene archivo para formar un proyecto Clojure.
Normalmente, código Clojure existe dentro de estos proyectos Clojure.

Corre los siguientes comandos:

```bash
cd myproject
lein repl
```

El inicio de esto puede llegar a tardar un buen rato la primera vez.
Leiningen descarga las librerias necesarias para poder correr Clojure.
Cuando Leinigen inicia, deberias ver el prompt `user =>` en tu terminal. 

![Testing lein repl](img/os_x/testing-lein-repl.png)

Ahora estas lista para usar el __REPL__, el cual vas a aprender de el pronto.
Es una terminal especial para Clojure.

En el REPL prompt, tipea `(+ 1 1)` y luego presiona Enter. Obtuviste la respuesta `2`? Genial!

Tu instalación de Leinigen se ve bien. Ahora, presiona las teclas Control y la tecla D en tu teclado a la vez (abreviado Ctrl+D). Esto debería sacarte fuera el REPL de Clojure y llevarte a tu prompt en la terminal. Luego, la terminal debería mostrarte el siguiente mensaje: `user=> By for now!`

#### Clonando tu repositorio Github

Abre otra terminal y corre el siguiente comando:

```bash
git clone https://github.com/ClojureBridge/welcometoclojurebridge
```

Esto clonará el repositorio `welcometoclojurebridge` el cual incluye aplicaciones Clojure de ejemplo.
Tu terminal debería verse similar a lo siguiente:

![Testing git clone](img/os_x/testing-git-clone.png)

Una vez que finalice, tipea los siguientes comandos en la misma terminal:

```bash
cd welcometoclojurebridge
ls
```
Deberás ver la lista de directorios/archivos como esto:

```
README.md       outline         project.clj     resources       src
```


#### Testeando Nightcode

Si Nightcode no sido inicido o fue cerrado, abrelo tipeando lo siguiente en la terminal:

```bash
java -jar Nightcode-2.1.0.jar
```
Al la derecha del final de la pantalla, typea `(+ 1 1)` en la ventana. Debería verse similar a la siguiente imagen:

![Testing Nightcode](img/nightcode-repl.png)

Si puede ver el resultado, 2, eseto funcionó, genial! 

#### Testeando apps - Bienvenido a clojurebridge


Ahora abriremos y correremos las aplicaciones de ejemplo en Nightcode.
Arriba en la esquina izquierda, click "Import", luego busca el directorio,
`welcometoclojurebridge`, el cual fue creado cuando el comando `git clone` fue ejecutado. Click en "Open".
A la izquierda, en el arbol de directorio del proyecto, click en `src` - `welcometoclojurebridge` - `core.clj`. El archivo `core.clj` se abrirá del lado derecho.
Eso es un programa Clojure.

![Testeando apps - click import](img/nightcode-click-import.png)
![Testeando apps - abre welcometoclojurebridge](img/nightcode-open-project.png)
![Testeando apps - core.clj](img/nightcode-welcometoclojurebridge-core.png)

El paso siguiente es correr el código mostrado en la ventana.
Click "Run with REPL" al final.
Esto podría tomar un largo tiempo, y descargará otras partes de codigo que la aplicación requiere.
Tal vez puedas ver lineas que comienzan con `Retrieving...` en tu pantalla.
Eventualmente, el REPL comenzará y mostrará el prompt, `user=>`.
Una vez que puedas ver el prompt, haz click en el boton "Reload".

![Testeando apps - inicia REPL](img/nightcode-welcometoclojurebridge-run-with-repl.png)
![Testeando apps - REPL iniciado](img/nightcode-repl-started.png)
![Testeando apps - REPL recargado](img/nightcode-repl-reload.png)

Deberías podes ver un divertido mensaje de bienvenida.

![Testeando apps - Bienvenida](img/testing-welcomeclojurebridge.png)

#### Testeando apps - La tortuga camina.


Probemos un ejemplo más.
En el arbol de directorio a tu izquierda, click en
`welcometoclojurebridge` - `src` - `clojurebridge-turtle` -
`walk.clj`. El archivo `walk.clj` se abrirá del lado derecho.
Tal como inicimos anteriormente, click en el boton "Reoload"

![Testeando apps - walk code](img/nightcode-turtle-walk.png)
![Testeando apps - walk reload](img/nightcode-turtle-walk-reload.png)

Una imagen de las aplicación turtles debería mostrarse.
Un pequeño triangulo en el centro es la *tortuga* 

An initial image of the turtles app should pop up.
A small triangle on the center is the *turtle*.

Tipea `(forward 40)` en el REPL al fondo de la pantalla.
Deberías ver la tortuga moverse hacia adelante:

![Testeando apps - forward](img/nightcode-turtle-forward-40.png)


#### Exito!

Felicitaciones! Haz abierto y ejecutado tu primer aplicación Clojure, y tu instalación y setup han sido completado!

Si quieres saber que puede hacer la tortuga (*a small triangle*),
por favor mira [Turtle App API](https://github.com/ClojureBridge/welcometoclojurebridge/blob/master/outline/TURTLE.md) y
[How to Walk Turtles](https://github.com/ClojureBridge/welcometoclojurebridge/blob/master/outline/TURTLE-SAMPLES.md) para más información.
