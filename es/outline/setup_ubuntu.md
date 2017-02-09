Configuración en Ubuntu
==========

* Iniciar una terminal
* Instalar Git
* Configurar Git
* Instalar Java
* Instalar Leiningen
* Install Nightcode
* Test your setup

## Iniciando una terminal

Para estas instrucciones, y para la mayor parte de la clase, vas a necesitar una terminal o línea de comandos. Esta es una interfaz basada en texto para "hablarle" a tu computadora. La podés abrir haciendo click en "Dash Home" y tipeando `Terminal`. También podés abrir una terminal en cuaquier momento apretando `Ctrl-Alt-T`. Si nunca usaste una terminal antes, puede que convenga invertir algo de tiempo leyendo [lo básico acerca de la línea de comandos](http://blog.teamtreehouse.com/command-line-basics).

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

Verificá que todo está bien tipieando lo siguiente en la terminal:

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

Leiningen es una herrmienta para administrar proyectos Clojure desde la terminal.

Andá al [sitio de Leiningen](http://leiningen.org/). Vas a ver un enlace al script `lein` en la sección "Install" ("Instalación"). Pinchá en ese enlace con el boton secundario del ratón y elegí "Guardar enlace como...". Guardalo en tu directorio Descargas.

![sitio de Leiningen](/outline/img/leiningen_site.png)
![sitio de Leiningen](/outline/img/lein_install.png)

Luego de eso, ejecutá el siguiente comando en tu terminal. Se te va a pedir tu contraseña.

```
sudo mkdir -p /usr/local/bin/
sudo mv ~/Descargas/lein* /usr/local/bin/lein
sudo chmod a+x /usr/local/bin/lein
export PATH=$PATH:/usr/local/bin
```

Luego de haber ejecutado los comandos de arriba, ejecutá el comando `lein version`. Va a tomar un rato, puesto que, como es la primera vez, va a bajar algunos recursos que necesita. Si lo completa correctamente, ¡genial!. Si no, pedile ayuda a una instructora o instuctor.

## Install Nightcode

Go to the [Nightcode releaes site](http://github.com/oakes/Nightcode/releases).
On the page there, you should see version numbers and links to download specific version of Nightcode, for example, Nightcode-2.1.0.jar.
Click the link ending in `.jar` and you will download a file, `Nightcode-x.y.z.jar`.

> Don't download platform specific binary releases.
> Use jar archive.
> Jar archive is much easier to get started.

Once the download finished, we want to start the editor.
To startup, go into your Downloads folder (or wherever you save files from your browser) and run the Nightcode-x.y.z.jar file using `java` command.


Open a terminal and run the following commands:

```bash
cd ~/Downloads/
java -jar Nightcode-2.1.0.jar
```

![Nightcode](img/nightcode-startup.png)


## Testing your setup

You have set up Java, Leiningen, Nightcode, and Git on your computer--all the tools you will need for this course. Before starting, we need to test them out.

#### Testing Leiningen

Open a new terminal and run the following command:

```bash
lein new myproject
```

This will create a new project, `myproject`, which has files to form a Clojure project.
Normally, Clojure code exists within such Clojure project.

Run following commands:

```bash
cd myproject
lein repl
```

This may take long to start up for the first time.
Leiningen downloads libraries it needs to run Clojure.
When Leiningen starts, you'll see `user=>` prompt on your terminal.

![Testing lein repl](img/ubuntu/testing-lein-repl.png)

Now, you are ready to use __REPL__, which we learn about soon.
It's a special terminal for Clojure.

At the REPL prompt, type `(+ 1 1)` and press Return. Did you get the answer `2` back? Great!

Your leiningen install looks good. For now, press the Control button and D button on your keyboard together (abbreviated as Ctrl+D). This should take you out of the Clojure REPL and back to your normal terminal prompt. Then, the terminal will show you the following message: `user=> Bye for now!`


#### Cloning out github repository

Open another terminal and run the following command:

```bash
git clone https://github.com/ClojureBridge/welcometoclojurebridge
```

This will clone `welcometoclojurebridge` repository which includes sample Clojure apps.
Your terminal should look similar to this picture:

![Testing git clone](img/ubuntu/testing-git-clone.png)

Once it finishes, type following commands on the same terminal.

```bash
cd welcometoclojurebridge
ls
```

You'll see the list of directories/files like this:

```
README.md       outline         project.clj     resources       src
```

#### Testing Nightcode

If Nightcode isn't started yet or closed, open it by typing the command on terminal:

```bash
java -jar Nightcode-2.1.0.jar
```

At the bottom right of the screen, type `(+ 1 1)` into the window. It should look like the following image:

![Testing Nightcode](img/nightcode-repl.png)

If you see the result, 2, that worked, great!


### Testing apps

Now we will open and run the sample Clojure apps in Nightcode.
On the top left corner, click "Import" then find the directory,
`welcometoclojurebridge`, which was created when you ran
`git clone` command. Click "Open."
In the project directory tree on the left, click on `src` - `welcometoclojurebridge` - `core.clj`. The `core.clj` file will be opened on the right side.
This is a Clojure program.

![Testing apps - click import](img/nightcode-click-import.png)
![Testing apps - open welcometoclojurebridge](img/nightcode-open-project.png)
![Testing apps - core.clj](img/nightcode-welcometoclojurebridge-core.png)


The next step is to run the code shown in the window.
Click "Run with REPL" on the bottom.
It may take a while.
Eventually, REPL will start and show a prompt, `user=>`.
Once, you see the prompt, click "Reload" button.


![Testing apps - start repl](img/nightcode-welcometoclojurebridge-run-with-repl.png)
![Testing apps - repl started](img/nightcode-repl-started.png)
![Testing apps - repl reload](img/nightcode-repl-reload.png)


You should see a fun welcome message.

![Testing apps - welcome](img/testing-welcomeclojurebridge.png)


Let's try one more sample.
In the directory tree on the left, click on
`welcometoclojurebridge` - `src` - `clojurebridge-turtle` -
`walk.clj`. The `walk.clj` file will open on the right side.
Like we did before, click "Reload" button.

![Testing apps - walk code](img/nightcode-turtle-walk.png)
![Testing apps - walk reload](img/nightcode-turtle-walk-reload.png)


An initial image of the turtles app should pop up.
A small triangle on the center is the *turtle*.


Type `(forward 40)` on the repl at the bottom of the window.
You should see the turtle moved upword:

![Testing apps - forward](img/nightcode-turtle-forward-40.png)



#### Success!

Congratulations! You have opened and run your first Clojure apps, and
your install and setup are all completed!

If you want to know what the turtle (*a small triangle*) can do,
see [Turtle App API](https://github.com/ClojureBridge/welcometoclojurebridge/blob/master/outline/TURTLE.md) and
[How to Walk Turtles](https://github.com/ClojureBridge/welcometoclojurebridge/blob/master/outline/TURTLE-SAMPLES.md) for more information.
