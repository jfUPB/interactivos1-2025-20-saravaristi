# Unidad 3


## 🛠 Fase: Apply

### Actividad 06 


``` py
let estado = "CONFIG";
let PASSWORD = ['A','B','A'];
let keyInput = [];
let keyIndex = 0;
let count = 20;
let startTime = 0;

function setup() {
  createCanvas(400, 400);
  textAlign(CENTER, CENTER);
  textSize(32);
  startTime = millis();
}

function draw() {
  background(220);

  switch (estado) {
    case "CONFIG":
      STATE_CONFIG();
      break;

    case "ARMED":
      STATE_ARMED();
      break;

    case "EXPLODED":
      STATE_EXPLODED();
      break;
  }
}

function STATE_CONFIG() {
  fill(0);
  text("CONFIG", width/2, 50);
  text("Tiempo: " + count, width/2, height/2);
  text("A: +1  B: -1  Shake: ARMAR", width/2, height - 50);
}

function STATE_ARMED() {
  fill(0);
  text("ARMED", width/2, 50);
  text("Cuenta regresiva: " + count, width/2, height/2);
  text("Introduce clave", width/2, height - 50);

  if (millis() - startTime > 1000) {
    startTime = millis();
    count--;
    if (count <= 0) {
      estado = "EXPLODED";
    }
  }
}

function STATE_EXPLODED() {
  fill("red");
  text("EXPLODED", width/2, height/2);

}

function keyPressed() {
  if (estado === "CONFIG") {
    if (key === 'A') {
      count = min(count + 1, 60);
    } 
    else if (key === 'B') {
      count = max(10, count - 1);
    }
    else if (key === 'S') { // shake
      startTime = millis();
      estado = "ARMED";
    }
  } 
  
  else if (estado === "ARMED") {
    if (key === 'A' || key === 'B') {
      keyInput[keyIndex] = key;
      keyIndex++;

      if (keyIndex === PASSWORD.length) {
        let passIsOK = true;
        for (let i = 0; i < PASSWORD.length; i++) {
          if (keyInput[i] !== PASSWORD[i]) {
            passIsOK = false;
            break;
          }
        }
        if (passIsOK) {
          count = 20;
          keyIndex = 0;
          keyInput = [];
          estado = "CONFIG";
        } else {
          keyIndex = 0;
          keyInput = [];
        }
      }
    }
  } 
}
```
