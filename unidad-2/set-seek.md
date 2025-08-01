# Unidad 2

## 🔎 Fase: Set + Seek

### Actividad 01 

1. Describe detalladamente cómo funciona este ejemplo.

El codigo funciona de forma que se tienen 2 pixeles que parpadean cada uno con un tienmpo respectivo y diferente el uno del otro, se tienen dos estados los cuales son "Init" y "WaitTimeOut" donde Init funciona de forma que guarda el tiempo de inicio y confiigura los valores de los pixeles, mientras que WaitTimeOut se eencarga de verificar que el tiempo estipulado para cada pixel pase para hacer que cada pixel brille, cuando esto se cumple todo el proceso se repite. En este caso el evento es "Interval" y hay varias acciones dentro del programa que ayudan a que cada estado sea completado

2. ¿Cuáles son los estados en el programa?

En este caso los estados son una condición de espera, por lo que el codigo hay 2 estados los cuales son "Init" y "WaitTimeOut" 

3. ¿Cuáles son los eventos/inputs en el programa?

Los eventos es cuando el programa esta esperando que se cumplan un conjuntos de acciones como si fuese una lista de cosas que hacer

4. ¿Cuáles son las acciones en el programa?

Hay algunas como actualizar variables, leer tiempo, alternaltar el estado de los pixeles entre prendido y apagado, calcular cuanto tiempo ha pasado desde la ultima actualización de cada pixel, calcular el tiempo restante para cada pixel 

### Actividad 02 


### Actividad 03 

1. Explica por qué decimos que este programa permite realizar de manera concurrente varias tareas.

El programa si permmite realizar varias tareas a la vez ya que se tiene 3 caritas que se van cambiado segun el tiempo que tenga cada una, ademas de poder cambiar las caras manualmente usando el boton A

2. Identifica los estados, eventos y acciones en el programa.

3. Describe y aplica al menos 3 vectores de prueba para el programa. Para definir un vector de prueba debes llevar al sistema a un estado, generar los eventos y observar el estado siguiente y las acciones que ocurrirán. Por tanto, un vector de prueba tiene unas condiciones iniciales del sistema, unos resultados esperados y los resultados realmente obtenidos. Si el resultado obtenido es igual al esperado entonces el sistema pasó el vector de prueba, de lo contrario el sistema puede tener un error.

   
