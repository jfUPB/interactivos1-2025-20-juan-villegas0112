
# Evidencias de la unidad 7

## Actividad 01

***🧐🧪✍️ Reporta en tu bitácora***

**¿Qué URL de Dev Tunnels obtuviste? ¿Por qué crees que necesitamos usar esta URL en lugar de http://localhost:3000 o la IP local de tu computador para que el celular se conecte?**

https://v9xk7s8d-3000.use2.devtunnels.ms/

Lo que pasa es que localhost solo sirve dentro del mismo computador, entonces el celular no puede entrar ahí porque no está en la misma red interna del PC. En cambio, Dev Tunnels crea una dirección pública en internet que redirige a mi servidor local, y así el celular sí puede conectarse desde cualquier parte. Básicamente, es como “sacar” el servidor del computador para que sea visible por fuera.

**Describe brevemente qué hace npm install y npm start.**

- El npm install busca y descarga todas las dependencias que necesita el proyecto (por ejemplo express y socket.io). Solo se hace una vez para preparar el entorno.
- El npm start ya ejecuta el servidor, o sea que corre el archivo server.js y deja el sistema listo para que las páginas (desktop y mobile) se conecten entre sí.

**¿Qué mensajes observaste en la terminal del servidor al conectar el cliente de escritorio y el cliente móvil? ¿Eran diferentes los mensajes o identificadores?**

<img width="376" height="198" alt="image" src="https://github.com/user-attachments/assets/332a3bfa-8b3e-4d32-a18c-b28b84760d4f" />

Cada vez que se conectaba una página (ya fuera la del computador o la del celular) aparecía un mensaje distinto con su identificador de cliente. Sin embargo, los logs más frecuentes aparecían cuando se movía el dedo en el celular, porque ahí es cuando se envían los datos del movimiento al servidor.

<img width="520" height="576" alt="image" src="https://github.com/user-attachments/assets/5167f185-e94c-4725-97c0-c66f05173419" />


**Describe el comportamiento observado: ¿Funcionó la interacción? ¿Hubo algún retraso (latencia)?**

Sí funcionó correctamente. Desde el celular se movía el dedo sobre la pantalla y el círculo del computador respondía casi al instante. Se notaba un pequeño retraso, pero muy leve, probablemente por la conexión del túnel, ya que al correrlo localmente la respuesta era inmediata.

## Actividad 02

***🧐🧪✍️ Reporta en tu bitácora***

**Explica con tus propias palabras: ¿Por qué es necesario Dev Tunnels en este escenario y cómo funciona conceptualmente?**

Dev Tunnels es necesario porque el localhost solo funciona dentro del mismo computador, y el celular no puede acceder ahí directamente. Entonces, lo que hace Dev Tunnels es crear un “camino” o túnel seguro que conecta una dirección pública en internet con el servidor local que está corriendo en el PC.
En otras palabras, Dev Tunnels actúa como un intermediario que recibe las peticiones desde cualquier parte y las redirige hasta el servidor del computador, sin exponerlo directamente. Es como tener un número de teléfono público que redirige las llamadas a tu línea privada.

**Describe la función de touchMoved() y por qué se usa la variable threshold en el cliente móvil.**

La función touchMoved() en p5.js se ejecuta constantemente mientras el usuario mantiene el dedo presionado y lo mueve sobre la pantalla. Ahí es donde se leen las coordenadas mouseX y mouseY, que representan la posición actual del toque, y se envían al servidor para actualizar la posición del círculo en el computador.
La variable threshold se usa para que el código solo envíe información cuando haya un movimiento “grande” o significativo. Si el dedo se mueve muy poquito o tiembla, no manda nada. Esto ayuda a que la red no se llene de mensajes innecesarios y la conexión sea más fluida.

**Compara brevemente Dev Tunnels con simplemente usar la IP local. ¿Cuáles son las ventajas y desventajas de cada uno?**
La IP local sirve si el celular y el computador están conectados a la misma red Wi-Fi. Es rápida y directa porque no pasa por internet, pero tiene el problema de que solo funciona dentro de esa red. Si el celular usa datos o está en otra red, ya no sirve, y a veces los firewalls bloquean la conexión.

En cambio, Dev Tunnels crea una URL pública (con HTTPS) que cualquiera puede usar para conectarse al servidor, sin importar la red. Es más flexible y fácil para pruebas o para compartir el proyecto, aunque puede tener un poco más de latencia y depende de que el túnel esté activo. En resumen:

- IP local: más rápida y estable, pero limitada a la red local.

- Dev Tunnels: más accesible y práctica, pero con un poco más de retardo.

**Coloca en tu bitácora capturas de pantalla del sistema completo funcionando. Esto lo puedes hacer abriendo tanto el mobile como el desktop en tu computador y tomando una captura de pantalla de todos los involucrados (celular, computador y terminal).**

<img width="242" height="315" alt="image" src="https://github.com/user-attachments/assets/3bbc1861-ff38-44cb-9a6d-6c757eef65d4" />

<img width="458" height="273" alt="image" src="https://github.com/user-attachments/assets/83d4d4f7-9c57-4e50-81e8-0df633573022" />

<img width="270" height="344" alt="image" src="https://github.com/user-attachments/assets/0e127ec1-92fb-407e-91b3-e72847cf5309" />


## Actividad 03

***🧐🧪✍️ Reporta en tu bitácora***

**¿Cuál es la función principal de express.static(‘public’) en este servidor? ¿Cómo se compara con el uso de app.get(‘/ruta’, …) del servidor de la Unidad 6?**

La función principal de express.static('public') es permitir que el servidor envíe automáticamente todos los archivos que estén dentro de la carpeta public (como los HTML, CSS o los scripts de p5.js), sin tener que escribir una ruta para cada uno.
En cambio, con app.get('/ruta', …) tocaba definir manualmente qué archivo devolver para cada solicitud. O sea, con express.static() el servidor ya sabe que todo lo que esté en esa carpeta puede ser mostrado directamente, mientras que con app.get() hay que programar la respuesta una por una.

**Explica detalladamente el flujo de un mensaje táctil: ¿Qué evento lo envía desde el móvil? ¿Qué evento lo recibe el servidor? ¿Qué hace el servidor con él? ¿Qué evento lo envía el servidor al escritorio? ¿Por qué se usa socket.broadcast.emit en lugar de io.emit o socket.emit en este caso?**

- El flujo empieza en el móvil, cuando ocurre el evento táctil touchMoved() de p5.js. En ese momento, el código usa socket.emit('message', datos) para enviar al servidor las coordenadas del toque.
- El servidor recibe ese mensaje dentro de socket.on('message', ...), lo muestra por consola con console.log y luego lo reenvía a los demás clientes con socket.broadcast.emit('message', datos).
- El escritorio (o cualquier otro cliente conectado) tiene su propio socket.on('message', ...), donde recibe esos datos y actualiza la posición del círculo en pantalla.
- Se usa socket.broadcast.emit porque así el mensaje llega a todos los clientes excepto al que lo envió. Si se usara socket.emit, solo lo recibiría el emisor; y si se usara io.emit, se enviaría a todos, incluyendo al mismo celular, lo que causaría mensajes duplicados.

**Si conectaras dos computadores de escritorio y un móvil a este servidor, y movieras el dedo en el móvil, ¿Quién recibiría el mensaje retransmitido por el servidor? ¿Por qué?**

El mensaje sería recibido por los dos computadores de escritorio, pero no por el celular. Esto pasa porque el servidor usa socket.broadcast.emit, que envía el mensaje a todos los clientes conectados excepto al que lo originó (en este caso, el móvil). De esa forma, los escritorios sí ven el movimiento, pero el celular no recibe su propio mensaje de vuelta.

**¿Qué información útil te proporcionan los mensajes console.log en el servidor durante la ejecución?**

Los console.log del servidor sirven para ver lo que está pasando “por detrás”. Muestran cuándo un cliente se conecta o se desconecta, cuándo llega un mensaje desde algún dispositivo y qué datos trae (como las coordenadas del toque). Esto ayuda mucho para verificar que todo está funcionando bien, entender el flujo de comunicación y detectar errores o desconexiones en tiempo real.


## Actividad 04

***🧐🧪✍️ Reporta en tu bitácora***

**Realiza un diagrama donde muestres el flujo completo de datos y eventos entre los tres componentes: móvil, servidor y escritorio. Puedes ilustrar con un ejemplo de coordenadas táctiles (x, y) y cómo viajan a través del sistema.**

<img width="426" height="675" alt="image" src="https://github.com/user-attachments/assets/abd426dd-509b-4bc6-a24f-5b53ed115def" />

## Apply 

1. Mi idea es usar la canción “See You Again” de Tyler, The Creator, inspirándome en las abejas que aparecen en su álbum. Quiero crear un enjambre de abejas que se muevan al ritmo de la música, cambiando de color y dirección según el sonido. Durante el coro, las abejas se desordenan y vuelan con más energía.

El touch del móvil servirá para guiarlas, como si el dedo fuera una flor que las atrae. Usaré una clase Abeja con update() y draw() para manejar cada una, y la conexión entre el móvil y el escritorio será con Node.js y p5.js, para que la animación reaccione en tiempo real.


<img width="1193" height="1200" alt="image" src="https://github.com/user-attachments/assets/0544de60-cefe-418e-8253-f30dc71bdf98" />

## Evidencias 🗂️

***Mi nota es 3,7***

Considero que mi trabajo merece una nota de 3,7 porque realicé las cuatro actividades completas, además de incluir un numeral del apply, demostrando un buen nivel de comprensión y aplicación de los temas. Cada parte del trabajo está bien desarrollada, con ideas claras, coherentes y creativas, mostrando dedicación y cumplimiento con todos los requerimientos planteados.


