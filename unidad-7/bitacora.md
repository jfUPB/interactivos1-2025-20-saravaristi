
# Evidencias de la unidad 7

## Actividad 01 

### ¿Qué URL de Dev Tunnels obtuviste? ¿Por qué crees que necesitamos usar esta URL en lugar de http://localhost:3000 o la IP local de tu computador para que el celular se conecte? 

El port me dio esta URL https://fxfbq7z6-3000.use2.devtunnels.ms/ en este caso necesitamos este tipo de URL ya que es una URL publica y en internet en vez de una local donde se podia acceder sin necesidad de internet de por medio

### Describe brevemente qué hace npm install y npm start. 

npm install lo que hace es descargar las dependencias y npm start inicia el servidor

### ¿Qué mensajes observaste en la terminal del servidor al conectar el cliente de escritorio y el cliente móvil? ¿Eran diferentes los mensajes o identificadores? 

<img width="1126" height="323" alt="image" src="https://github.com/user-attachments/assets/182fbd7c-46b6-4372-ab41-d646ef1e56e0" />

Estos mensajes muestran la posición en X y Y del circulo rojo cuando se mueve con el touch del celular

### Describe el comportamiento observado: ¿Funcionó la interacción? ¿Hubo algún retraso (latencia)?

Si funciono, pero habia un poco de delay en el computador al mover el circulo con el touch del telefono de forma rapida, veo que no detecta un solo toque en la pantalla, es decir que si o si debo de hacer el gesto de mover el dedo para que el circulo cambie de posición

## Actividad 02 

### Explica con tus propias palabras: ¿Por qué es necesario Dev Tunnels en este escenario y cómo funciona conceptualmente? 

Como tal Dev Tunnels funciona como un intermedirario entre el localhost y la URL creada donde al conectarse a la URL se reenvia la conexión hasta el localhost y cuando hay interacciones las respuestas viajan desde el servidor a la URL

### Describe la función de touchMoved() y por qué se usa la variable threshold en el cliente móvil. 

touchMoved() sirve para detectar el movimiento de el dedo en la pantalla ya que tiene los valores mouseX y mouseY, en el caso de threshold funciona de forma en que no se envia cualquier pequeño movimiento del dedo sobre la pantalla, se encarga de solo enviar los movimientos significativos, esto con el objetivo de evitar inundad la red de mensajes

### Compara brevemente Dev Tunnels con simplemente usar la IP local. ¿Cuáles son las ventajas y desventajas de cada uno?

Al usar Dev Tunnel no necesitamos depender de que ambos dispositivos esten en la misma red, mientras que con la IP local si se depende de eso y de que no hayan firewalls bolqueadas por lo que si se abre el localhost desde el celular se estaria buscando un servidor enn el celular pero no el que esta ya en el computador

### Coloca en tu bitácora capturas de pantalla del sistema completo funcionando. Esto lo puedes hacer abriendo tanto el mobile como el desktop en tu computador y tomando una captura de pantalla de todos los involucrados (celular, computador y terminal).  

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/5676a8b3-f3bb-462f-8fb4-45702d9f704e" />

https://github.com/user-attachments/assets/f84e6e63-40c0-471b-8dcb-570ceae432b1

## Actividad 03 

### ¿Cuál es la función principal de express.static(‘public’) en este servidor? ¿Cómo se compara con el uso de app.get(‘/ruta’, …) del servidor de la Unidad 6?

express.static(‘public’) convierte la carpeta public en la raiz del servidor osea que en vez de tener un index.html lo que se tiene es un localhost al que solo se le debe de poner la ruta a la pagina especifica como /desktop/, mientras que app.get(‘/ruta’, …) lo que hace es responder manualmente a la ruta agregando un index.html

### Explica detalladamente el flujo de un mensaje táctil: ¿Qué evento lo envía desde el móvil? ¿Qué evento lo recibe el servidor? ¿Qué hace el servidor con él? ¿Qué evento lo envía el servidor al escritorio? ¿Por qué se usa socket.broadcast.emit en lugar de io.emit o socket.emit en este caso? 

Primero los eventos wue envian desde el movil es touchstart, touchmove y touchend, el evento que lo recibe en el servidor es socket.on('message', (message) donde lo valida

### Si conectaras dos computadores de escritorio y un móvil a este servidor, y movieras el dedo en el móvil, ¿Quién recibiría el mensaje retransmitido por el servidor? ¿Por qué? 

Los dos computadores son quienes reciben la retransmición porque socket.broadcast.emit envia el evento a todos menos al celular que es el emisor

### ¿Qué información útil te proporcionan los mensajes console.log en el servidor durante la ejecución? 

En el codigo console.log informa cuando hay un nuevo cliente conectado al servidor, muestra cada mensaje qque se proporciona en el servidor como los cambios a la hora de mover el dedo en el panel de la version movil y avisa cuanto un cliente se desconecta del servidor

## Actividad 04  

### Realiza un diagrama donde muestres el flujo completo de datos y eventos entre los tres componentes: móvil, servidor y escritorio. Puedes ilustrar con un ejemplo de coordenadas táctiles (x, y) y cómo viajan a través del sistema. 

<img width="391" height="732" alt="image" src="https://github.com/user-attachments/assets/7b6cd754-2ede-4383-9c72-c1911f2f8f4f" />

## Actividad 05 

### Idea

Mi idea era hacer unos visuales donde los fondos fueran gifs y se pudieran cambiar al usar el touch de la pantalla tactil, los visuales son fotos png que se mueven dependiendo de las frecuencias altas y bajas 

### Codigo 

### Index.hmtl desktop 

```js
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
  background: transparent;
}
canvas {
  position: relative;
  z-index: 1;      /* encima del video */
  background: transparent !important;
}
  </style>
</head>
<body></body>
</html>
```
### Sketch.js desktop
```js
// === Desktop sketch: video de fondo en canvas + visuales por bandas (bass/mid/treble) ===
let socket;

// AUDIO
let song = null;
let fft = null;
let amp = null;

// VISUALES
let visualImages = []; // [bass, mid, treble]
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

  ['/assets/visuals/visual1.png','/assets/visuals/visual2.png','/assets/visuals/visual3.png']
    .forEach((p,i) => loadImage(
      p,
      img => { visualImages[i] = img; console.log('loaded', p); },
      ()  => console.warn('No cargó', p)
    ));

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

  // Umbrales (ligeramente más fáciles)
  const thrLow  = map(sRMS, 0, 1, 0.50, 0.75, true) * 255;
  const thrMid  = map(sRMS, 0, 1, 0.46, 0.70, true) * 255;
  const thrHigh = map(sRMS, 0, 1, 0.44, 0.70, true) * 255;

  const canSpawn = (millis() - lastSpawnAt) > SPAWN_COOLDOWN_MS;
  const room = particles.length < MAX_PARTICLES;

  if (room && canSpawn && bass > thrLow  && random() < 0.55) { spawn('bass',  bass);  lastSpawnAt = millis(); }
  if (room && canSpawn && mid  > thrMid  && random() < 0.40) { spawn('mid',   mid);   lastSpawnAt = millis(); }
  if (room && canSpawn && treb > thrHigh && random() < 0.35) { spawn('treble',treb);  lastSpawnAt = millis(); }

  // === NUEVO: Forzar aparición rotando bandas ===
  if (room && millis() - lastForce > FORCE_SPAWN_EVERY_MS) {
    spawn(bandCycle[bandIdx], 180);
    bandIdx = (bandIdx + 1) % bandCycle.length;
    lastForce = millis();
  }

  // Respaldo si todo muy bajo
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
  // Imagen por banda con fallback
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

// === comportamiento por banda (mismo que tenías, sin cambios fuertes) ===
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

// Debug (opcional con tecla D)
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

// Teclas de test: 1=bass, 2=mid, 3=treble
function keyPressed(){
  if (key === 'd' || key === 'D') showDebug = !showDebug;
}
```
### Index.html mobile
```js
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
### Sketch.js mobile 
```js
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
### Server.js
```js
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

### Capturas

<img width="753" height="360" alt="image" src="https://github.com/user-attachments/assets/1e1f2e0e-c390-4fc9-8324-483cff142207" />

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/6507ff00-de9b-4fa7-ad5b-3c951f2853e4" />

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/8cd88120-f171-4b68-bd1f-35617ebd3f9c" />

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/b17b5c6c-82c5-4dac-85f6-a238e41d952f" />

<img width="801" height="332" alt="image" src="https://github.com/user-attachments/assets/b55ad15a-d7a4-445f-b104-7e90636e16ef" />

### Video 

https://github.com/user-attachments/assets/e2989d8b-09d8-4380-b5c9-9363e358dacc

## Autoevaluación 

Como tal esta vez yo me pongo una nota de 4.5 ya que a pesar de que hice todos los ejercicios en realidad tuve bastantes problemas a la hora de hacer el codigo para la actividad 5 ya que esta no funciono demasiadas veces ya sea por fallos en server.js, fallas con los visuales y el audio o simplemente codigos que no funcionaban, a pesar de que hice lo posible para solucionarlos muchas veces me toco hacer todo desde cero y logre solucionarlo al cambiar las rutas de las bibliotecas de p5.sound y el socket io ademas re organizar los elementos den draw




