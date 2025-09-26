
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


