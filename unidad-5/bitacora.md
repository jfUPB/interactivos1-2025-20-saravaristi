
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

### 2. Captura el resultado del experimento anterior. Lo que ves ¿Cómo está relacionado con esta línea de código? 

### 3. ¿Qué ventajas y desventajas ves en usar un formato binario en lugar de texto en ASCII? 

### 4. Captura el resultado del experimento. ¿Cuántos bytes se están enviando por mensaje? ¿Cómo se relaciona esto con el formato '>2h2B'? ¿Qué significa cada uno de los bytes que se envían? 

### 5. Recuerda de la unidad anterior que es posible enviar números positivos y negativos para los valores de xValue y yValue. ¿Cómo se verían esos números en el formato '>2h2B'? 

### 6. 





