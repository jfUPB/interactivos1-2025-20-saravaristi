# Unidad 1

## 🛠 Fase: Apply

### Actividad 05 
Se hizo un sistema fisico interactivo donde se tiene de inputs un microbit, su boton A y como outputs la interacción con el boton A dentro del codigo, el sistema dibuja un cuadrado y nos pide conectar el microbit luego tenemos que presionar el boton A (en el editor del microbit se tiene inicializado que se detecte cuando el boton A esta siendo presionado en el momento, si no se encuentra presionado se detectara como N) si se detecta que el boton A esta siendo presionado el cuadrado de color verde pasa a colorearse de rojo, si se deja de presionar el boton A el cuadrado vuelve a colorearse de verde que corresponde a N.
### Actividad 06 
[Enlace al codigo de la actividad 6](https://editor.p5js.org/saravaristi/sketches/2lKtahcFY) 

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
