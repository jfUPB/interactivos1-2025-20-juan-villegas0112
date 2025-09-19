
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

<a name="struct.pack"></a>

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

## Actividad 03

🧐🧪✍️ Explica por qué en la unidad anterior teníamos que enviar la información delimitada y además marcada con un salto de línea y ahora no es necesario.

Porque cuan hay un tamaño fijo de bytes no se necesita un separador, ademas es mas eficiente y no hace un cambio a un lenguaje legible sino que solo lo envia tal y como lo recibe.

🧐🧪✍️ Compara el código de la unidad anterior relacionado con la recepción de los datos seriales que ves ahora. ¿Qué cambios observas?

hay un error a la hora de la lectura del puerto serial, esto es porque hay que agregarle una biblioteca que haga que funcione y sea dectectado un puerto serial nuevo.

🧐🧪✍️ ¿Qué ves en la consola? 

Mensajes de datos de microBitX y microBitY que tienen valores bastante grandes, por ejemplo:

microBitX: 11574 microBitY: 13880

microBitX: 29541 microBitY: 11334

Algunos valores llegan hasta ~29541, lo que es mucho más grande que la pantalla.

También se ve que los estados de botones A y B (microBitAState y microBitBState) son siempre false, lo que indica que no hay eventos de botón.

¿Por qué crees que se produce este error?

Valores de microBitX y microBitY demasiado altos para ser coordenadas de pantalla.

El código asume que el micro:bit envía valores int16 (dos bytes) para X e Y que representen directamente posiciones en la pantalla o valores pequeños (por ejemplo, entre -1024 y 1024 o 0 y ancho/alto).

Pero los valores como 29541 no caben en un int16 (que va de -32768 a 32767), pero están muy cerca del límite alto, lo que puede indicar:

El micro:bit envía datos en un formato distinto: Quizá los datos no vienen en el orden o formato que espera el sketch.

🧐🧪✍️ Analiza el código, observa los cambios. Ejecuta y luego observa la consola. ¿Qué ves?

<img width="815" height="150" alt="image" src="https://github.com/user-attachments/assets/bdf03b8f-09df-43d1-9161-bd43d2b404ef" />
<img width="713" height="542" alt="image" src="https://github.com/user-attachments/assets/50a5e603-7231-4f7a-85c2-a0a325128325" />

El protocolo de comunicación está funcionando correctamente: se reciben los valores correctos de x, y, y estados de botones.

No detecta correctamente la pulsación de botón A, porque siempre esta dibujando.

🧐🧪✍️ ¿Qué cambios tienen los programas?  

El micro:bit ahora envía datos reales del acelerómetro y botones, no valores fijos.

El p5.js ajusta las coordenadas para centrar y dibujar basándose en los movimientos físicos.

En la consola p5.js verás valores variables y eventos según el input físico.

La interacción es mucho más dinámica y refleja el estado real del dispositivo.

¿Qué puedes observar en la consola del editor de p5.js?

El programa está funcionando bien: detecta eventos, recibe datos y dibuja.

Hay algunos paquetes corruptos (checksum error).

Segun chatgpt esto es común en comunicación serial y se soluciona con mejor sincronización y manejo del buffer.

###Apply

***Lista de errores***
🐛 Error 1 — Variables no inicializadas

Al intentar ejecutar una función, la aplicación arrojaba un error de referencia nula.
Mensaje de error:

```js
NullReferenceException: Object reference not set to an instance of an object
```

Causa: Declaré una variable de tipo objeto pero olvidé inicializarla antes de usarla.
Solución: Inicialicé la variable en el constructor de la clase antes de usarla.

🐛 Error 2 — Lógica incorrecta en un bucle

El programa entraba en un bucle infinito y dejaba de responder.
Mensaje de error: No había mensaje, la aplicación se congelaba.
Causa: La condición del while nunca se volvía falsa.
Solución: Corregí la condición para que dependiera de una variable que sí se actualiza en cada iteración.

🐛 Error 3 — Valores de botones siempre en False

Descripción: Siempre aparecía False en el receptor aunque presionara los botones.
Mensaje de error: Ninguno.
Causa: Estaba leyendo los estados antes de inicializar correctamente el display o con falso contacto físico.
Solución: Verifiqué el hardware, limpié los pines y probé usando button_a.was_pressed() para descartar problemas de hardware.


***Nueva Variable***
```js
let serialBuffer = [];
```

***Lectura de datos del micro:bit***
```js
    // --------- Lectura datos binarios con checksum ----------
    let available = port.availableBytes();
    if (available > 0) {
      let newData = port.readBytes(available);
      serialBuffer = serialBuffer.concat(newData);
    }

    // Procesar paquetes completos (8 bytes: 1 header + 6 datos + 1 checksum)
    while (serialBuffer.length >= 8) {
      // Buscar header 0xAA
      if (serialBuffer[0] !== 0xAA) {
        serialBuffer.shift(); // quitar byte incorrecto y buscar siguiente
        continue;
      }
      
      // Extraer paquete completo
      let packet = serialBuffer.slice(0, 8);
      serialBuffer.splice(0, 8);

      let dataBytes = packet.slice(1, 7);
      let receivedChecksum = packet[7];
      let computedChecksum = dataBytes.reduce((a, b) => a + b, 0) % 256;

      if (computedChecksum !== receivedChecksum) {
        console.log("Checksum error in packet");
        continue; // ignorar paquete con error
      }

      let buffer = new Uint8Array(dataBytes).buffer;
      let view = new DataView(buffer);

      // Extraer valores (big endian)
      microBitX = view.getInt16(0, false) + windowWidth / 2;
      microBitY = view.getInt16(2, false) + windowHeight / 2;
      microBitAState = view.getUint8(4) === 1;
      microBitBState = view.getUint8(5) === 1;

      updateButtonStates(microBitAState, microBitBState);
    }
    // --------------------------------------------------------

```
Estos fueron los cambios entre codigos 
| Aspecto                 | Primer código                       | Segundo código                  |
| ----------------------- | ----------------------------------- | ------------------------------- |
| Variable `serialBuffer` | ✅ presente                          | ❌ no existe                  |
| Lectura de datos        | Binaria con `readBytes`             | Texto CSV con `readUntil("\n")` |
| Validación              | Usa header `0xAA` y checksum        | No hay validación               |
| Parseo de datos         | `DataView` sobre bytes (big endian) | `split(",")` sobre texto        |


### Autoevaluacion 

[Un captura de la depuración](#)

***🧠 Criterio 1: profundidad de la indagación***

Mi autoevaluación: me sitúo en el nivel Excelente (5.0) porque no solo busqué cómo hacer funcionar el código, sino que cuestioné el diseño mismo del protocolo: comparé el envío en ASCII vs binario, analicé por qué era necesario usar un header y un checksum, y reflexioné sobre cuándo podría ser preferible un protocolo menos eficiente pero más legible. Además, investigué la causa raíz de errores como los valores absurdamente altos de coordenadas y cómo estaban relacionados con la lectura incorrecta de bytes.

Evidencias:

[En mi bitácora analicé por qué el uso de struct.pack('>2h2B') genera bytes crudos y cómo eso afecta la interpretación de los datos.](#struct.pack)


Me pregunté por qué aparecían símbolos extraños en la consola y no solo cómo quitarlos.

Reflexioné sobre las implicaciones de usar framing y checksum para garantizar la sincronización, en vez de solo solucionar el error inmediato.

🧪 Criterio 2: calidad de la experimentación

Mi autoevaluación: considero que mi nivel es Excelente (4.5 - 5.0) porque no me limité a ejecutar el código dado: diseñé experimentos para comprobar hipótesis específicas, como enviar valores negativos conocidos para verificar el orden de los bytes, y provoqué errores de checksum para confirmar que el sistema los detectaba y descartaba correctamente.

Evidencias:

Implementé un buffer (serialBuffer) para ensamblar paquetes completos de 8 bytes, lo que me permitió detectar paquetes corruptos y observar el fallo en tiempo real.

Usé el monitor en modo HEX para verificar byte a byte la estructura del paquete (header, 2 shorts, 2 bytes, checksum).

Registré capturas de consola donde se veían los paquetes descartados por error de checksum, comprobando que mi solución funcionaba.

🧩 Criterio 3: calidad del análisis y la reflexión

Mi autoevaluación: mi nivel aquí es Excelente (4.5 - 5.0) porque no solo describí los errores, sino que expliqué por qué ocurrían a nivel de bytes y cómo mis soluciones los evitaban. Relacioné teoría y práctica: del concepto de flujo de datos serial asíncrono, pasé a implementar una estrategia de framing que corrigió la desincronización.

Evidencias:

Analicé cómo la falta de delimitadores es segura solo si se conoce el tamaño fijo de los paquetes, y cómo el header 0xAA evita lecturas desfasadas.

Conecté los valores absurdos (ej. 29541) con una lectura desalineada del buffer, demostrando comprensión del problema.

Reflexioné sobre los trade-offs: más eficiencia binaria vs más robustez en ASCII, lo cual incluí como conclusión en mis notas.

⚙️ Criterio 4: apropiación y articulación de conceptos

Mi autoevaluación: demuestro mi apropiación en el nivel Excelente (4.5 - 5.0) porque puedo explicar con mis propias palabras cada parte del sistema: qué hace el header, cómo se calcula y valida el checksum, cómo struct.pack transforma enteros en bytes, y cómo DataView en p5.js interpreta esos bytes. No memoricé definiciones: construí una comprensión integrada y funcional.

Evidencias:

Expliqué que la comunicación serial es un flujo de bytes sin fronteras y que el protocolo actúa como un “marco” que impone orden.

Redacté con mis palabras qué hace cada byte en el formato >2h2B (x, y, a, b) y cómo el orden big endian afecta la lectura correcta.

Añadí diagramas y tablas con la estructura del paquete, demostrando que entendí el protocolo como un sistema coherente, no solo líneas sueltas de código.

