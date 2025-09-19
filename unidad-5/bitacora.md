
# Evidencias de la unidad 5

## Actividad 01 

### 1. Describe cómo se están comunicando el micro:bit y el sketch de p5.js. ¿Qué datos envía el micro:bit?

En este caso el microbit envia datos tales como el acelerometro (posiciones en xValue y yValue) y los botones A y B

### 2. ¿Cómo es la estructura del protocolo ASCII usado? 

En este caso se toman primero los datos xValue y yValue, estos seguidos de los datos aState y bState

### 3. Muestra y explica la parte del código de p5.js donde lee los datos del micro:bit y los transforma en coordenadas de la pantalla. 

<img width="686" height="612" alt="image" src="https://github.com/user-attachments/assets/e5a3e275-179f-4544-a932-baa04a2604aa" />

En esta parte se leen todos los datos del microbit y se asegura de que se esten tomando los 4 datos

### 4. ¿Cómo se generan los eventos A pressed y B released que se generan en p5.js a partir de los datos que envía el micro:bit? 

Estos eventos se generan cuando el boton A o B estam siendo presionados, en este caso dejar presionado A hace que se dibuje en la pantalla hasta que el boton se deje de presionar, mientras que el boton B tiene como función cambiar el color del trazo, pero el cambio solo es visible una vez el boton B deje de ser presionado

### 5. Capturas de pantalla de los algunos dibujos que hayas hecho con el sketch. 

<img width="746" height="874" alt="image" src="https://github.com/user-attachments/assets/8af6a5ba-213d-4152-b4ef-2aaa83fafc2b" />

## Actividad 02 

### 1. Captura el resultado del experimento anterior. ¿Por qué se ve este resultado? 

<img width="1239" height="365" alt="image" src="https://github.com/user-attachments/assets/9a6b20a3-a5c5-43a1-b28d-244cfb34b7ed" />

Este resultado se ve de estar forma ya que esta en binario y los caracteres no los reconoce como texto, por lo que tiene que hacerse visible usando otro formato

### 2. Captura el resultado del experimento anterior. Lo que ves ¿Cómo está relacionado con esta línea de código? 
<img width="1254" height="376" alt="image" src="https://github.com/user-attachments/assets/b023e533-ba57-4987-b74a-5505e372f130" />

Esto se relaciona con el codigo de forma que cada 6 bytes representan un paquete completo con el formato >2h2B
### 3. ¿Qué ventajas y desventajas ves en usar un formato binario en lugar de texto en ASCII? 

Tengo entendido que una de las ventajas que hay al usar binario en lugar de texto en ASCII es que el binario ocupa menos lugar que el texto y mayor velocidad al interpretar los datos, por lo que supongo que una de las desventajas es que el binario no es entendible a plena vista 

### 4. Captura el resultado del experimento. ¿Cuántos bytes se están enviando por mensaje? ¿Cómo se relaciona esto con el formato '>2h2B'? ¿Qué significa cada uno de los bytes que se envían? 

<img width="1241" height="257" alt="image" src="https://github.com/user-attachments/assets/b192d877-0c86-4ba2-891e-ef9fa8ad3e15" />

Se estan mandando 6 bytes al hacer el gesto shake con el microbit, al usar >2h2B se estan enviado bloqjues de 6 bytes, en este caso 07 f8 son el xValue, fb 94 son el yValue y 00 es aState y 00 es bState

### 5. Recuerda de la unidad anterior que es posible enviar números positivos y negativos para los valores de xValue y yValue. ¿Cómo se verían esos números en el formato '>2h2B'? 

en >2h2b xe ve normal en en hex, por ejemplo 03 E8, pero si esta en negativo se ve en complemento a dos, por ejemplo FC 08 

### 6. ¿Qué diferencias ves entre los datos en ASCII y en binario? ¿Qué ventajas y desventajas ves en usar un formato binario en lugar de texto en ASCII? ¿Qué ventajas y desventajas ves en usar un formato ASCII en lugar de binario? 

<img width="1236" height="282" alt="image" src="https://github.com/user-attachments/assets/c93f7ea8-1cf4-4e1b-a7dc-44f83fc244e3" />

Esta parte es binario 04 c0 fc 04 00 00, luego le sigue esta parte en ASCII 04 c0 fc 04 00 00, esta parte es ASCII como texto 31 32 31 36 2c 2d 31 30 32 30 2c 46 61 6c 73 65 2c 46 61 6c 73 65 0a ("1216,-1020,False,False\n"). En cuanto a las ventajs y desventajas de usar binario en vez de ASCII estas son que es mucho mejor para codigos que requieren usar menos espacio de texto, pero no es entendible a la hora de leerlo, por otro lado el ASCII es mas usado que el binario ya que la mayoria de programas entiende texto, pero es mucho mas pesado que el binario 

## Actividad 03

### 1. Compara el código de la unidad anterior relacionado con la recepción de los datos seriales que ves ahora. ¿Qué cambios observas? 

### 2. ¿Qué ves en la consola? ¿Por qué crees que se produce este error? 

<img width="805" height="106" alt="image" src="https://github.com/user-attachments/assets/32ff3c70-c866-47ff-a1d4-46159a3a869d" />
En este caso es un error de interpretación de datos, lo que sucede es que los datos que llegan del microbit como xValue, yValue, aState y bState no son los que el programa espera, ya que el formato de paquete no corresponde o hay un desajuste en el orden de envio y lectura

### 3. Analiza el código, observa los cambios. Ejecuta y luego observa la consola. ¿Qué ves? 

<img width="796" height="81" alt="image" src="https://github.com/user-attachments/assets/eb9dcca3-669f-4920-b562-24d0698b391d" />


### 4. ¿Qué cambios tienen los programas y ¿Qué puedes observar en la consola del editor de p5.js? 

En este caso la consola funciona de forma normal, sin errores 

## Actividad 04 

### Proceso 

Para confirmar que el codigo dado por el profe hacia que el microbit estuviese mandando datos en binario lo revise con la aplicación de conexión de datos y en efecto si estaba mandando datos en binario 

<img width="1253" height="381" alt="image" src="https://github.com/user-attachments/assets/c7e79d7d-8bc0-4bd9-8a03-43ab5067ecb8" />

Luego de eso ya pase a la parte del codigo, lo que hice fue cambiar el connectMicrobit, para que permitiera el protocolo de datos binarios y en consola se vieran los valores de xValue, yValue, aState y bState, pero a la hora de conectar el microbit los datos de xValue y yValue se iban muy lejos del canvas y no se mostraban en pantalla, eso pasaba debido a esta linea de codigo donde se convertian los valores y la tuve que cambiar a una forma muy similar a una usada en el ejemplo dado por el profesor, pero si muestra los datos del microbit

parte a cambiar:

```js
if (buffer.length === 8) { // paquete completo
            const xRaw = (buffer[1] << 8) | buffer[2];
            const yRaw = (buffer[3] << 8) | buffer[4];
            const aPressed = buffer[5] === 1;
            const bPressed = buffer[6] === 1;
            const checksum = buffer[7];
```

https://github.com/user-attachments/assets/a296c34f-c854-4a1d-a83f-31ca3f3ba44c

Luego de solucionar eso, ya los datos binarios se mostraban y el programa funciona normalmente

Codigo modificado

```js
// P_2_2_3_02
//
// Generative Gestaltung – Creative Coding im Web
// ISBN: 978-3-87439-902-9, First Edition, Hermann Schmidt, Mainz, 2018
// Benedikt Groß, Hartmut Bohnacker, Julia Laub, Claudius Lazzeroni
// with contributions by Joey Lee and Niels Poldervaart
// Copyright 2018
//
// http://www.generative-gestaltung.de
//
// Licensed under the Apache License, Version 2.0 (the "License");
// you may not use this file except in compliance with the License.
// You may obtain a copy of the License at http://www.apache.org/licenses/LICENSE-2.0
// Unless required by applicable law or agreed to in writing, software
// distributed under the License is distributed on an "AS IS" BASIS,
// WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
// See the License for the specific language governing permissions and
// limitations under the License.

/**
 * form mophing process by connected random agents
 * two forms: circle and line
 *
 * MOUSE
 * click               : start a new circe
 * position x/y        : direction and speed of floating
 *
 * KEYS
 * 1-2                 : fill styles
 * 3-4                 : form styles circle/line
 * arrow up/down       : step size +/-
 * f                   : freeze. loop on/off
 * Delete/Backspace    : clear display
 * s                   : save png
 */

'use strict';

var formResolution = 15;
var stepSize = 2;
var distortionFactor = 1;
var initRadius = 150;
var centerX;
var centerY;
var x = [];
var y = [];

var filled = false;
var freeze = false;
var drawMode = 1;

let port;
let reader;
let microbitX = 0;
let microbitY = 0;
let buttonA = 1;
let buttonB = 0;
let connectButton;

function setup() {
  createCanvas(windowWidth, windowHeight);

  // init shape
  centerX = width / 2;
  centerY = height / 2;
  var angle = radians(360 / formResolution);
  for (var i = 0; i < formResolution; i++) {
    x.push(cos(angle * i) * initRadius);
    y.push(sin(angle * i) * initRadius);
  }

  stroke(0, 50);
  strokeWeight(0.75);
  background(255);
  setupMicrobitButton();
}

function setupMicrobitButton() {
  connectButton = createButton("Conectar micro:bit");
  connectButton.position(20, 20);
  connectButton.mousePressed(connectMicrobit);
}

async function connectMicrobit() {
  try {
    port = await navigator.serial.requestPort();
    await port.open({ baudRate: 115200 });
    reader = port.readable.getReader();
    console.log("Conectado al micro:bit");

    while (true) {
      const { value, done } = await reader.read();
      if (done) break;
      if (!value) continue;

      const dataBytes = new Uint8Array(value);

      // asegurarnos de que sea un paquete completo (1 byte cabecera + 6 datos + 1 checksum = 8)
      if (dataBytes.length === 8 && dataBytes[0] === 0xAA) {
        let buffer = dataBytes.buffer;
        let view = new DataView(buffer);

        let xRaw = view.getInt16(1, false); // big-endian
        let yRaw = view.getInt16(3, false);
        let aPressed = view.getUint8(5) === 1;
        let bPressed = view.getUint8(6) === 1;
        let checksum = view.getUint8(7);

        // Verificación de checksum
        let sum = 0;
        for (let i = 1; i < 7; i++) sum += dataBytes[i];
        let calculatedChecksum = sum % 256;

        if (checksum === calculatedChecksum) {
          console.log("Paquete válido:", xRaw, yRaw, aPressed, bPressed);

          // Actualizar variables globales
          microbitX = map(xRaw, -1024, 1024, 0, width);
          microbitY = map(yRaw, -1024, 1024, 0, height);
          buttonA = aPressed;
          buttonB = bPressed;

          // Acciones equivalentes a teclas '1' y '2'
          if (aPressed) filled = false; // tecla '1'
          if (bPressed) filled = true;  // tecla '2'

        } else {
          console.warn("Checksum incorrecto, paquete descartado");
        }
      }
    }
  } catch (err) {
    console.error("Error conectando micro:bit:", err);
  }
}


// Funciones para usar en vez de mouseX/mouseY
function getMicrobitMouseX() {
  return microbitX || mouseX;
}
function getMicrobitMouseY() {
  return microbitY || mouseY;
}

function draw() {
  // floating towards mouse position
 centerX += (getMicrobitMouseX() - centerX) * 0.01;
centerY += (getMicrobitMouseY() - centerY) * 0.01;

  // calculate new points
  for (var i = 0; i < formResolution; i++) {
    x[i] += random(-stepSize, stepSize);
    y[i] += random(-stepSize, stepSize);
  }

  if (filled) {
    fill(random(255));
  } else {
    noFill();
  }

  switch (drawMode) {
  case 1: // circle
    beginShape();
    // start controlpoint
    curveVertex(x[formResolution - 1] + centerX, y[formResolution - 1] + centerY);

    // only these points are drawn
    for (var i = 0; i < formResolution; i++) {
      curveVertex(x[i] + centerX, y[i] + centerY);
    }
    curveVertex(x[0] + centerX, y[0] + centerY);

    // end controlpoint
    curveVertex(x[1] + centerX, y[1] + centerY);
    endShape();
    break;
  case 2: // line
    beginShape();
    // start controlpoint
    curveVertex(x[0] + centerX, y[0] + centerY);

    // only these points are drawn
    for (var i = 0; i < formResolution; i++) {
      curveVertex(x[i] + centerX, y[i] + centerY);
    }

    // end controlpoint
    curveVertex(x[formResolution - 1] + centerX, y[formResolution - 1] + centerY);
    endShape();
    break;
  }
}

function mousePressed() {
  // init shape on mouse position
centerX = getMicrobitMouseX();
centerY = getMicrobitMouseY();

  switch (drawMode) {
  case 1: // circle
    var angle = radians(360 / formResolution);
    var radius = initRadius * random(0.5, 1);
    for (var i = 0; i < formResolution; i++) {
      x[i] = cos(angle * i) * radius;
      y[i] = sin(angle * i) * radius;
    }
    break;
  case 2: // line
    var radius = initRadius * random(0.5, 5);
    var angle = random(PI);

    var x1 = cos(angle) * radius;
    var y1 = sin(angle) * radius;
    var x2 = cos(angle - PI) * radius;
    var y2 = sin(angle - PI) * radius;
    for (var i = 0; i < formResolution; i++) {
      x[i] = lerp(x1, x2, i / formResolution);
      y[i] = lerp(y1, y2, i / formResolution);
    }
    break;
  }
}

function keyReleased() {
  if (key == 's' || key == 'S') saveCanvas(gd.timestamp(), 'png');
  if (keyCode == DELETE || keyCode == BACKSPACE) background(255);
  if (key == '1') filled = false;
  if (key == '2') filled = true;
  if (key == '3') drawMode = 1;
  if (key == '4') drawMode = 2;

  if (keyCode == UP_ARROW) stepSize++;
  if (keyCode == DOWN_ARROW) stepSize--;
  stepSize = max(stepSize, 1);

  // pause/play draw loop
  if (key == 'f' || key == 'F') freeze = !freeze;
  if (freeze) {
    noLoop();
  } else {
    loop();
  }
}
```

https://github.com/user-attachments/assets/6338e23d-1827-4e4d-ae22-54d5509c4011

















