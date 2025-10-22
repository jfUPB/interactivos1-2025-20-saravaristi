
# Evidencias de la unidad 8

## Actividad 01 

### Documenta los referentes visuales que te inspiren. 

### Define el concepto de las visuales que quieres crear. 

Mi idea era hacer unos visuales donde los fondos fueran gifs y se pudieran cambiar al usar el touch de la pantalla tactil, los visuales son fotos png que se mueven dependiendo de las frecuencias altas y bajas, en este caso el movil funciona para cambiar los fondos, y el microbit funciona para cambiar las visuales por 2 paquetes diferentes de visuales donde cada uno le corresponde al boton A y B

### Explica cómo el móvil y el micro:bit controlarán las visuales.

El movil a partir de touch controla los fondos del programa, cada vez que el usuario toca la pantalla del celular se cambia entre 3 fondos secuencialmente, en el caso de los botones A y B del microbit cada uno corresponde a un paquete de visuales donde cada uno tiene su paquete prederterminado, al presionar A los visuales son los del paquete 1 y al presionar B los visuales son los del paquete 2

### Haz un bocetos de todas las interfaces del sistema. 

### Haz un diagrama que explique cómo se comunicarán los diferentes componentes del sistema.

## Actividad 02 

### Codigos 

### Microbit 

```py
from microbit import *
import utime

# Inicializar UART para comunicación serial (a 115200 baudios)
uart.init(baudrate=115200)

while True:
    if button_a.is_pressed():
        uart.write("BTN:A\n")
        display.show("A")
        utime.sleep(0.3)
        display.clear()

    if button_b.is_pressed():
        uart.write("BTN:B\n")
        display.show("B")
        utime.sleep(0.3)
        display.clear()

    # Añade una pausa pequeña para evitar saturar el buffer
    utime.sleep(0.1)

# Mostrar mariposa al final para confirmar conexión
display.show(Image.BUTTERFLY)
```




