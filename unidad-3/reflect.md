# Unidad 3


## 🤔 Fase: Reflect

### Actividad 08 

### Parte 2: reflexión sobre tu proceso (Metacognición)

1. Describe con tus palabras qué es una máquina de estados. ¿Cuáles son sus cuatro componentes fundamentales que has utilizado en esta unidad?

Como tal una maquina de estados es un sistema que depende de diferentes eventos, estados y acciones para que ell programa funcione correctamente, esto permite que el programa pueda volver a usar estos eventos sin neceisdad de vovlerlos a instanciar lo que es muy conveniente para ciertos codigos donde se necesitan que ocurran eventos consecutivos o que se necesite volver a uno de estos de forma rapida o a partir de alguna acción

2. Explica por qué la técnica de máquina de estados es tan útil para gestionar la “concurrencia” (atender varios eventos y tareas “al mismo tiempo”) en un dispositivo con un solo hilo de ejecución como el micro:bit o en p5.js. ¿Qué problema soluciona en comparación con usar funciones como sleep()?

Como tal la tecnica de estados sirve para que el programa no se pierda de eventos importantes, ya que si se usa sleep es probable que el sistema se quede dormido e ignore o no este despierto para un evento o acción importante

3. Imagina que tienes que añadir una nueva funcionalidad a la bomba: si se recibe un evento especial (por ejemplo, una combinación de botones o un comando serial) mientras la cuenta regresiva está activa, el tiempo se reduce a la mitad. ¿Cómo modificarías tu diagrama de máquina de estados para incluir este nuevo evento y acción?

Esta acción estaria en STATE_ARMED ya que esta puede hacer que la bomba explote mucho mas rapido si se utiliza, podria ser presionando una serie de botones o alguna combinanción de movimientos con el acelerometro y cuandoel microbit los detecte haga que el tiempo se reduzca a la mitad

4. Explica qué es un “vector de prueba” y por qué es una herramienta crucial para verificar que una máquina de estados funciona como se espera.

Los vectores de prueba tienen la función de probar ciertas partes del codigo en circustancias o fierentes a lss predeterminadas,esto con el fin de comprar que el codigo siga funcionando a pesar de diferentes factores a la hora de correr el programa

### Parte 2: reflexión sobre tu proceso (Metacognición) 

1. ¿Qué parte del diseño de la bomba te resultó más desafiante: crear el diagrama de estados o traducir ese diagrama a código? ¿Por qué?

En mi caso es el traducir el diagrama al codigo, a pesar de estar en la unidad 3 aun se me complica un poco ya que sigo sin saber por donde iniciar y que evento debo de crear primero para guiarme con el y seguir el codgo, tambien se me dificuta el saber que tipo de acciones debo de agregar a cada evento para que este funcione correctamente

2. Describe un error o “bug” que encontraste al implementar tu programa. ¿Cómo te ayudó pensar en términos de estados, eventos y transiciones a identificar y solucionar el problema?

En la actividad 6 tuve un bug con el contador ya que muchas veces los botones A y B hacian la misma acción o no sumaban o restaran al contador, el error como tal era dentro del contador donde no tenia el funcionamiento de quee si se presionaba alguno de los 2 botones se debia de restar o sumar un numero al contador

3. El problema de la bomba era complejo. ¿Qué estrategia usaste para abordarlo? ¿Comenzaste con una versión simple y añadiste funcionalidades poco a poco?

Para la bomba 3.0 me guie de algunos diagranmas que ya habia hecho antes e itente deglozar cada evento individuamente para entender que acción podria llevar a otro evento para asi lograr estructurar el diagrama y comprender el funcionamiento de la bomba

4. Ahora que entiendes el patrón de máquina de estados, ¿En qué otro tipo de proyecto o sistema de entretenimiento digital crees que podrías aplicarlo?

Como dije en la unidad pasada, sigo sosteniendo la idea de un juego virtual como tamagochi, pero creo que tambien puede servir para sistemas de seguridad o juegos de puzzles ya que al implementar contraseñas y cosas asi este tipo de programas se pueden hacer posibles

### Actividad 09 

1. Continuar: ¿Qué actividad, explicación o ejemplo de esta unidad te ayudó más a entender el poder de las máquinas de estados? ¿Qué elemento consideras que es indispensable y debería mantener?

Para mi lo mas dificil fueron las actividades 6 y 7 donde se tenia que implementar la maquina de estados en p5.js y luego crear un "controlador" en microbit para la bomba dentro de p5.js, en este caso tuve que pedirle ayuda a conocidos y generar algunas partes del codigo (pero solo lo hice para tener una base de como implementar una maquina de estados en p5.js para ya luego guiarme con ella y hacer mi propio codigo de al bomba) ya luego con el microbit tuve que buscar un poco de información y pedirle ayuda a mis primos quienes son programadores para comprobar el funcionamiento del microbit, al principio tuvimos errores, pero al final se logro probar, no de la forma mas eficiente, pero si funconaba luego de unos cuentos intentos 

2. Dejar de hacer: ¿Hubo algún paso o actividad que te pareció confuso? ¿Qué cambiarías o eliminarías?

En general fueron las actividades 6 y 7 ya que coom tuve que investigar como implementar la maquina de estados en p5.js y  me hubiese gustado que el profesor nos diera una explicación basica de que se necesitaba para crear la maquina de estados en este programa, por ejemplo como servian las funciones en estos casos y las demas acciones dentro de los eventos

3. Empezar a hacer: ¿Qué te habría ayudado a entender mejor?

En este caso creo que me hubiese ayudado mas hacer codigos tanto en p5.js como en microbit para que las ultimas 2 actividades no fueran complicadas y hubiesen sido mas faciles de hacer

4. Ritmo y dificultad: En una escala del 1 (muy fácil) al 5 (muy difícil), ¿Cómo calificarías la dificultad de pasar del análisis de un programa a diseñar y programar uno complejo? ¿Por qué?

Yo calificaria con un 4.5 la dificultad en general de la actividad, ya que me toco investigar y dedicar mucho mas tiempo al realizar las actividades y lograr comprender su funcionamiento a fondo, lo que no he tenido que hacer en las demas unidades ya que se me habian hecho mucho mas facil de realizar

5. Comentario adicional: ¿Hay algo más que te gustaría compartir sobre tu proceso de aprendizaje en esta unidad? ¿Algún momento de frustración o de “¡Aha!” que quieras destacar?

Fue al ver la actividad 02 ya que no sabia de que forma se podria crear una contraseña en un programa, por lo que al ver el codigo logre enetender luego de unas cuentas revisadas que no era tan complicado como lo pensaba y que de hecho era mucho mas logico hacerlo de esta manera que de la forma que lo estaba intentando plantear


