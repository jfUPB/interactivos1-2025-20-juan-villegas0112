
# Evidencias de la unidad 5

## Actividad 01

👽 Describe cómo se están comunicando el micro:bit y el sketch de p5.js. ¿Qué datos envía el micro:bit?

El micro bit esta envianado datos que van dirigidos a la utilizacion de los botones y el acelerometro, estos llegan codigo en p5js con valores como 1 o 0 y true o false, haciendo que la comunicacion se limite a si esta presionado o no el boton, tambien le da un valor a las coordenadas iniciaes del acelerometro permitiendo que cuando se haga el gesto o la rotacion del microbit haya un cambio en el valor.

👽 ¿Cómo es la estructura del protocolo ASCII usado?
desde el micro:bit  se envian estos datos 
```-200,1300,true,false\n``` 

👽 Muestra y explica la parte del código de p5.js donde lee los datos del micro:bit y los transforma en coordenadas de la pantalla.
```js
        let values = data.split(",");
        if (values.length == 4) {
          microBitX = int(values[0]) + windowWidth / 2;
          microBitY = int(values[1]) + windowHeight / 2;
        } 
```
como el microbit envia un rango de posicion de 1024 a -1024, en el codigo de p5 se hace la conversion haciendo que se les suma la mitad del ancho/alto de la pantalla para centrarlos:

0 ----> Centro de la pantalla

-300 ----> A la izquierda / arriba del centro

+300 ----> A la derecha / abajo del centro


👽 ¿Cómo se generan los eventos A pressed y B released que se generan en p5.js a partir de los datos que envía el micro:bit?

Al microbit enviar los estados de los botones como booleados, es decir true o false, hace que el proceso funcione asi:

Si el botón A pasa de no presionado(true) a presionado(false) → se interpreta como "A pressed"

Si el botón B pasa de presionado(true) a no presionado(false) → se interpreta como "B released"

👽 Capturas de pantalla de los algunos dibujos que hayas hecho con el sketch.

<img width="1589" height="806" alt="image" src="https://github.com/user-attachments/assets/a291f1c5-a6b3-4465-9dcd-a8e3df1c5419" />

<img width="750" height="671" alt="image" src="https://github.com/user-attachments/assets/50fc3015-65a4-451f-8f56-94864dda5b23" />

<img width="782" height="629" alt="image" src="https://github.com/user-attachments/assets/05694c28-9b23-4335-9b0d-792a2fea1118" />



