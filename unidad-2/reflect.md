# Unidad 2

## 🤔 Fase: Reflect 

### Actividad 06 

### Parte 1: recuperación de conocimiento (Retrieval Practice) 

1. Describe con tus palabras qué es una máquina de estados. ¿Cuáles son sus cuatro componentes fundamentales que has utilizado en esta unidad?

Una maquina de estados es un sistema que esta compuesto por eventos, estados, acciones y transciciones las cuales funcionan conjuntamente ya que todas dependen una de la otra para hacer que el programa funcione como tal.

2. Explica por qué la técnica de máquina de estados es tan útil para gestionar la “concurrencia” (atender un temporizador y botones “al mismo tiempo”) en un dispositivo con un solo hilo de ejecución como el micro:bit. ¿Qué problema soluciona en comparación con usar funciones como sleep()?



3. Imagina que tienes que añadir una nueva funcionalidad a la bomba temporizada: si se agita (shake) el micro:bit mientras la cuenta regresiva está activa, el tiempo se reduce a la mitad. ¿Cómo modificarías tu diagrama de máquina de estados para incluir este nuevo evento y acción?

Agregaria etsa funcionalidad en STATE_ARMED ya que en este estado la bomba ya esta armada y lo que hace esta función es reducir a la mitad el tiempo estimado por el usuario y por lo que la bomba explotaria mucho mas rapido de lo especificado, dentro del diagrama esto en realidad no cambia los demas estados y funciones ya que solo es agregar una función que de todas hara que la bomba explote sin interferir en los demas estados 

4. Explica qué es un “vector de prueba” y por qué es una herramienta crucial para verificar que una máquina de estados funciona como se espera.

Un vector de prueba tiene la función de corroborar que un estado o acción este funcionando correctamente bajo distintas condiciones a las especificadas inicialmente, es decir que cumpa su función predeterminada pero ademas que se cumpla otra condición dada justamente por este vector de prueba, esto con el objetivo de que el sistema funcione bajo diversas condiciones y usos

### Parte 2: reflexión sobre tu proceso (Metacognición) 

1. ¿Qué parte del diseño de la bomba temporizada te resultó más desafiante: crear el diagrama de estados (Actividad 04) o traducir ese diagrama a código MicroPython (Actividad 05)? ¿Por qué?

En mi caso lo que mas se me complico fue el diagrama ya que no sabia de que forma organizar los eventos y estados de forma que tuviese logica, como ya habia hecho codigos similares durante toda esta unidad ya tenia conocimiento de como inicializar las cosas y guiarme por el enunciado para generar un codigo funcional y optimizarlo para que fuese lo mas fluido posible

2. Describe un error o “bug” que encontraste al implementar tu programa. ¿Cómo te ayudó pensar en términos de estados, eventos y transiciones a identificar y solucionar el problema?

Uno de los bug o errores mas frecuentes que encontre a la hora de crear el codigo fue a la hora de gestionar el STATE_CONFIG ya que no se guardaban los valores dados por el usuario a la bomba y a la hora de implementar STATE_ARMED la bomba no guardaba los datos que se habian dado en STATE_CONFIG lo que me hizo buscar una solución al problema que al final era un error al implementar el STATE_CONFIG. En general tuve que investigar un poco para comprender que habia hecho mas dentro del programa lo que me hizo comprender un poco mas los temas tratados en esta unidad y su importancia dentrod e un programa para crear sistemas mas complejos y organizados en un futuro

3. El problema de la bomba era complejo. ¿Qué estrategia usaste para abordarlo? ¿Comenzaste con una versión simple y añadiste funcionalidades poco a poco?

Para hacer el codigo lo intente hacer la forma mas logica y simple posible para ya luego ir implementando las acciones mas dificiles de comprender y ver si funcionabban correctamente, a medida que iba agregando mas cosas se hacia mas complicado pero al verificar cada cosa una por una e investigar su funcionamiento eventualmente fue mas facil implementar estados y acciones

4. Ahora que entiendes el patrón de máquina de estados, ¿En qué otro tipo de proyecto o sistema de entretenimiento digital crees que podrías aplicarlo?

### Actividad 07 

### Actividad 08 

1. Continuar: ¿Qué actividad, explicación o ejemplo de esta unidad te ayudó más a entender el poder de las máquinas de estados? ¿Qué elemento consideras que es indispensable y debería mantener?

El ejemplo que mas me ayudo fue el de las expresiones ya que ahi logre comprender en realidad como funcionaban los eventos, estados y acciones y porque era importante que cada parte funcionara bien para no afectar a las demas y por ello al sistema como tal

2. Dejar de hacer: ¿Hubo algún paso o actividad que te pareció confuso, innecesariamente complicado o que aportó poco a tu aprendizaje? ¿Qué cambiarías o eliminarías?

La explicación inicial con la galleta me confumdio mas que ayudarme a comprender los conceptos iniciales de la unidad ya que al combinar un concepto tan claro como lo es una galleta con algunos concpetos de programación orientada a objetos hizo que la verdad no comprendiera y me confundiera con los conceptos, pero esto en parte creo que se debe a que en general no recordaba bien los conceptos de POO que se explicaron esa vez por lo que siento aque en base fue eso lo que me hizo confundir. Sin embargo creo que hubiese sido mas facil recordar directamente los conceptos de POO antes de explicar los conceptos base de la unidad para evitar confusiones

3. Empezar a hacer: ¿Qué te habría ayudado a entender mejor?

Creo que depronto algun video explicativo en clase sobre los concpetos mas iniciales, o almenos tenerlo como recurso dentro la unidad

4. Ritmo y dificultad: En una escala del 1 (muy fácil) al 5 (muy difícil), ¿Cómo calificarías la dificultad de pasar del análisis de un programa (Actividad 03) al diseño desde cero de uno complejo (Actividad 04 y 05)? ¿Por qué?

Creo que calificaria con un 4 la dificultad de pasar del analisis ya que al inicio de la unidad si se me complicaba crear los codigos ya que no sabia como podia iniciar y tampoco como estructurar correctamente los estados y las acciones dentro de estos. Ya luego con el diseño desde cero de uno complejo le daria un 3 ya que a pesar de ya estas mas familiarizada con el codigo no lo estaba con el diagrama y esto complico las cosas en ese momemnto

5. Comentario adicional: ¿Hay algo más que te gustaría compartir sobre tu proceso de aprendizaje en esta unidad? ¿Algún momento de frustración o de “¡Aha!” que quieras destacar?

Creo que como tal en toda la unidad tuve momentos de frustación pero tambien de descubrimientos y de satisfacción al lograr las actividades planteadas sin necesidad de investigar por fuera de los recursos dados, lo que mas resaltaria es la importancia de la practica ya que esta te ayuda demasiado a comprender temas y alcanzar metas a corto plazo que en este caso seria cada actividad de la unidad

