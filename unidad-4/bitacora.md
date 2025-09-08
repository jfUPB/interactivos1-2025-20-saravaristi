# Evidencias de la unidad 4

## Código

[Enlace a la aplicación a modificar](https://editor.p5js.org/generative-design/sketches/P_2_2_3_02)

Código a modificar:

``` js
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
}

function draw() {
  // floating towards mouse position
  centerX += (mouseX - centerX) * 0.01;
  centerY += (mouseY - centerY) * 0.01;

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
  centerX = mouseX;
  centerY = mouseY;

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

[Enlace a la aplicación modificada](https://editor.p5js.org/saravaristi/sketches/iFc36sipn)

Código modificado:

``` js
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

    let buffer = "";
    while (true) {
      const { value, done } = await reader.read();
      if (done) break;
      if (value) {
        buffer += new TextDecoder().decode(value);
        let lines = buffer.split("\n");
        buffer = lines.pop(); // guarda lo que no está completo

        for (let line of lines) {
          let parts = line.trim().split(",");
          if (parts.length === 4) {
            let xRaw = parseInt(parts[0]);
            let yRaw = parseInt(parts[1]);
            buttonA = parseInt(parts[2]);
            buttonB = parseInt(parts[3]);

            // Mapear acelerómetro a pantalla
            microbitX = map(xRaw, -1024, 1024, 0, width);
            microbitY = map(yRaw, -1024, 1024, 0, height);
            
          // 2) botones: acepta "1"/"0" o "True"/"False"
  const toBool = t => {
    const v = String(t).toLowerCase();
    return v === "1" || v === "true";
  };

  const aPressed = toBool(parts[2]);
  const bPressed = toBool(parts[3]);

  // (opcional) guarda estados por si quieres mostrarlos en pantalla
  buttonA = aPressed ? 1 : 0;
  buttonB = bPressed ? 1 : 0;

  // 3) acciones equivalentes a teclas '1' y '2'
  if (aPressed) filled = false; // '1' → solo contorno
  if (bPressed) filled = true;  // '2' → relleno


          }
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

## Video

[Video demostratativo](https://youtu.be/b4cBYHa1NpY)

## 🤔 Fase: Reflect 

### 1. ¿Qué es un protocolo de comunicación y por qué es importante en la comunicación serial? 

Un protocolo de comunicación es una serie de instrucciones que hay entre dos dispositivos para recibir y enviar datos el uno al otro, esto es importante para la comunicacion serial para que los datos lleguen completos y no hayan perdidas de información

### 2. ¿Por qué se separan los datos con comas en el protocolo ASCII que exploramos? 

En ASCII se separan los datos con comas para que no hayan confusiones a la hora ingresar datos, ya que al ingresar datos como numeros estos pueden ser ingresados erroneamente

### 3. ¿Por qué es necesario terminar los datos con un carácter que marque el fin del mensaje? 

Es para saber donde inicia y termina un paquete de datos

### 4. ¿Por qué fue necesario usar una máquina de estados en la aplicación modificada de p5.js? 

En este caso se usa para verificar el estado de las teclas del teclado y los botones del microbit, esto se hace es esta forma para evitar que los estados no se ejecuten correctamente y no hayan complicaciones

### 5. ¿Cómo se formatean los datos en el micro:bit para ser enviados por el puerto serial? 

En el codigo dado por el profe se formatean los datos xValue, yValue, aState y bState, estos sirven ara tener los datos en X y Y del acelerometro y los estados de los botones A y B del microbit

### 6. ¿Qué significa que los datos enviados por el micro:bit están codificados en ASCII? 

Esto se refiere a que cada uno de los datos tiene un número especifico de manera que el computador pueda enteder la información dada

### 7. ¿Por qué es necesario en la aplicación de p5.js preguntar si hay bytes disponibles en el puerto serial antes de leerlos? 

Esto es necesario cuando hay dispositivo que envia datos a diferentes velocidades y al usar serial.available() la aplicación puede detectar de forma mas eficiente estos datos y leerlos cuando esten listos

### 8. ¿Qué hiciste bien en esta unidad que debes continuar haciendo? 

En esta unidad siento que hice bien la parte de desglozar el codigo y comprenderlo a fondo para asi poder elegir que funciones eran las que queria implementar con el microbit y darme la idea de como hacerlas y solo decirle a la IA lo que necesitaba claramente, pero teniendo en cuenta lo que habia aprendido sobre el codigo y la forma en la que queria que se ejecutara

### 9. ¿Qué deberías comenzar a hacer para mejorar tu proceso?

Creo que deberia de commenzar a investigar mas profundamente a la hora de realizar codigos ya que creo qque aun me falta mucho ppara aprender y comprender mucho mejor los temas que se tratan en cada una de las unidades y las complicaciones que traen cada uno de estos



