
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

Si funciono, pero habia un poco de daley en el computador al mover el circulo con el touch del telefono de forma rapida, veo que no detecta un solo toque en la pantalla, es decir que si o si debo de hacer el gesto de mover el dedo para que el circulo cambie de posición

## Actividad 02 

### Explica con tus propias palabras: ¿Por qué es necesario Dev Tunnels en este escenario y cómo funciona conceptualmente? 

Como tal Dev Tunnels funciona como un intermedirario entre el localhost y la URL creada donde al conectarse a la URL se reenvia la conexción hasta el localhost y cuando hay interacciones las respuestas viajan desde el servidor a la URL

### Describe la función de touchMoved() y por qué se usa la variable threshold en el cliente móvil. 

touchMoved() sirve para detectar el movimiento de el dedo en la pantalla ya que tiene los valores mouseX y mouseY, en el caso de threshold funciona de forma en que no se envia cualquier pequeño movimiento del dedo sobre la pantalla, se encarga de solo enviar los movimientos significativos, esto con el objetivo de evitar inundad la red de mensajes

### Compara brevemente Dev Tunnels con simplemente usar la IP local. ¿Cuáles son las ventajas y desventajas de cada uno?  {

Al usar Dev Tunnel no necesitamos depender de que ambos dispositivos esten en la misma red, mientras que con la IP local si se depende de esto y de que no hayan firewalls bolqueadas por lo que si se abre el localhost desde el celular se estaria buscando un servidor enn el celular pero no el que esta ya en el computador

### Coloca en tu bitácora capturas de pantalla del sistema completo funcionando. Esto lo puedes hacer abriendo tanto el mobile como el desktop en tu computador y tomando una captura de pantalla de todos los involucrados (celular, computador y terminal).  

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/5676a8b3-f3bb-462f-8fb4-45702d9f704e" />

https://github.com/user-attachments/assets/f84e6e63-40c0-471b-8dcb-570ceae432b1

## Actividad 03 

### ¿Cuál es la función principal de express.static(‘public’) en este servidor? ¿Cómo se compara con el uso de app.get(‘/ruta’, …) del servidor de la Unidad 6?

express.static(‘public’) convierte la carpeta public en la raiz del servidor osea que en vez de tener un index.html lo que se tiene es un localhost al que solo se le debe de poner la ruta a la pagina especifica como /desktop/, mientras que app.get(‘/ruta’, …) lo que hace es responder manualmente a la ruta agregando un index.html

### Explica detalladamente el flujo de un mensaje táctil: ¿Qué evento lo envía desde el móvil? ¿Qué evento lo recibe el servidor? ¿Qué hace el servidor con él? ¿Qué evento lo envía el servidor al escritorio? ¿Por qué se usa socket.broadcast.emit en lugar de io.emit o socket.emit en este caso? 

Primero los eventos wue envian desde el movil es touchstart, touchmove y touchend, el evento que lo recibe en el servidor es socket.on('message', (message) donde lo valida

### Si conectaras dos computadores de escritorio y un móvil a este servidor, y movieras el dedo en el móvil, ¿Quién recibiría el mensaje retransmitido por el servidor? ¿Por qué? 



### ¿Qué información útil te proporcionan los mensajes console.log en el servidor durante la ejecución? 



## Actividad 04 

### Realiza un diagrama donde muestres el flujo completo de datos y eventos entre los tres componentes: móvil, servidor y escritorio. Puedes ilustrar con un ejemplo de coordenadas táctiles (x, y) y cómo viajan a través del sistema.
