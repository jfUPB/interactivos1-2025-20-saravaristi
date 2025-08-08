# Unidad 2

## 🛠 Fase: Apply 

### Actividad 04 

### Actividad 05 

``` py
from microbit import *
import utime
import music

MIN_TIEMPO = 10
MAX_TIEMPO = 60
TIEMPO_INICIAL = 20
INTERVALO_MS = 1000

estado = "STATE_INIT"
tiempo_restante = TIEMPO_INICIAL
ultimo_tiempo = utime.ticks_ms()

while True:
    if estado == "STATE_INIT":
        tiempo_restante = TIEMPO_INICIAL
        display.show(str(tiempo_restante))
        estado = "STATE_CONFIG"

    elif estado == "STATE_CONFIG":
        if button_a.was_pressed():
            if tiempo_restante < MAX_TIEMPO:
                tiempo_restante += 1
            display.show(str(tiempo_restante))
            utime.sleep_ms(200)

        if button_b.was_pressed():
            if tiempo_restante > MIN_TIEMPO:
                tiempo_restante -= 1
            display.show(str(tiempo_restante))
            utime.sleep_ms(200)

        if accelerometer.was_gesture("shake"):
            estado = "STATE_ARMED"
            ultimo_tiempo = utime.ticks_ms()
            display.show(str(tiempo_restante))

    elif estado == "STATE_ARMED":
        if utime.ticks_diff(utime.ticks_ms(), ultimo_tiempo) >= INTERVALO_MS:
            tiempo_restante -= 1
            ultimo_tiempo = utime.ticks_ms()
            if tiempo_restante > 0:
                display.show(str(tiempo_restante))
            else:
                estado = "STATE_EXPLODE"

        if pin_logo.is_touched():
            estado = "STATE_CONFIG"
            display.show(str(tiempo_restante))
            utime.sleep_ms(300)

    elif estado == "STATE_EXPLODE":
        display.show(Image.SKULL)
        music.play(music.WAWAWAWAA)
        utime.sleep(2)
        estado = "STATE_CONFIG"
        tiempo_restante = TIEMPO_INICIAL

```
