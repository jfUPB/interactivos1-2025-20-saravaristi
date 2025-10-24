
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

### Proceso 

En este caso solo implemente los botones del Microbit al programa con ayuda de ChatGPT que me dio los codigos para el microbit y el bloque faltante para el Sketch,js del Desktop y el Index.html del Desktop, todos los demas codigos se mantuvieron iguales, fue un proceso facil y no se presentaron errores

### Codigos 

### Microbit 

```py
from microbit import *
from microbit import *
import utime

# Inicializar UART para comunicación serial (a 115200 baudios)
uart.init(baudrate=115200)

while True:
    if button_a.was_pressed():
        uart.write("BTN:A\n")
        display.show("A")
        utime.sleep(0.3)
        display.clear()

    if button_b.was_pressed():
        uart.write("BTN:B\n")
        display.show("B")
        utime.sleep(0.3)
        display.clear()

    # Añade una pausa pequeña para evitar saturar el buffer
    utime.sleep(0.1)
    display.show(Image.BUTTERFLY)
```
### Server.js 

```cpp
// server.js
const express = require('express');
const path = require('path');
const app = express();
const http = require('http').createServer(app);

// socket.io (sirve /socket.io/socket.io.js y maneja websockets)
const io = require('socket.io')(http, {
  // Útil si el móvil entra por DevTunnel (https) y el desktop por http local
  cors: { origin: true, methods: ['GET', 'POST'] }
});

const PORT = 3000;

// Log de cada request para depurar rutas/404 fácilmente
app.use((req, res, next) => {
  console.log('HTTP', req.method, req.url);
  next();
});

// Servir estáticos de /public (sin cache agresivo mientras desarrollas)
app.use(express.static(path.join(__dirname, 'public'), {
  etag: false,
  lastModified: false,
  cacheControl: false,
  maxAge: 0
}));

// Rutas de las apps
app.get('/desktop', (_req, res) => {
  res.sendFile(path.join(__dirname, 'desktop/index.html'));
});
app.get('/mobile', (_req, res) => {
  res.sendFile(path.join(__dirname, 'mobile/index.html'));
});

// Healthcheck
app.get('/health', (_req, res) => res.send('ok'));

// Socket.IO
io.on('connection', (socket) => {
  console.log('cliente conectado:', socket.id);

  socket.on('changeBackground', () => {
    console.log('changeBackground de', socket.id);
    // Retransmite a todos (desktop recibirá y cambiará el fondo)
    io.emit('changeBackground');
  });

  socket.on('disconnect', () => {
    console.log('cliente desconectado:', socket.id);
  });
});

// Importante para DevTunnel: escuchar en 0.0.0.0
http.listen(PORT, '0.0.0.0', () => {
  console.log(`servidor escuchando en http://localhost:${PORT}`);
});
```
### Index.html Desktop 

```cpp
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Visuales Musicales - Desktop</title>

  <!-- p5 y p5.sound desde CDN (p5 primero) -->
  <script src="https://cdn.jsdelivr.net/npm/p5@1.11.10/lib/p5.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/p5@1.11.10/lib/addons/p5.sound.min.js"></script>

  <!-- socket.io cliente por CDN -->
  <script src="https://cdn.socket.io/4.7.5/socket.io.min.js"></script>

  <!-- tu sketch -->
  <script src="sketch.js" defer></script>

  <style>
    html, body {
      margin: 0;
      padding: 0;
      height: 100%;
      overflow: hidden;
      background: black; /* antes estaba transparente: mejor usar negro */
    }
    canvas {
      position: fixed;
      top: 0;
      left: 0;
      z-index: 0; /* el canvas siempre al fondo */
      background: transparent !important;
    }

    /* === NUEVO: botón conectar microbit visible y fluido === */
    button {
      font-family: sans-serif;
      transition: background 0.25s;
    }

    #connectMicrobit {
      position: fixed;
      top: 20px;
      left: 20px;
      z-index: 10000;
      background: #333;
      color: white;
      padding: 10px 18px;
      border: none;
      border-radius: 6px;
      font-size: 16px;
      cursor: pointer;
    }

    #connectMicrobit:hover {
      background: #555;
    }
  </style>
</head>

<body>
  <!-- === NUEVO: botón físico en el DOM para conectar el microbit === -->
  <button id="connectMicrobit"> Conectar micro:bit</button>

  <script>
    // === NUEVO ===
    // Este script permite conectar el micro:bit y reenviar eventos a p5.js
    let port, reader;

    document.getElementById("connectMicrobit").addEventListener("click", async () => {
      try {
        port = await navigator.serial.requestPort();
        await port.open({ baudRate: 115200 });
        const decoder = new TextDecoderStream();
        const inputDone = port.readable.pipeTo(decoder.writable);
        const inputStream = decoder.readable;
        reader = inputStream.getReader();

        document.getElementById("connectMicrobit").innerText = "✅ micro:bit conectado";
        console.log("micro:bit conectado");

        // Enviar datos al sketch (si p5 ya está cargado)
        window.microbitReader = reader;
        listenToMicrobit();
      } catch (err) {
        console.error("Error conectando microbit:", err);
        document.getElementById("connectMicrobit").innerText = "❌ Error al conectar";
      }
    });

    async function listenToMicrobit() {
      while (true) {
        const { value, done } = await window.microbitReader.read();
        if (done) break;
        if (value) {
          console.log("Microbit dice:", value.trim());
          // reenviar al sketch.js si está listo
          if (window.handleMicrobitInput) window.handleMicrobitInput(value.trim());
        }
      }
    }
  </script>
</body>
</html>
```
### Sketch.js Desktop 

```cpp
// === Desktop sketch: video de fondo en canvas + visuales por bandas (bass/mid/treble) ===
let socket;
let serial;           // objeto p5.SerialPort
let latestData = "";

// AUDIO
let song = null;
let fft = null;
let amp = null;

// VISUALES
let visualImages = [];
let paquetes = [];
let paqueteActual = 0;
let particles = [];

// VIDEOS DE FONDO
const bgPaths = [
  '/assets/backgrounds/fondo1.mp4',
  '/assets/backgrounds/fondo2.mp4',
  '/assets/backgrounds/fondo3.mp4'
];
let vidEl = null;
let currentBg = 0;

// UI
let startBtn;
let started = false;
let lastAutoSpawn = 0;
let showDebug = false;

// Control de densidad
const MAX_PARTICLES = 80;
const SPAWN_COOLDOWN_MS = 180;
let lastSpawnAt = 0;

// Energías suavizadas
let sBass = 0, sMid = 0, sTreble = 0, sRMS = 0;

// === NUEVO: Forzar presencia de todas las bandas ===
const FORCE_SPAWN_EVERY_MS = 1500;
let lastForce = 0;
const bandCycle = ['bass','mid','treble'];
let bandIdx = 0;

// ---------------------------------------------------------------
function setup() {

  createCanvas(windowWidth, windowHeight);
  imageMode(CENTER);
  noStroke();

  socket = io();
  socket.on('connect', () => console.log('[desktop] socket conectado:', socket.id));
  socket.on('changeBackground', changeBackground);

  loadBackground(currentBg);

  // === NUEVO: Cargar paquetes ===
  cargarPaquetes();
  cargarPaqueteActual();

  createStartOverlay();
}

function createStartOverlay() {
  startBtn = createButton('Iniciar audio');
  startBtn.position(0, 0);
  startBtn.size(windowWidth, windowHeight);
  startBtn.style('background', '#000');
  startBtn.style('color', '#fff');
  startBtn.style('font-size', '28px');
  startBtn.style('border', 'none');
  startBtn.style('cursor', 'pointer');
  startBtn.style('z-index', '9999');
  startBtn.style('position', 'absolute');
  startBtn.mousePressed(startAudioFlow);
}

function startAudioFlow() {
  userStartAudio().then(() => {
    loadSound('/assets/style.mp3',
      snd => {
        song = snd; song.setVolume(0.9); song.loop();
        fft = new p5.FFT(0.9, 1024); fft.setInput(song);
        amp = new p5.Amplitude();    amp.setInput(song);
        started = true; if (startBtn) startBtn.remove();
      },
      () => { fft = new p5.FFT(0.9, 1024); amp = new p5.Amplitude(); started = true; if (startBtn) startBtn.remove(); }
    );
  });
}

// ---------------------- BACKGROUND VIDEO (canvas) ------------
function loadBackground(index) {
  if (vidEl) { try { vidEl.remove(); } catch (e) {} vidEl = null; }
  vidEl = createVideo(bgPaths[index], () => {
    vidEl.volume(0); vidEl.attribute('muted',''); vidEl.attribute('playsinline','');
    vidEl.loop(); vidEl.hide();
  });
  vidEl.elt.controls = false;
}
function changeBackground() { currentBg = (currentBg + 1) % bgPaths.length; loadBackground(currentBg); }

function windowResized() {
  resizeCanvas(windowWidth, windowHeight);
  if (startBtn) { startBtn.position(0,0); startBtn.size(windowWidth, windowHeight); }
}

// ---------------------- DRAW -------------------
function draw() {
  // fondo
  push(); imageMode(CORNER); clear(); if (vidEl) { try { image(vidEl,0,0,width,height); } catch(e){} } pop();

  if (!started || !fft || !amp) { fallbackSpawn(); renderParticles(); return; }

  fft.analyze();
  const bass = fft.getEnergy('bass');
  const mid  = fft.getEnergy(400, 2000);
  const treb = fft.getEnergy('treble');
  const rms  = amp.getLevel();

  const nB = constrain(bass/255,0,1), nM = constrain(mid/255,0,1), nT = constrain(treb/255,0,1);
  const nR = constrain(map(rms,0,0.35,0,1),0,1);
  const EASE = 0.15;
  sBass = lerp(sBass,nB,EASE); sMid = lerp(sMid,nM,EASE); sTreble = lerp(sTreble,nT,EASE); sRMS = lerp(sRMS,nR,EASE);

  const thrLow  = map(sRMS, 0, 1, 0.50, 0.75, true) * 255;
  const thrMid  = map(sRMS, 0, 1, 0.46, 0.70, true) * 255;
  const thrHigh = map(sRMS, 0, 1, 0.44, 0.70, true) * 255;

  const canSpawn = (millis() - lastSpawnAt) > SPAWN_COOLDOWN_MS;
  const room = particles.length < MAX_PARTICLES;

  if (room && canSpawn && bass > thrLow  && random() < 0.55) { spawn('bass',  bass);  lastSpawnAt = millis(); }
  if (room && canSpawn && mid  > thrMid  && random() < 0.40) { spawn('mid',   mid);   lastSpawnAt = millis(); }
  if (room && canSpawn && treb > thrHigh && random() < 0.35) { spawn('treble',treb);  lastSpawnAt = millis(); }

  if (room && millis() - lastForce > FORCE_SPAWN_EVERY_MS) {
    spawn(bandCycle[bandIdx], 180);
    bandIdx = (bandIdx + 1) % bandCycle.length;
    lastForce = millis();
  }

  if (room && canSpawn && bass < 22 && mid < 22 && treb < 22 && millis() - lastAutoSpawn > 300) {
    spawn(random(['bass','mid','treble']), 180);
    lastAutoSpawn = millis();
    lastSpawnAt = millis();
  }

  renderParticles();

  if (showDebug) {
    debugHUD({
      rms: nf(sRMS,1,2),
      bass: int(bass), mid: int(mid), treb: int(treb),
      thrLow: int(thrLow), thrMid: int(thrMid), thrHigh: int(thrHigh)
    });
  }
}

// ---------------------- PARTICLES -------------------
function spawn(band, energy) {
  const has3 = visualImages.filter(Boolean).length >= 3;
  let img = null;
  if (has3) {
    if (band === 'bass')   img = visualImages[0];
    if (band === 'mid')    img = visualImages[1];
    if (band === 'treble') img = visualImages[2];
  } else if (visualImages.length) {
    img = visualImages[(band === 'bass' ? 0 : band === 'mid' ? 1 : 2) % visualImages.length];
  }

  const baseSize =
    band === 'bass'   ? map(energy, 0, 255, 60, 200) :
    band === 'mid'    ? map(energy, 0, 255, 40, 120) :
                        map(energy, 0, 255, 36, 110);

  const startY =
    band === 'bass'   ? height + random(30, 140) :
    band === 'mid'    ? random(height*0.30, height*0.70) :
                        random(height*0.05, height*0.45);

  const startX = random(width);

  if (img) particles.push(new BandImageP(startX, startY, img, baseSize, band));
  else     particles.push(new BandCircleP(startX, startY, baseSize, band));
}

function renderParticles() {
  if (particles.length > MAX_PARTICLES) particles.splice(0, particles.length - MAX_PARTICLES);
  for (let i = particles.length - 1; i >= 0; i--) {
    particles[i].update(); particles[i].draw();
    if (particles[i].dead()) particles.splice(i, 1);
  }
}

// === comportamiento por banda ===
class BandImageP {
  constructor(x,y,img,s,band){
    this.x=x; this.y=y; this.img=img; this.baseS=s; this.s=s;
    this.a=255; this.band=band;
    if (band==='bass'){ this.vx=random(-0.5,0.5); this.vy=-random(2,5); this.pulse=random(TWO_PI); }
    else if (band==='mid'){ this.vx=random(-0.8,0.8); this.vy=random(-0.4,0.4); this.phase=random(TWO_PI); this.freq=random(0.02,0.05); }
    else { this.vx=random(-1.2,1.2); this.vy=random(-0.2,0.6); this.r=random(TWO_PI); this.rs=random(-0.03,0.03); }
  }
  update(){
    if (this.band==='bass'){
      this.vy -= 0.65 * sBass;
      this.s = this.baseS * (1.0 + 1.0*sBass + 0.2*sin(this.pulse));
      this.pulse += 0.15 + sBass*0.3;
    } else if (this.band==='mid'){
      const ampX = 18 + 40*sMid;
      this.x += sin(this.phase) * (0.5 + 1.2*sMid);
      this.phase += this.freq * (1.0 + 1.5*sMid);
      this.vy += (noise(frameCount*0.003, this.x*0.001)-0.5) * 0.12;
      this.vx += (noise(this.y*0.002, frameCount*0.004)-0.5) * 0.1;
      this.s = this.baseS * (1.0 + 0.5*sMid);
      this.x += map(sin(this.phase), -1, 1, -ampX, ampX) * 0.02;
    } else {
      this.vx += random(-0.7,0.7) * (0.8 + 1.8*sTreble);
      this.vy -= 0.05 * sTreble;
      this.r  += this.rs + (sTreble*0.22)*(this.rs<0?-1:1);
      this.s  = this.baseS * (1.0 + 0.45*sTreble);
    }
    this.x += this.vx; this.y += this.vy;
    const energyGlobal = max(sBass,sMid,sTreble);
    this.a -= 1.0 + (1.2*(1.0 - energyGlobal));
  }
  draw(){ push(); translate(this.x,this.y); if(this.r) rotate(this.r); tint(255,this.a); image(this.img,0,0,this.s,this.s); noTint(); pop(); }
  dead(){ return this.a<=0 || this.y<-300 || this.y>height+500 || this.x<-400 || this.x>width+400; }
}

class BandCircleP {
  constructor(x,y,s,band){
    this.x=x; this.y=y; this.baseS=s; this.s=s; this.a=255; this.band=band;
    this.vx=random(-0.6,0.6);
    this.vy=(band==='bass')?-random(1,3):(band==='mid'?random(-0.4,0.4):random(-0.2,0.8));
    this.phase=random(TWO_PI);
  }
  update(){
    if (this.band==='bass'){ this.vy -= 0.5 * sBass; this.s = this.baseS * (1.0 + 0.8*sBass); }
    else if (this.band==='mid'){ this.x += sin(this.phase) * (1.0 + 3.0*sMid); this.phase += 0.05 + 0.1*sMid; this.s = this.baseS * (1.0 + 0.45*sMid); }
    else { this.vx += random(-0.4,0.4) * (1.2*sTreble); this.vy -= 0.05 * sTreble; this.s = this.baseS * (1.0 + 0.35*sTreble); }
    this.x+=this.vx; this.y+=this.vy;
    this.a -= 1.2 + (1.0*(1.0 - max(sBass,sMid,sTreble)));
  }
  draw(){ noStroke(); fill(255,200,40,this.a); circle(this.x,this.y,this.s); }
  dead(){ return this.a<=0 || this.y<-300 || this.y>height+500 || this.x<-400 || this.x>width+400; }
}

// Fallback
function fallbackSpawn() {
  if (millis() - lastAutoSpawn > 300 && particles.length < MAX_PARTICLES) {
    spawn(random(['bass','mid','treble']), 160);
    lastAutoSpawn = millis();
  }
}

// Debug
function debugHUD({ rms, bass, mid, treb, thrLow, thrMid, thrHigh }) {
  push(); fill(255); textSize(14);
  let y=10; text('DEBUG (D para ocultar):',10,y); y+=18;
  if (rms !== null) {
    text('RMS: ' + rms,10,y); y+=16;
    text('Bass: ' + bass + '  ThrLow: ' + thrLow,10,y); y+=16;
    text('Mid:  ' + mid  + '  ThrMid: ' + thrMid,10,y); y+=16;
    text('Treble:'+ treb + '  ThrHigh:'+ thrHigh,10,y); y+=16;
  } else text('Analizadores aún no listos…',10,y);
  pop();
}

function keyPressed(){
  if (key === 'd' || key === 'D') showDebug = !showDebug;
  if (key === '1') spawn('bass', 200);
  if (key === '2') spawn('mid', 200);
  if (key === '3') spawn('treble', 200);
  if (key === 'p' || key === 'P') cambiarPaquete(); // <--- cambia de paquete
}

// === NUEVO: SISTEMA DE PAQUETES ===
function cargarPaquetes() {
  paquetes = [
    [ // paquete 1 (tu actual)
      loadImage('/assets/visuals/paquete1/visual1.png'),
      loadImage('/assets/visuals/paquete1/visual2.png'),
      loadImage('/assets/visuals/paquete1/visual3.png')
    ],
    [ // paquete 2 (nuevo)
      loadImage('/assets/visuals/paquete2/visual4.png'),
      loadImage('/assets/visuals/paquete2/visual5.png'),
      loadImage('/assets/visuals/paquete2/visual6.png')
    ]
  ];
}

function cargarPaqueteActual() {
  if (paquetes.length > 0) {
    visualImages = paquetes[paqueteActual];
    console.log('Paquete activo:', paqueteActual + 1);
  }
}

function cambiarPaquete() {
  paqueteActual = (paqueteActual + 1) % paquetes.length;
  cargarPaqueteActual();
}

function createMicrobitButton() {
  microbitBtn = createButton('Conectar micro:bit');
  microbitBtn.position(20, 20);
  microbitBtn.style('padding', '10px 16px');
  microbitBtn.style('background', '#222');
  microbitBtn.style('color', '#0f0');
  microbitBtn.style('border-radius', '8px');
  microbitBtn.style('border', '2px solid #0f0');
  microbitBtn.mousePressed(connectMicrobit);
}
createMicrobitButton();

async function connectMicrobit() {
  try {
    // Solicitar el puerto serial al navegador
    port = await navigator.serial.requestPort();
    await port.open({ baudRate: 115200 });

    const decoder = new TextDecoderStream();
    inputDone = port.readable.pipeTo(decoder.writable);
    reader = decoder.readable.getReader();

    console.log('✅ micro:bit conectado');
    microbitBtn.html('🟩 micro:bit conectado');

    listenToMicrobit();
  } catch (err) {
    console.error('❌ Error al conectar micro:bit:', err);
  }
}

async function listenToMicrobit() {
  try {
    while (true) {
      const { value, done } = await reader.read();
      if (done) break;
      if (value) {
        const msg = value.trim();
        if (msg.startsWith('BTN:')) {
          console.log('Microbit dice:', msg);
          if (msg === 'BTN:A') {
            cambiarPaquete(); // Cambia visuales con A
          } else if (msg === 'BTN:B') {
            cambiarPaquete(); // Cambia visuales con B
          }
        }
      }
    }
  } catch (e) {
    console.error('❌ Error leyendo micro:bit:', e);
  } finally {
    if (reader) reader.releaseLock();
  }
}
```
### Index.html Mobile 

```cpp
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Control - Mobile</title>

  <script src="https://cdn.jsdelivr.net/npm/p5@1.11.10/lib/p5.js"></script>
  <script src="https://cdn.socket.io/4.7.5/socket.io.min.js"></script>
  <script src="sketch.js" defer></script>

  <style>
    html,body{height:100%;margin:0;background:#000;color:#fff;display:flex;align-items:center;justify-content:center;font-family:sans-serif}
  </style>
</head>
<body>
  <div style="text-align:center">
    <h2>Toca la pantalla</h2>
    <p>Cada toque cambia el fondo del desktop</p>
  </div>
</body>
</html>
```

### Sketch.js Mobile 
```cpp
let socket;
function setup(){
  createCanvas(windowWidth, windowHeight);
  background(0);
  socket = io(); // mismo origen (DevTunnel + /mobile funciona)
  console.log('[mobile] socket conectado? esperando...');
  socket.on('connect', ()=> console.log('[mobile] conectado', socket.id));
}
function touchStarted(){
  socket.emit('changeBackground');
  background(random(40,255), random(40,255), random(40,255)); // feedback
  return false;
}
```






