
# Evidencias de la unidad 6

## Actividad 01

### ¿Qué ocurrió en la terminal cuando ejecutaste npm install? ¿Cuál crees que es su propósito? 

nmp install sirve para descargar las dependencias, lo que hace es descargar el servidor en el computador y espera a que funcione usando npm start

### ¿Qué mensaje específico apareció en la terminal después de ejecutar npm start? ¿Qué indica este mensaje? 

<img width="435" height="103" alt="image" src="https://github.com/user-attachments/assets/31c07c8c-49fc-49ca-82b7-bf45297d3a87" />

Aparece este mensaje que indica que el servidor ya esta funcionando y muestra el link del servidor para copiarlo en un navegador y abrir la page1 y page2 

### Describe lo que ves inicialmente en page1 y page2 en tu navegador. 

<img width="1751" height="983" alt="image" src="https://github.com/user-attachments/assets/dc947928-b990-41ee-a463-80161e5754f3" />

Se ven dos circulos los cuales dan la aparencia de estar conectado a pesar de estar en ventanas diferentes 

### ¿Qué mensajes aparecieron en la terminal del servidor cuando abriste page1 y page2? 

<img width="1013" height="673" alt="image" src="https://github.com/user-attachments/assets/c4c5c326-39f4-4a06-a258-2d589ac5b09e" />

Este mensaje significa que se esta esperando la conexión de la otra ventana para que el programa funcione 

### Describe qué sucede en ambas páginas del navegador cuando mueves una de las ventanas. ¿Cambia algo visualmente? ¿Qué mensajes aparecen (si los hay) en la consola del navegador (usualmente accesible con F12 -> Pestaña Consola) y en la terminal del servidor? 

https://github.com/user-attachments/assets/6309e0cd-2bd4-49ef-8c65-af762335aef2

En el video se ve que con el movimiento de las ventanas se va organizando la imagen, y si se sobreponene se dibujan ambas peloticas en la misma ventana 

<img width="941" height="939" alt="image" src="https://github.com/user-attachments/assets/8f2caadf-7472-4493-8b6f-994373dd763d" />
<img width="924" height="949" alt="image" src="https://github.com/user-attachments/assets/1e382a98-11eb-4f81-8eb9-2b45dfa5ca7f" />

Lo que se ve en las imagenes es el codigo pjs de la pagina y el apartado donde verifica el tamaño y la posición de la otra ventana como de la propia ventana para hacer la intereacción y dibujar en pantalla el visual segun los valores de ambas ventanas

## Actividad 02 

### Piensa en cómo te conectas a Internet en casa o en la Universidad. ¿Usas Wi-Fi? ¿Un cable de red? Eso es simplemente tu “rampa de acceso” a la gran red de carreteras. ¿Qué pasaría si esa rampa se corta? Anota tus ideas.

En ambos casos utilizo Wi-fi, cuando esa gran red se corta los datos no pueden ser recibidos por lo dispositivos conectados al servidor del internet y no se leen 

### ¿Puedes identificar otros ejemplos de relaciones Cliente-Servidor en tu vida diaria (no necesariamente digitales)? Por ejemplo, al pedir comida en un restaurante. ¿Quién es el cliente y quién el servidor? ¿Qué se pide y qué se entrega? 

Una relación cliente servidor puede ser una consulta medica donde el cliente es el paciente y el servidor es el doctor quuien procesa la información y le entrega un diagnostico al paciente 

### Toma la URL de tu sitio web favorito. Intenta identificar el protocolo, el nombre de dominio y la ruta (si la hay). ¿Qué crees que pasa si solo escribes el nombre de dominio (ej. www.google.com) sin una ruta específica? ¿Qué “página por defecto” crees que te envía el servidor? 

En este caso a voy a usar como ejemplo https://co.pinterest.com/, en este caso el protocolo es https:// el cual es un protocolo que utiliza cifrado seguro , luego el subdominio es co ya que pinterest tiene subdominios para cada pais y en el caso de Colombia es co, el nombre del dominio como tal es pinterest.com y la ruta es / pero como no hay nada despues de eso esa es la raiz del sitio. 
Si solo se escribe del dominio solo te lleva a la pagina principal de pinterest 

### Compara HTTP con los protocolos seriales que usaste. 


### ¿Qué similitudes encuentras? 

Ambos son protocolos de comunicación que establecen un conjunto de reglas claras para que las entidades puedan conectarse y recibir datos, por ello se necesita que ambas partes entiendan el mismo protocolo para que esto funcione sin errores

### ¿Qué diferencias clave ves? 

La seguridad mas que nada, ya que seria si brinda seguridad pero depende de la conexión directa y no tiene casi seguridad, mientras que HTTP puede usar HTTPS para la gestion de errores mas elaborada

### ¿Por qué crees que HTTP necesita ser más complejo que un simple envío de bytes como hacías con el micro:bit?

Porque necesita manejar errores, debe de indicar el tipo de archivo que se esta mandando y tiene que identificar el recurso que se esta pidiendo 

### ¿Qué parte crees que es HTML (ej. los campos de texto, el botón)? 

El HTML son los campos de texto y los botones, es basicamennte lo que define que qelementos existen y en que orden aparecen 

### ¿Qué parte es CSS (ej. el color del botón, el tipo de letra)? 

El CSS es toda la parte visual, desde el color del texto, el tamaño y el tipo de fuente

### ¿Qué parte es JavaScript (ej. la comprobación de si escribiste algo antes de enviar, el mensaje de “contraseña incorrecta” que aparece sin recargar la página)? 

Es toda la interactividad del programa, lo que controla que pasa cuando se escribe en campos de texto y lo que pasa al presionar un boton 

### ¿Qué ventajas crees que tiene el modelo basado en eventos para una interfaz de usuario web? 

Es mucho mas facil de manejar, no consume recursos inecesarios y tiene una mejor experencia de usuario

### ¿Sería eficiente tener un bucle draw() redibujando toda la página 60 veces por segundo si nada ha cambiado? 

De hecho no ya que se deberia de dibujar la pagina unas 60 veces por segundo aun que no haya cambios 

### ¿Por qué crees que podría ser útil usar JavaScript tanto en el cliente (navegador) como en el servidor? ¿Se te ocurre alguna ventaja para los desarrolladores? 

Es muy útil porque permite trabajar con un solo lenguaje en todo el proyecto, es mucho mas rapido y se puyeden reutilizar secciones del codigo 

### Resume con tus propias palabras la diferencia fundamental entre una comunicación HTTP tradicional y una comunicación usando WebSockets/Socket.IO. ¿En qué tipo de aplicaciones has visto o podrías imaginar que se usa esta comunicación en tiempo real? 

La comunicación HTTP tradicional funciona con el modelo de pedido y respuesta ya que el navegador siempre solicita información y el servidor simplemente responde, mientras que con websockets y socket.IO se establece una conexión permanente entre cliente y servidor, que permite que ambos envíen y reciban mensajes en tiempo real sin necesidad de nuevas solicitudes
 
## Actividad 03 

### Cambia la primera ruta de /page1 a /pagina_uno. 

<img width="655" height="131" alt="image" src="https://github.com/user-attachments/assets/1627eb7e-b51c-40df-8d00-ebcb14c56ebd" />

### Intenta acceder a http://localhost:3000/page1. ¿Funciona? 

<img width="1037" height="831" alt="image" src="https://github.com/user-attachments/assets/0aefc47a-c459-428f-9bca-545c31a722d2" />

No funciona, aparece el mensaje "Cannot GET /page1" 

### Ahora intenta acceder a http://localhost:3000/pagina_uno. ¿Funciona?

<img width="1038" height="832" alt="image" src="https://github.com/user-attachments/assets/b3fe721a-56ff-4e70-9a0c-24cc4867c371" />

Si, la pagina funciona con normalidad

### ¿Qué te dice esto sobre cómo el servidor asocia URLs con respuestas? Restaura el código. 

Lo que pasa es que el programa reemplaza la URL por la que se ponga en ese apartado 

### Abre http://localhost:3000/page1 en una pestaña. Observa la terminal del servidor. ¿Qué mensaje ves? Anota el ID.

<img width="745" height="449" alt="image" src="https://github.com/user-attachments/assets/76abf14b-13d5-4b7f-be04-f8ed2ff33653" />

El ID es: Hu7ieEtNQpzIxHz8AAAD 

### Abre http://localhost:3000/page2 en OTRA pestaña. Observa la terminal. ¿Qué mensaje ves? ¿El ID es diferente?

<img width="732" height="138" alt="image" src="https://github.com/user-attachments/assets/b35245ee-dc34-49ad-948b-0ef99e9f952b" />

El ID es: H2wJz2uWl7LktDXlAAAH eso significa que los ID son diferentes 

### Cierra la pestaña de page1. Observa la terminal. ¿Qué mensaje ves? ¿Coincide el ID con el que anotaste? 

<img width="434" height="55" alt="image" src="https://github.com/user-attachments/assets/bdfa180b-4aa2-4248-8f21-258c83c0ed22" />

Al desconectarse el ID no cambia y sigue siendo el mismo que se genero al abrir page1 

### Cierra la pestaña de page2. Observa la terminal. 

<img width="442" height="41" alt="image" src="https://github.com/user-attachments/assets/de52e470-2796-46c9-a4a8-9fd76f213ab7" />

Al iguel que con page1, al cerrar page2 se mantiene el mismo ID que tenia a la hora de crearse 

### Mueve la ventana de page1. Observa la terminal del servidor. ¿Qué evento se registra (win1update o win2update)? ¿Qué datos (Data:) ves? 

<img width="745" height="449" alt="image" src="https://github.com/user-attachments/assets/95318571-a391-43b6-9d38-2a2cf73916e2" />

Al mover page1, se registra el evento win1update con su nuevo ID el cual fue creado al abrir la pagina, los datos que se estan registrando es su posicion en X y Y, el alto y el ancho de la ventana 

### Mueve la ventana de page2. Observa la terminal. ¿Qué evento se registra ahora? ¿Qué datos ves? 

<img width="745" height="449" alt="image" src="https://github.com/user-attachments/assets/f10878ae-c9be-4601-8c7a-f76dcc2cf958" />

Pasa lo mismo que con page1, pero ahora se registra el evento win2update y toma los mismos valores que win1update, pero estos corresponde a la ventana en donde esta page2

### Experimento clave: cambia socket.broadcast.emit(‘getdata’, page1); por socket.emit(‘getdata’, page1); (quitando broadcast). Reinicia el servidor, abre ambas páginas. Mueve page1. ¿Se actualiza la visualización en page2? ¿Por qué sí o por qué no? (Pista: ¿A quién le envía el mensaje socket.emit?). Restaura el código a broadcast.emit. 

<img width="766" height="217" alt="image" src="https://github.com/user-attachments/assets/91d76930-9242-47a7-a878-dca4f0e63522" />

<img width="745" height="449" alt="image" src="https://github.com/user-attachments/assets/f0819982-e968-49d4-b811-64241b52a308" />

https://github.com/user-attachments/assets/7595d9cf-ef4e-4cb7-b083-96ce3252ff8e

Al mover page1 los datos siguen actualizandose de forma normal en la termina y en page2 

### Cambia const port = 3000; a const port = 3001;.

<img width="219" height="28" alt="image" src="https://github.com/user-attachments/assets/05840060-ce8e-4391-af16-9128c206427b" />

### Inicia el servidor. ¿Qué mensaje ves en la consola? ¿En qué puerto dice que está escuchando? 

<img width="742" height="162" alt="image" src="https://github.com/user-attachments/assets/aac90aac-c9d0-4969-a4d1-e052e1466dc9" />

Al cambiar el port a 3001, se esta escuchando el puerto 3001 y aunque se tengan page1 y page2 abiertas, el programa no lo toma hya que ambas estan en 3000

### Intenta abrir http://localhost:3000/page1. ¿Funciona?

<img width="1044" height="837" alt="image" src="https://github.com/user-attachments/assets/0bb92a83-b576-4522-b40e-dca51aabb095" />

No funciona porque se encuentra en port 3000 y se esta escuchando es el por 3001

### Intenta abrir http://localhost:3001/page1. ¿Funciona? 

<img width="1044" height="837" alt="image" src="https://github.com/user-attachments/assets/6e3ac7e2-1c73-48b1-b689-9b37a340dc1c" />

Si funciona y esta esperando a sincronizar datos

### ¿Qué aprendiste sobre la variable port y la función listen? Restaura el puerto a 3000.

## Actividad 04 

### Abre page2.html en tu navegador (con el servidor corriendo). 

<img width="1044" height="839" alt="image" src="https://github.com/user-attachments/assets/bf9065d3-fca7-40f8-a668-e2f3586f6096" />

### Abre la consola de desarrollador (F12). 

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/2bda9f1b-8ab7-460c-b7a0-7d7849764d29" />

### Refresca la página page2.html. Observa la consola del navegador. ¿Ves algún error relacionado con la conexión? ¿Qué indica? 

<img width="1080" height="408" alt="image" src="https://github.com/user-attachments/assets/3d10dde3-89fb-4878-b702-21f33a1f81f0" />

Este error significa que la pagina web se esta intentando conectar al servidor, pero no encuentra nada escuchando en ese puerto 

### Vuelve a iniciar el servidor y refresca la página. ¿Desaparecen los errores? 

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/7ecb09a7-c5ea-4ba6-97ee-7c985e18302b" />

Los errores desaparecen ya que la pagina si se pudo conectar al servidor 

### Comenta la línea socket.emit(‘win2update’, currentPageData, socket.id); dentro del listener connect. 

<img width="952" height="387" alt="image" src="https://github.com/user-attachments/assets/d48a30d2-f3f5-4b22-ad5b-c98ab498cf41" />

### Mueve la ventana de page2 un poco para que envíe una actualización.

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/25aaf17d-f041-40cf-b209-a777fd3cb426" />

### ¿Qué pasó? ¿Por qué? 

Al mover page2 solo se actualiza la posición de esta ventana, pero page1 no actualiza su posición y se queda en la mimsa posición inicial, al menos que page1 se mueva ya que si se manipula esta ventana tanto page1 como page2 se actualizan. Todo esto se debe a que al comentar socket.emit('win2update', currentPageData, socket.id); las actualizaciones de page2 dejan de ser compatibles para page1 por lo que esta no se actualiza segun la posición de page2 y sigue en la misma posición hasta que se mueva 

### Mueve la ventana de page1. Observa la consola del navegador de page2. ¿Qué datos muestra?

<img width="908" height="767" alt="image" src="https://github.com/user-attachments/assets/3f397cc1-d4b3-4ecf-bd2d-0c45d6f175a8" />

Al mover page1 en el consola de page2 se muestran las actualizaciones con su valor en X y Y, el ancho de la ventana y la altura de esta 

### Mueve la ventana de page2. Observa la consola de page1. ¿Qué pasa? ¿Por qué? 

<img width="904" height="766" alt="image" src="https://github.com/user-attachments/assets/429e6e36-6f4b-42d4-ac1e-092467549183" />

Al mover page2 no se muestra ninguna actualización en la consola de page1, esto por que al comentar socket.emit('win2update', currentPageData, socket.id); page1 no recibe actualizaciones de los datos de page2 

### Observa checkWindowPosition() en page2.js y modifica el código del if para comprobar si el código dentreo de este se ejecuta. 

```js
function checkWindowPosition() {
    currentPageData = {
        x: window.screenX,
        y: window.screenY,
        width: window.innerWidth,
        height: window.innerHeight
    };

    if (currentPageData.x !== previousPageData.x || currentPageData.y !== previousPageData.y || 
        currentPageData.width !== previousPageData.width || currentPageData.height !== previousPageData.height) {

        console.log("El if se ejecutó. Datos nuevos detectados:", currentPageData);

        point2 = [currentPageData.width / 2, currentPageData.height / 2]
        socket.emit('win2update', currentPageData, socket.id);
        previousPageData = currentPageData; 
    }
}
```

### Mueve cada ventana y observa las consolas. 

<img width="1913" height="789" alt="image" src="https://github.com/user-attachments/assets/2f2ef934-d600-470d-9200-91e8e138989b" />

### ¿Qué puedes concluir y por qué? 

Como se ve en las imagenes este mensaje solo de muestra en la consola de page2 ya que la modificacion del codigo solo se hace para  checkWindowPosition( de page2 y eso comprueba que el if si se esta ejecutando dentro del programa a la hora de mover page2 

### Cambia el background(220) para que dependa de la distancia entre las ventanas. Puedes calcular la magnitud del resultingVector usando let distancia = resultingVector.mag(); y luego usa map() para convertir esa distancia a un valor de gris o color. background(map(distancia, 0, 1000, 255, 0)); (ajusta el rango 0-1000 según sea necesario). 

```js
function draw() {
    let vector2 = createVector(remotePageData.x, remotePageData.y);
    let vector1 = createVector(currentPageData.x, currentPageData.y);
    let resultingVector = createVector(vector2.x - vector1.x, vector2.y - vector1.y);

    let distancia = resultingVector.mag();

    let fondo = map(distancia, 0, 1000, 255, 0);

    background(fondo);

    if (!isConnected) {
        showStatus('Conectando al servidor...', color(255, 165, 0));
        return;
    }

    if (!hasRemoteData) {
        showStatus('Esperando conexión de la otra ventana...', color(255, 165, 0));
        return;
    }

    if (!isFullySynced) {
        showStatus('Sincronizando datos...', color(255, 165, 0));
        return;
    }

    drawCircle(point2[0], point2[1]);
    checkWindowPosition();

    stroke(50);
    strokeWeight(20);
    drawCircle(resultingVector.x + remotePageData.width / 2, resultingVector.y + remotePageData.height / 2);
    line(point2[0], point2[1], resultingVector.x + remotePageData.width / 2, resultingVector.y + remotePageData.height / 2);
}

```
https://github.com/user-attachments/assets/159c404a-1396-49fa-aed8-436091e70721

### Inventa otra modificación creativa.

```js
function draw() {
    let vector2 = createVector(remotePageData.x, remotePageData.y);
    let vector1 = createVector(currentPageData.x, currentPageData.y);
    let resultingVector = createVector(vector2.x - vector1.x, vector2.y - vector1.y);

    let distancia = resultingVector.mag();

    let fondo = map(distancia, 0, 1000, 255, 0);
    background(fondo);

    if (!isConnected) {
        showStatus('Conectando al servidor...', color(255, 165, 0));
        return;
    }

    if (!hasRemoteData) {
        showStatus('Esperando conexión de la otra ventana...', color(255, 165, 0));
        return;
    }

    if (!isFullySynced) {
        showStatus('Sincronizando datos...', color(255, 165, 0));
        return;
    }

    let diametro = map(distancia, 0, 1000, 200, 50); 
    // Ajusta valores (200 grande cerca, 50 pequeño lejos)

    drawCircle(point2[0], point2[1], diametro);

    checkWindowPosition();

    stroke(50);
    strokeWeight(20);

    drawCircle(
        resultingVector.x + remotePageData.width / 2,
        resultingVector.y + remotePageData.height / 2,
        diametro
    );
    line(
        point2[0], point2[1],
        resultingVector.x + remotePageData.width / 2,
        resultingVector.y + remotePageData.height / 2
    );
}

function drawCircle(x, y, d) {
    fill(255, 0, 0);
    ellipse(x, y, d, d);
}

```
https://github.com/user-attachments/assets/f388d1ec-082d-467a-b45b-87e7bfc2dd40

Hice una modificiación al codigo para que entre mas lejos estuviesen una pagina de la otra el tramaño del circulo iba creciendo o decreciendo segun esta distancia

## Actividad 05

### Explica tu idea y realiza algunos bocetos. 

Mi idea era hacer dos paginas donde ambas tenian emojis y simulaban una conversación ya que al presionar los emojis de page1 deberian de aparecen en page2 en tiempo real y lo mismo con los emojis de page2 en page1

### Proceso 

En realidad tuve bastantes problemas a la hora de crear el codigo ya que muchas veces o las paginas o cargaban o no interactuan unas con otras, por ejemplo aqui que aunque se presionen los emojis estos no se mostraban en tiempo real en la otra pagina 

<img width="1843" height="959" alt="image" src="https://github.com/user-attachments/assets/0c6a5cb0-815a-442b-bbde-a5e1fd9d701e" />

Cuando logre que el codigo funcionara agregando page1.js y page2.js a public en vez de view se veia algo asi 

<img width="1838" height="918" alt="image" src="https://github.com/user-attachments/assets/29b92b25-1e73-45ae-99f3-d8b7426f84c2" />

Ya luego cambie la parte visual y se ve de esta forma del programa

<img width="1916" height="953" alt="image" src="https://github.com/user-attachments/assets/31ba5a80-d02b-489d-9d3a-18448a9889df" />

### Codigo 

package.json

```js
{
  "name": "emoji-chat",
  "version": "1.0.0",
  "description": "Chat visual con emojis usando Socket.IO",
  "main": "server.js",
  "scripts": {
    "start": "node server.js"
  },
  "dependencies": {
    "express": "^4.18.2",
    "socket.io": "^4.7.2"
  }
}
```

server.js

```js
const express = require('express');
const http = require('http');
const { Server } = require('socket.io');
const path = require('path');

const app = express();
const server = http.createServer(app);
const io = new Server(server);

app.use(express.static(path.join(__dirname, 'public')));

app.get('/page1.html', (req, res) => {
  res.sendFile(path.join(__dirname, 'views', 'page1.html'));
});

app.get('/page2.html', (req, res) => {
  res.sendFile(path.join(__dirname, 'views', 'page2.html'));
});

io.on('connection', (socket) => {
  console.log('Usuario conectado:', socket.id);

  socket.on('sendEmoji', (data) => {
    console.log(`Emoji recibido: ${data.emoji} desde ${data.sender}`);
    io.emit('newEmoji', data);
  });

  socket.on('disconnect', () => {
    console.log('Usuario desconectado:', socket.id);
  });
});

const PORT = 3000;
server.listen(PORT, () => {
  console.log(`Servidor corriendo en http://localhost:${PORT}`);
});
```

page1.html 

```js
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Page 1 - Emoji Chat</title>
  <style>
    body { font-family: Arial, sans-serif; display: flex; flex-direction: column; align-items: center; background: #f7f7f7; margin: 0; padding: 20px; }
    h2 { margin-bottom: 15px; }

    #emojiContainer {
      border: 1px solid #ccc;
      background: #fff;
      width: 80%;
      height: 350px;
      overflow-y: auto;
      margin-top: 20px;
      padding: 15px;
      display: flex;
      flex-direction: column;
      border-radius: 12px;
      box-shadow: 0px 3px 8px rgba(0,0,0,0.15);
    }

    .emoji-btn {
      font-size: 2rem;
      cursor: pointer;
      margin: 5px;
      padding: 5px 10px;
      border-radius: 8px;
      border: 1px solid #ddd;
      background: #fafafa;
      transition: background 0.2s;
    }
    .emoji-btn:hover { background: #eee; }

    .bubble {
      display: inline-block;
      padding: 10px 15px;
      border-radius: 20px;
      margin: 5px 0;
      max-width: 70px;
      text-align: center;
      font-size: 2rem;
      word-wrap: break-word;
    }
    .left { background: #e1f5fe; align-self: flex-start; }
    .right { background: #c8e6c9; align-self: flex-end; }
  </style>
</head>
<body>
  <h2>Page 1</h2>
  <div>
    <span class="emoji-btn">😀</span>
    <span class="emoji-btn">😂</span>
    <span class="emoji-btn">😍</span>
    <span class="emoji-btn">😎</span>
    <span class="emoji-btn">👍</span>
  </div>
  <div id="emojiContainer"></div>

  <script src="/socket.io.js"></script>
  <script src="page1.js"></script>
</body>
</html>
```

page2.html 
```js
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Page 2 - Emoji Chat</title>
  <style>
    body { font-family: Arial, sans-serif; display: flex; flex-direction: column; align-items: center; background: #f7f7f7; margin: 0; padding: 20px; }
    h2 { margin-bottom: 15px; }

    #emojiContainer {
      border: 1px solid #ccc;
      background: #fff;
      width: 80%;
      height: 350px;
      overflow-y: auto;
      margin-top: 20px;
      padding: 15px;
      display: flex;
      flex-direction: column;
      border-radius: 12px;
      box-shadow: 0px 3px 8px rgba(0,0,0,0.15);
    }

    .emoji-btn {
      font-size: 2rem;
      cursor: pointer;
      margin: 5px;
      padding: 5px 10px;
      border-radius: 8px;
      border: 1px solid #ddd;
      background: #fafafa;
      transition: background 0.2s;
    }
    .emoji-btn:hover { background: #eee; }

    .bubble {
      display: inline-block;
      padding: 10px 15px;
      border-radius: 20px;
      margin: 5px 0;
      max-width: 70px;
      text-align: center;
      font-size: 2rem;
      word-wrap: break-word;
    }
    .left { background: #e1f5fe; align-self: flex-start; }
    .right { background: #c8e6c9; align-self: flex-end; }
  </style>
</head>
<body>
  <h2>Page 2</h2>
  <div>
    <span class="emoji-btn">🔥</span>
    <span class="emoji-btn">🥳</span>
    <span class="emoji-btn">💡</span>
    <span class="emoji-btn">🎉</span>
    <span class="emoji-btn">💀</span>
  </div>
  <div id="emojiContainer"></div>

  <script src="/socket.io.js"></script>
  <script src="page2.js"></script>
</body>
</html>
```

page1.js 

```js
const socket = io();

const emojiContainer = document.getElementById('emojiContainer');
const emojiButtons = document.querySelectorAll('.emoji-btn');

emojiButtons.forEach(btn => {
  btn.addEventListener('click', () => {
    const emoji = btn.textContent;
    socket.emit('sendEmoji', { emoji, sender: 'page1' });
  });
});

socket.on('newEmoji', (data) => {
  const div = document.createElement('div');
  div.textContent = data.emoji;
  div.classList.add('bubble');

  if (data.sender === 'page1') {
    div.classList.add('right');
  } else {
    div.classList.add('left');
  }

  emojiContainer.appendChild(div);
  emojiContainer.scrollTop = emojiContainer.scrollHeight;
});
```

page2.js 

```js
const socket = io();

const emojiContainer = document.getElementById('emojiContainer');
const emojiButtons = document.querySelectorAll('.emoji-btn');

emojiButtons.forEach(btn => {
  btn.addEventListener('click', () => {
    const emoji = btn.textContent;
    socket.emit('sendEmoji', { emoji, sender: 'page2' });
  });
});

socket.on('newEmoji', (data) => {
  const div = document.createElement('div');
  div.textContent = data.emoji;
  div.classList.add('bubble');

  if (data.sender === 'page2') {
    div.classList.add('right');
  } else {
    div.classList.add('left');
  }

  emojiContainer.appendChild(div);
  emojiContainer.scrollTop = emojiContainer.scrollHeight;
});
```

### Video demostrativo 

https://github.com/user-attachments/assets/3887e925-98d0-4522-b31b-82bff708355a

### Autoevaluación 

Creo que en este caso mi auto evalución es de 4.6 ya que a pesar de haber hecho todas las actividades y haber comprendido los conceptos de la unidad, a la hora de ponerlo en practica tuve unos cuantos problemas con el codigo del page1.html, page2.hmtl, page1.js y page2.js los que me complicaron la solución del problema y tuve que recurri a mas investigación para poder solucionar el conflicto y hacer que el programa funcionara correctamente, ademas siento que algunos de los conceptos aprendidos me son claros pero no sabria ponerlos en practica sin algun ejemplo previo, lo que creo que le resta a la nota final ya que la idea es saber todos los conceptos y poderlos aplicar si es necesario



