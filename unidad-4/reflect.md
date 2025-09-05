# Unidad 4


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
