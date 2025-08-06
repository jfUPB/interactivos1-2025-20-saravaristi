# Unidad 2

## 🔎 Fase: Set + Seek

### Actividad 01 

1. Describe detalladamente cómo funciona este ejemplo.

El codigo funciona de forma que se tienen 2 pixeles que parpadean cada uno con un tienmpo respectivo y diferente el uno del otro, se tienen dos estados los cuales son "Init" y "WaitTimeOut" donde Init funciona de forma que guarda el tiempo de inicio y confiigura los valores de los pixeles, mientras que WaitTimeOut se eencarga de verificar que el tiempo estipulado para cada pixel pase para hacer que cada pixel brille, cuando esto se cumple todo el proceso se repite. En este caso el evento es "Interval" y hay varias acciones dentro del programa que ayudan a que cada estado sea completado

2. ¿Cuáles son los estados en el programa?

En este caso los estados son una condición de espera, por lo que el codigo hay 2 estados los cuales son "Init" y "WaitTimeOut" 

3. ¿Cuáles son los eventos/inputs en el programa?

Los eventos es cuando el programa esta esperando que se cumplan un conjuntos de acciones como si fuese una lista de cosas que hacer

4. ¿Cuáles son las acciones en el programa?

Hay algunas como actualizar variables, leer tiempo, alternaltar el estado de los pixeles entre prendido y apagado, calcular cuanto tiempo ha pasado desde la ultima actualización de cada pixel, calcular el tiempo restante para cada pixel 

### Actividad 02 
``` py
from microbit import *
import utime

class Pixel:
    def __init__(self, x, y):
        self.x = x
        self.y = y

    def turn_on(self):
        display.set_pixel(self.x, self.y, 9)

    def turn_off(self):
        display.set_pixel(self.x, self.y, 0)


RED = Pixel(2, 0)
YELLOW = Pixel(2, 1)
GREEN = Pixel(2, 2)

STATE_RED = 0
STATE_GREEN = 1
STATE_YELLOW = 2

DURATION_RED = 3000
DURATION_GREEN = 3000
DURATION_YELLOW = 3000

current_state = STATE_RED
start_time = utime.ticks_ms()

while True:
    RED.turn_off()
    YELLOW.turn_off()
    GREEN.turn_off()

    now = utime.ticks_ms()
    elapsed = utime.ticks_diff(now, start_time)

    if current_state == STATE_RED:
        RED.turn_on()
        if elapsed > DURATION_RED:
            current_state = STATE_GREEN
            start_time = now

    elif current_state == STATE_GREEN:
        GREEN.turn_on()
        if elapsed > DURATION_GREEN:
            current_state = STATE_YELLOW
            start_time = now

    elif current_state == STATE_YELLOW:
        YELLOW.turn_on()
        if elapsed > DURATION_YELLOW:
            current_state = STATE_RED
            start_time = now

    sleep(100)
```
En este codigo se tiene como evento el cambiar del color y existen los estados STATE_RED, STATE_YELLOW y STATE_GREEN donde cada uno de estos tiene acciones como obttener el tiempo actual y su estado actual para ya luego si el tiempo concurrido es menor a la duración predeterminada de cada color se cambia al siguiente estado 

### Actividad 03 

1. Explica por qué decimos que este programa permite realizar de manera concurrente varias tareas.

El programa si permmite realizar varias tareas a la vez ya que se tiene 3 caritas que se van cambiado segun el tiempo que tenga cada una, ademas de poder cambiar las caras manualmente usando el boton A.

2. Identifica los estados, eventos y acciones en el programa.

En este programa se tiene como evento "mostrar expresiones" existen varios estados, entre ellos estan STATE_INIT, STATE_HAPPY, STATE_SMILE, STATE_SAD, en cuanto a acciones son todas estasn que se encuentran dentro de cada uno de los estados para que cada uno de estos se cumpla correctamente, algunas de las acciones presentes en el codigo son: display.show(Image.HAPPY), start_time = utime.ticks_ms(), interval = HAPPY_INTERVAL y current_state = STATE_HAPPY

3. Describe y aplica al menos 3 vectores de prueba para el programa. Para definir un vector de prueba debes llevar al sistema a un estado, generar los eventos y observar el estado siguiente y las acciones que ocurrirán. Por tanto, un vector de prueba tiene unas condiciones iniciales del sistema, unos resultados esperados y los resultados realmente obtenidos. Si el resultado obtenido es igual al esperado entonces el sistema pasó el vector de prueba, de lo contrario el sistema puede tener un error.

VECTOR DE PRUEBA 1:

``` py
current_state = STATE_INIT

    if current_state == STATE_INIT:
        display.show(Image.HAPPY)
        start_time = utime.ticks_ms()
        interval = HAPPY_INTERVAL
        current_state = STATE_HAPPY
```

En este vector de prueba se espera que pase del estado inicial que es STATE_INIT a STATE_HAPPY 

VECTOR DE PRUEBA 2: 

``` py
    current_state = STATE_HAPPY
    display.show(Image.HAPPY)
    start_time = utime.ticks_ms()
    interval = HAPPY_INTERVAL

    button_a.was_pressed()

    if current_state == STATE_HAPPY and button_pressed:
        display.show(Image.SAD)
        start_time = utime.ticks_ms()
        interval = SAD_INTERVAL
        current_state = STATE_SAD
```

Este vector de prueba sirve comproobar que al presionar el boton A se cambie la expresión en este caso se tiene como estado inicial STATE_HAPPY y al presionar el boton A se debe de cambiar a STATE_SAD 

VECTOR DE PRUEBA 3: 

``` py
current_state = STATE_SMILE
    display.show(Image.SMILE)
    start_time = utime.ticks_ms()
    interval = SMILE_INTERVAL

    utime.sleep_ms(interval + 100)

    if current_state == STATE_SMILE and utime.ticks_diff(utime.ticks_ms(), start_time) > interval:
        display.show(Image.SAD)
        start_time = utime.ticks_ms()
        interval = SAD_INTERVAL
        current_state = STATE_SAD
```
En este caso el vector de prueba sirve para coomprobar que una vez pase el tiempo necesario se cambbia de estado, en este caso iniciamos con STATE_SMILE y al agostarse el tiempo la expresión cambia a STATE_SAD

