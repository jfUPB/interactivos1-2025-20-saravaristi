# Unidad 1

## 🔎 Fase: Set + Seek

### Actividad 01

¿Que es un sistema fisico interactivo?  

A mi parecer es la combinacion entre elementos virtuales y elementos fisicos donde a partir de inputs, procesamiento y outputs se logran hacer visuales, proyectos o experencias donde el usuario es quien interactua con ellas. 

¿Como podrias aplicar lo que has visto en tu perfil profesional?  

Como tal yo tengo interes en todo lo que son visuales ya sean para conciertos, videos musicales o videojuegos por lo que creo que seria una nueva forma de implementarlos en mis trabajos y una tecnica que no mucha gente trabaja lo que lo hace unico.  

### Actividad 02

¿Que es el diseño/arte generativo? 

Es cuando se utiliza programacion y otro tipo de herramientas en un sistema autonomo para definir reglas con el objetivo de realizar una pieza de arte que dependa de estas instrucciones, al tener tanta libertad sobre lo que se quiere realizar, el artista puede generar ya sean paletas de colores, formas geometricas y darle la opcion de decidir al programa para generar el diseño deseado.

¿Como podrias aplicar lo que has visto en tu perfil profesional? 

Me gustaria aplicarlo en creacion de marcas o de logos ya que si se hace de la forma correcta el logo diseñado va a tener su identidad propia y es probable que nunca sea igual en cada uno de los elementos en los que se utilize lo que lo hace muy innovador ya que se puede jugar con diferentes parametros dependiendo de lo que se quiere representar.

### Actividad 03 

inputs: en este caso son los botones y el acelerometro que tiene la microbit. ademas del serial por el que se interactua al presionar send love. 

outputs: las formas que se generan en los leds y en la pagina al interactuar con los botones y el acelerometro. 

procesos: es el programa que procesa los inputs y las instrucciones que se escriben en los editores. 

### Actividad 04 

[Enlace a mi programa en la web](https://editor.p5js.org/saravaristi/sketches/S5ur-IYdk)

```
function setup() {
  createCanvas(400, 400);
}

function draw() {
  background (5,5);
  stroke(paletteLerp([
    ['purple', 0],
    ['pink', 0.25],
    ['cyan', 0.45],
    ['violet', 0.60],
    ['orange',0.75],
    ['magenta', 1]
  ], millis() / 10000 % 10));
   fill(paletteLerp([
    ['purple', 0],
    ['pink', 0.25],
    ['cyan', 0.45],
    ['violet', 0.60],
    ['orange',0.75],
    ['magenta', 1]
  ], millis() / 10000 % 10));
 
  
  circle (mouseX,mouseY,random(5,20));
   
}
```
<img width="1351" height="899" alt="image" src="https://github.com/user-attachments/assets/af245650-bbdc-40eb-b4d0-4b3ca5c2a80e" />

