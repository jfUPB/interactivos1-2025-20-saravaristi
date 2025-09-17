
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

### 3. Analiza el código, observa los cambios. Ejecuta y luego observa la consola. ¿Qué ves? 

<img width="796" height="81" alt="image" src="https://github.com/user-attachments/assets/eb9dcca3-669f-4920-b562-24d0698b391d" />

### 4. ¿Qué cambios tienen los programas y ¿Qué puedes observar en la consola del editor de p5.js? 

En este caso la consola funciona de forma normal, sin errores 

## Actividad 04 
















