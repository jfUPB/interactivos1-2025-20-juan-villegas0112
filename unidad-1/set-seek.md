# Unidad 1

## 🔎 Fase: Set + Seek

### Actividad 01

Luego de ver juntos los videos y conversar sobre ellos, define en tus propias palabras

¿Qué es un sistema físico interactivo?
Un sistema interactivo es un generador de experiencias que necesita de un input y un autput, haciendo que el sitema necesite de una accion de entrada para generar una accion de salida. Por ejemplo, generar una imagen atraves de la generacion de un sonido.

¿Cómo podrías aplicar lo que has visto en tu perfil profesional?
Entendiendo bien como funciona la interacion usuario objeto, para saber que experiencia es mas adecuada para cada espacio, contexto y/o publico objetivo.

### Actividad 02

Luego de este ejercicio, define en tus propias palabras

¿Qué es el diseño/arte generativo?
Arte generado en tiempo real, con la utilizacion de un sistema que cumple u conjunto de reglas creadas por un artista. Esta practica contien un cierto nivel de eleatoriedad. Aunuqe el arte generativo tiene un fin y el diseño generativo pretende mostrar algo en especifico, ambas contienen casi la misma estructura.  
¿Cómo podrías aplicar lo que has visto en tu perfil profesional?
Me intera mucho la generacion de imagenes para conciertos, pues le permite vivir una experiecia unica al usuario que este viviendo el concierto o la exposicion artistica en la que se encuentre. Ademas la posibilidad de creacion de diseños para cualquier tipo de actividades y que sean no solo imagenes sino experiencias que pueden a llegar a ser unicas para cada usuario es algo que es demasiado innovador e importante para la creacion de productos y espacios interactivos.

### Actividad 03

#### Inputs:

- Botón A del microbit

- Botón B del microbit

- Sensor de movimiento del micro:bit

- Botón “Send Love” en la interfaz de p5.js

#### Outputs:

- Cambio de imagen en el LED del microbit:

- Se muestra una mariposa al iniciar.

- Se muestra un corazón y luego una cara feliz cuando se recibe el send love.

- Cambio de color del círculo en la interfaz de p5.js:

- Rojo si se presiona el botón A.

- Amarillo si se presiona el botón B.

- Verde si se detecta movimiento.

#### Proceso

##### En el microbit:

- Detecta cuándo se presionan los botones o se sacude el dispositivo.

- Envía los caracteres 'A', 'B' o 'C' a través de UART (comunicación serial).

- Recibe datos desde p5.js; si recibe 'h', muestra el corazón y la carita feliz.

##### En p5.js:

- Espera datos del micro:bit y los interpreta para cambiar el color del círculo.

- Tiene un botón que, al hacer clic, envía el carácter 'h' al micro:bit para activar una respuesta visual en él.

### Actividad 04

<img width="599" height="598" alt="image" src="https://github.com/user-attachments/assets/70324bee-a4c2-4a5a-9058-3f3d73c38b7e" />

```javascript

function setup() {
  createCanvas(600, 600);
  noStroke();
  frameRate(10); // reduce velocidad para apreciar los cambios
}

function draw() {
  background(20, 20, 30, 50); // fondo con leve transparencia

  for (let i = 0; i < 100; i++) {
    let x = width / 2 + sin(frameCount * 0.02 + i) * random(50, 250);
    let y = height / 2 + cos(frameCount * 0.02 + i) * random(50, 250);
    let r = random(5, 20);
    
    fill(random(100, 255), random(100, 255), random(100, 255), 150);
    ellipse(x, y, r, r);
  }
}
```


