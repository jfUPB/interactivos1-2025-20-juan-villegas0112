
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

## Actividad 02

🧐🧪✍️ Captura el resultado del experimento anterior.

<img width="989" height="195" alt="image" src="https://github.com/user-attachments/assets/59d25dc8-851d-4408-b8ac-e0ababd9ecf8" />

¿Por qué se ve este resultado?

- struct.pack('>2h2B', ...) empaqueta los datos en binario (bytes crudos), no en texto legible.

- Cada lectura produce 2 valores short (16 bits) y 2 byte (8 bits).

- Cuando esta en Texto el monitor, intenta interpretar esos bytes como caracteres de texto, pero como no son caracteres válidos, aparecen símbolos extraños (�).

🧐🧪✍️ Captura el resultado del experimento anterior. 

<img width="980" height="235" alt="image" src="https://github.com/user-attachments/assets/1dfc60da-2fb9-4f15-8f68-d28a21644acc" />

Lo que ves ¿Cómo está relacionado con esta línea de código?

``` py 
data = struct.pack('>2h2B', xValue, yValue, int(aState), int(bState))
```

- Esa línea genera 6 bytes por muestra.

- Cada paquete sigue el orden: x (2 bytes), y (2 bytes), A (1 byte), B (1 byte).

- En el monitor, al poner Todo en HEX, se puede ver como bytes crudos.


🧐🧪✍️ ¿Qué ventajas y desventajas ves en usar un formato binario en lugar de texto en ASCII?


| Aspecto               | Binario                      | Texto ASCII                 |
| --------------------- | ---------------------------- | --------------------------- |
| Tamaño                | Pequeño                      | Grande (más bytes)          |
| Velocidad             | Alta                         | Baja                        |
| Robustez ante errores | Baja                         | Alta                        |
| Exactitud             | Alta                         | Media                       |


🧐🧪✍️ Captura el resultado del experimento. 

<img width="982" height="191" alt="image" src="https://github.com/user-attachments/assets/cc51706c-f670-45b5-9a60-89127b2577c9" />


¿Cuántos bytes se están enviando por mensaje? ¿Cómo se relaciona esto con el formato '>2h2B'? ¿Qué significa cada uno de los bytes que se envían?

- Se envían 6 bytes por mensaje.

- El formato '>2h2B' define su cantidad, tamaño y orden.

- Los 6 bytes representan:

     2 bytes: xValue

     2 bytes: yValue

     1 byte: aState

     1 byte: bState

🧐🧪✍️ Recuerda de la unidad anterior que es posible enviar números positivos y negativos para los valores de xValue y yValue. ¿Cómo se verían esos números en el formato '>2h2B'?

| Campo  | Valor    |
| ------ | -------- |
| xValue | **−712** |
| yValue | **−532** |
| aState | 0        |
| bState | 0        |

## Actividad 02

🧐🧪✍️ Explica por qué en la unidad anterior teníamos que enviar la información delimitada y además marcada con un salto de línea y ahora no es necesario.

Porque cuan hay un tamaño fijo de bytes no se necesita un separador, ademas es mas eficiente y no hace un cambio a un lenguaje legible sino que solo lo envia tal y como lo recibe.







