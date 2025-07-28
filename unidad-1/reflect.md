# Unidad 1

## 🤔 Fase: Reflect

### Actividad 07

### Parte 1: recuperación de conocimiento (Retrieval Practice)
1. Basándote en los ejemplos que vimos de sistemas físicos interactivos al iniciar el curso, describe las tres características que definen a un sistema físico interactivo.

Como tal un sistema fisico interactivo consiste de un programa con instrucciones con diferentes parametros dadas por el usuario con el obeetivo de luego ser ejecutadas y tener unna interacción en tiempo real con ellas dependiendo de lo que se quiera hacer con el programa, se pueden programas diferentes interacciones con botones, ondas de sonido, arte/diseño, etc..

2. Explica el modelo input-process-output de Patrick Hübner usando como ejemplo el sistema que construiste con micro:bit y p5.js en la Actividad 06. ¿Cuál fue el input, cuál fue el proceso y cuál fue el output?
   
En este caso los inputs serian el microbit, sus botones A y B, el proceso es el programa como tal donde se encuentran isntrucciones y para terinar el output son las interaciones que hay a la hora de probar el prograa ya que el microbit recibe la información del programa y al presionar los botones A y B ambos tienen reacciones diferentes dentro del programa.

3. ¿Cuál es la función de la línea uart.write('A') en el código del micro:bit y qué función en p5.js se encarga de “escuchar” ese mensaje?

Si no estoy mal, esa linea cumple la función de detactar la tecla A cuando el usuario interactua con ella y luego en p5.js esta la "escucha" de forma que el boton A es valido enn el programa y al interactuar con el fisicamente se tiene una reacción dentro del programa. 

4. ¿Cuál es la diferencia fundamental entre el arte/diseño tradicional y el arte/diseño generativo? 

La diferencia fundamental que hay entre estos 2 tipos de arte/diseño es que el arte/diseño generativo requiere de un programa autonomo al cual se le dan instrucciones para hacer el diseño deseado, pero el programa tiene cierta participación en la toma de decisiones dentro del procedimiento, lo que dentro del arte/diseño tradicional no se necesita ya que todo esta hecho por un ser humano. 

### Parte 2: reflexión sobre tu proceso (Metacognición) 

1. ¿Qué fue más desafiante para ti en esta unidad: la parte conceptual (entender qué es un sistema físico interactivo) o la parte técnica (hacer que el micro:bit y p5.js se comunicaran)? ¿Por qué?

Para mi en lo general siempre me ha sido mas complicada la parte técnica a la horaa de programar, ya que no suelo tener muy claros ciertos concceptos aunque los estudie una y otra vez (solia ver la programación como algo imposible o muy dificil de comprender y me bloqueaba), durante estas clases no se si es el tipo de programación o los conceptos pero me he visto más interesada en estos y me dan muchas ganas de comprender como funciona cada codigo hecho ya que lo puedo utilizar a futuro.

2. Describe el momento “¡Aha!” que tuviste cuando lograste que una acción en el micro:bit (presionar un botón, sacudirlo) tuviera un efecto visible en el canvas de p5.js por primera vez. ¿Qué fue lo que entendiste en ese instante?

Fue durante la primera vez que usamos microbit y p5.js, ya que nunca habia visto algo similar y al inicio de la clase no sabia como funcionaba, pero estaba muy interesada en probarlo por mi misma para lograr comprenderlo, en especifico mi momento "¡Aha!" fue al momento de presionar los botones que hay en el microbit y ver como en el canvas de cambiaba de color el circulo que se mostraba ahi, en ese momento comprendi como funcionaban y que no era tan complicado como alguna vez lo pense.

3. Al inicio de la unidad te pregunté: “¿Este curso para qué me sirve?”. Después de experimentar y construir tu primer prototipo, ¿Cómo ha cambiado o se ha vuelto más concreta tu respuesta a esa pregunta?

Mi idea inicial no es tan diferente de mi idea actual, en general quiero hacer sistemas interactivos enfocados en visuales, videos musicales e identidad de marca, ya que es lo que me interesa hacer una vez salga de la carrera, creo que al combinar lo que se y o que estoy aprendiendo voy a tener un abanico de posibilidades a mi alcanze, podre hacer lo que quiero pero con un plus que puede que se convierta en mi fuerte y me diferencie de los demas proyectos que usan las mismas bases, pero no tienen del agregado que esta materia ofrece.

4. El tutorial de la Actividad 05 te llevó paso a paso. ¿Cómo te sentiste con ese método de aprendizaje? ¿Te dio seguridad o preferirías haberlo intentado por tu cuenta desde el principio?

En lo personal me gusto mucho este modelo de aprendizaje, ya que nos mostraba paso a paso de la creación del programa, como se haccia y para que servia cada parque que lo compone, lo que me parecio bastante interesante ya que es mas facil comprender como funciona un programa desde cero para ya luego haacerlo tu mismo, porque en mi opinion si se hace el programa sin conocimiento ninguno la persona puede no tener el mismo nivel de aprendizaje que al ver primero como se hace el programa y luego llevarlo a la practica. 

### Actividad 08 

Mi codigo 
``` js
let x = 200;
let port;
  let connectBtn;
  let connectionInitialized = false;

  function setup() {
    createCanvas(400, 400);
    background(220);
    port = createSerial();
    connectBtn = createButton("Connect to micro:bit");
    connectBtn.position(80, 300);
    connectBtn.mousePressed(connectBtnClick);
  }

  function draw() {
    background(220);

    if (port.opened() && !connectionInitialized) {
      port.clear();
      connectionInitialized = true;
    }

    if (port.availableBytes() > 0) {
      let dataRx = port.read(1);
      if (dataRx == "A") {
      x-=5;
      } else if (dataRx == "B") {
      x+=5;
      }
    }

    
    circle(x,height/2,60);

    if (!port.opened()) {
      connectBtn.html("Connect to micro:bit");
    } else {
      connectBtn.html("Disconnect");
    }
  }

  function connectBtnClick() {
    if (!port.opened()) {
      port.open("MicroPython", 115200);
      connectionInitialized = false;
    } else {
      port.close();
    }
  }

```

``` py
from microbit import *

uart.init(baudrate=115200)
display.show(Image.SNAKE)

while True:
    if button_a.is_pressed():
        uart.write('A')
    if button_b.is_pressed():
        uart.write('B')
    
        
    sleep(100)

```
Codigo de Valentina Martinez 

``` py
from microbit import *

uart.init(baudrate=115200)
display.show(Image.DUCK)

while True:

    if button_a.was_pressed():
        uart.write('A')
    if button_b.was_pressed():
        uart.write('B')    
    else:
        uart.write('N')

    sleep(100)
```
``` js
  let port;
  let x =200;
  let connectBtn;
  let connectionInitialized = false;

  function setup() {
    createCanvas(400, 400);
    background(220);
    port = createSerial();
    connectBtn = createButton("Connect to micro:bit");
    connectBtn.position(80, 300);
    connectBtn.mousePressed(connectBtnClick);
  }

  function draw() {
    background(220);

    if (port.opened() && !connectionInitialized) {
      port.clear();
      connectionInitialized = true;
    }

    if (port.availableBytes() > 0) {
      let dataRx = port.read(1);
      if (dataRx == "A") {
       x-=100;
      } 
      if (dataRx == "B") {
       x+=100;
      }
      else if (dataRx == "N") {
      }
    }

    circle(x,150,100);

    if (!port.opened()) {
      connectBtn.html("Connect to micro:bit");
    } else {
      connectBtn.html("Disconnect");
    }
  }

  function connectBtnClick() {
    if (!port.opened()) {
      port.open("MicroPython", 115200);
      connectionInitialized = false;
    } else {
      port.close();
    }
  }
``` 
La mas grande diferencia que veo entre el codigo de mi compañera y el mio es que el circulo solo se mueve si el boton A y B han sido presionados, a diferencia de mi codigo que solo funcion cuando los botones A y B estan siendo presionados en el momento respectivamente, en ambos casos el boton A funciona para mover el circulo hacia la izquierda y el boton B para mover el circulo a la derecha, sumandole y restandole valores dependiendo de la dirección a la que se quiere mover el circulo, en mi codigo solo se suman o se restan 5 pixeles hacia la derecha y la izquierda mientras que en el codigo de mi compañera se mueve el circulo 100 pixeles dependiendo de la dirección deseada por lo que creo que en su caso esto se debe al tamaño del circulo que es mucho mayor en tamaño que el mio. Lo demas del codigo veo que no tiene cambios significativos ya que ambas usamos de base el codigo que se nos dio para la actividad 05.
