
# Evidencias de la unidad 6

## Actividad 01

***🧐🧪✍️ Reporte***

***¿Qué ocurrió en la terminal cuando ejecutaste npm install? ¿Cuál crees que es su propósito?***

Se vio como se descargo todo el programa, ademas actualiza los datos con respecto al tiempo de utilizacion.

<img width="519" height="223" alt="image" src="https://github.com/user-attachments/assets/6cb5fef3-7df8-47e5-9542-231bc6945076" />


***¿Qué mensaje específico apareció en la terminal después de ejecutar npm start? ¿Qué indica este mensaje?***
```
Server is listening on http://localhost:3000
``` 
Esto significa que la aplicacion ya esta funcionando en dicha url.


***Describe lo que ves inicialmente en page1 y page2 en tu navegador.***

Al inicio sale un mensaje que dice : Esperando a la conexion, luego que se abren las dos ya empiea a correr el programa con normalidad.

***¿Qué mensajes aparecieron en la terminal del servidor cuando abriste page1 y page2?***

Muestra que un usuario se ha contectado, luego enseña en que pagina esta conectado, en la 1, la dos, o ambas. 

<img width="679" height="211" alt="image" src="https://github.com/user-attachments/assets/649b1d4f-834b-4707-840d-1fac2b709cff" />


***Describe qué sucede en ambas páginas del navegador cuando mueves una de las ventanas. ¿Cambia algo visualmente? ¿Qué mensajes aparecen (si los hay) en la consola del navegador (usualmente accesible con F12 -> Pestaña Consola) y en la terminal del servidor?***

Se generan unos circulos rojos que van conectados mediante un cable, si uno mueve la pestaña de una de ñlas paginas el cable seguirá el movimiento del otro circulo. En el navegador se va generando una actualizaion constante de coordenadas y del estado del cliente, es decir, si esta sincronizado o no. 

## Actividad 02

***🧐✍️ Reporte***

***Piensa en cómo te conectas a Internet en casa o en la Universidad. ¿Usas Wi-Fi? ¿Un cable de red? Eso es simplemente tu “rampa de acceso” a la gran red de carreteras. ¿Qué pasaría si esa rampa se corta? Anota tus ideas.***

- Si la rampa se corta no hay un ingreso a la red de carreteras, pues en esta rampa se encuentra la entrada o lo que permite generar una conexion. Si el computador tiene conexion sin cable 

***¿Puedes identificar otros ejemplos de relaciones Cliente-Servidor en tu vida diaria (no necesariamente digitales)? Por ejemplo, al pedir comida en un restaurante. ¿Quién es el cliente y quién el servidor? ¿Qué se pide y qué se entrega***

🏥 Consulta médica

- Cliente: Paciente.

- Servidor: Doctor o especialista.

- Lo que se pide: Diagnóstico o tratamiento.

- Lo que se entrega: Información médica, recetas, recomendaciones.

🏦 Banco

- Cliente: Persona que necesita hacer una operación (retirar dinero, abrir cuenta).

- Servidor: Cajero o asesor bancario.

- Lo que se pide: Servicios financieros.

- Lo que se entrega: Dinero, información, servicio solicitado.

🍽️ Restaurante

- Cliente: El comensal (tú).

- Servidor: El mesero o camarero.

- Lo que se pide: Comida y bebida del menú.

- Lo que se entrega: Los platillos y bebidas solicitados.

***Toma la URL de tu sitio web favorito. Intenta identificar el protocolo, el nombre de dominio y la ruta (si la hay). ¿Qué crees que pasa si solo escribes el nombre de dominio (ej. www.google.com) sin una ruta específica? ¿Qué “página por defecto” crees que te envía el servidor?***

🌐 URL analizada

https://futbol-11.com/

✅ Partes de la URL

Protocolo:
https://
→ HTTPS : la comunicación entre tu navegador y el servidor está cifrada y es segura.

Nombre de dominio:
futbol-11.com
→ Es el servidor. Este nombre se resuelve en una dirección IP para ubicar el servidor en Internet.

Ruta:
No hay ruta.

❓ ¿Qué sucede si solo se escribe el dominio?

El navegador va al servidor asociado con futbol-11.com.

En ese caso, normalmente devuelve la página por defecto: puede ser index.html, home.html, o alguna página principal definida por el sitio.

🔍 ¿Qué muestra la página inicial?

Al ingresar a https://futbol-11.com/
 aparece:

“We’re sorry but football-wordle doesn’t work properly without JavaScript enabled...” 

Esto indica que la página principal requiere que se tenga JavaScript habilitado para funcionar correctamente.

***🧐✍️ Reporte***

Compara HTTP con los protocolos seriales que usaste.

***¿Qué similitudes encuentras?***

Ambos son protocolos de comunicación, es decir, un conjunto de reglas que permiten que dos dispositivos se entiendan. En el caso del micro:bit, usábamos ASCII o binario con un esquema de inicio y fin para que p5.js pudiera interpretar los datos; con HTTP, el navegador y el servidor también siguen un formato específico para que los mensajes no se confundan. En los dos casos, si no se respeta el protocolo, la información no se puede interpretar correctamente.

***¿Qué diferencias clave ves?***

La principal diferencia está en la escala y en la complejidad. Los protocolos seriales transmiten datos básicos entre dos dispositivos conectados directamente, mientras que HTTP funciona a nivel global, en internet, permitiendo que cualquier navegador pueda pedir recursos a cualquier servidor en el mundo. Además, el protocolo serial se basa en el envío de bytes o caracteres simples, mientras que HTTP organiza la información en métodos (GET, POST), cabeceras, códigos de estado y tipos de contenido. Es decir, HTTP no solo manda datos, sino también instrucciones sobre cómo deben procesarse.

***¿Por qué crees que HTTP necesita ser más complejo que un simple envío de bytes como hacías con el micro:bit?***

HTTP necesita esta complejidad porque la web no se limita a transmitir datos crudos, sino que debe manejar múltiples tipos de recursos (texto, imágenes, videos, JSON, etc.), informar sobre errores o estados de la comunicación y mantener compatibilidad universal. En cambio, con el micro:bit bastaba con enviar valores numéricos o caracteres y asegurarse de que el otro extremo los entendiera en el mismo orden.

En conclusión, mientras que los protocolos seriales son como un “idioma sencillo” entre dos dispositivos cercanos, HTTP es un lenguaje mucho más completo y estandarizado que permite que millones de computadoras en el mundo puedan comunicarse de manera efectiva.


***🧐✍️ Reporte***

***Piensa en una página web simple, como un formulario de login.***

***¿Qué parte crees que es HTML (ej. los campos de texto, el botón)?***

Define la estructura básica. En este caso serían los campos de texto para “Usuario” y “Contraseña”, además del botón de “Iniciar sesión”. Es como el esqueleto del formulario, sin importar aún cómo se ve.

***¿Qué parte es CSS (ej. el color del botón, el tipo de letra)?***

Se encarga de darle la apariencia visual al formulario. Aquí entran cosas como el color azul del botón de “Iniciar sesión”, el tipo y tamaño de letra en las etiquetas de los campos, los márgenes para que todo quede alineado y, en general, el diseño que hace que la página se vea atractiva y ordenada.

***¿Qué parte es JavaScript (ej. la comprobación de si escribiste algo antes de enviar, el mensaje de “contraseña incorrecta” que aparece sin recargar la página)?***

Aporta la interactividad. En el login, sería el código que revisa si los campos están vacíos antes de permitir enviar el formulario, o el que muestra un mensaje en pantalla como “Contraseña incorrecta” sin necesidad de recargar toda la página. También podría usarse para validar en tiempo real que el correo escrito tenga un formato válido.

***🧐✍️ Reporte***

***Compara el bucle draw() de p5.js con este modelo de “esperar a que algo pase y reaccionar”.***

***¿Qué ventajas crees que tiene el modelo basado en eventos para una interfaz de usuario web?***

1. Eficiencia: no consume recursos innecesarios porque solo ejecuta código cuando algo realmente ocurre.

2. Escalabilidad: permite manejar muchas interacciones diferentes (clics, entradas de teclado, cambios de ventana) sin necesidad de revisar todo en cada “frame”.

3. Experiencia de usuario fluida: la página se siente más ligera y responde justo cuando el usuario la necesita, en vez de estar corriendo procesos en segundo plano constantemente.


***¿Sería eficiente tener un bucle draw() redibujando toda la página 60 veces por segundo si nada ha cambiado?***

Definitivamente no. Sería un gasto enorme de procesamiento y memoria para el navegador, además de que haría más lenta la experiencia del usuario. En una página web, la mayor parte del tiempo los elementos son estáticos (texto, imágenes, botones) y solo cambian cuando el usuario interactúa. Por eso el modelo basado en eventos es mucho más apropiado: solo se actualiza lo que cambia y en el momento justo.

***🧐✍️ Reporte***

***¿Por qué crees que podría ser útil usar JavaScript tanto en el cliente (navegador) como en el servidor? ¿Se te ocurre alguna ventaja para los desarrolladores?***

Creo que una de las principales ventajas de usar JavaScript tanto en el navegador como en el servidor es la unificación del lenguaje. Antes, un desarrollador tenía que aprender un lenguaje para el cliente (JavaScript) y otro distinto para el servidor (como PHP, Java o Python). Con Node.js ya no es necesario cambiar de “chip” mental, porque se puede trabajar en toda la aplicación con un mismo lenguaje.

Ventajas para los desarrolladores:

Aprendizaje más simple: basta con aprender bien un solo lenguaje para poder trabajar en las dos capas de la aplicación.

Reutilización de código: funciones, validaciones o estructuras se pueden compartir entre cliente y servidor, evitando duplicar trabajo.


***🧐✍️ Reporte***

***Resume con tus propias palabras la diferencia fundamental entre una comunicación HTTP tradicional y una comunicación usando WebSockets/Socket.IO. ¿En qué tipo de aplicaciones has visto o podrías imaginar que se usa esta comunicación en tiempo real?***

La comunicación HTTP tradicional funciona con un esquema de petición–respuesta: el cliente pide algo y el servidor responde. Es como mandar correos electrónicos: cada vez que necesito información debo enviar una solicitud nueva. Esto funciona bien para cargar páginas o pedir recursos estáticos, pero no es eficiente si quiero actualizaciones constantes.

En cambio, los WebSockets (y Socket.IO como librería que los facilita) establecen una conexión directa y persistente entre cliente y servidor, como si fuera una llamada telefónica abierta. Una vez conectados, ambos lados pueden enviarse mensajes en cualquier momento sin necesidad de hacer nuevas peticiones HTTP. Esto permite comunicación instantánea y en tiempo real.

Aplicaciones donde se usa comunicación en tiempo real:

- Chats en línea (WhatsApp Web, Messenger, Slack).

- Videojuegos multijugador en navegador, donde los movimientos de un jugador deben verse inmediatamente en los demás.

- Aplicaciones colaborativas como Google Docs, donde ves lo que otros escriben en tiempo real.


## Actividad 03

***🧐🧪✍️ Experimenta***

***Intenta acceder a http://localhost:3000/page1. ¿Funciona?***

No funcionó, porque la ruta ya no existe.

****Ahora intenta acceder a http://localhost:3000/pagina_uno. ¿Funciona?****

Funcionó, porque coincide con la nueva ruta definida en el servidor.

****¿Qué te dice esto sobre cómo el servidor asocia URLs con respuestas? Restaura el código.****

Esto confirma que el servidor funciona como un “mapa” de rutas: cada URL debe estar definida explícitamente en el código para que sea válida.


***🧐🧪✍️Experimenta***


***Abre http://localhost:3000/page1 en una pestaña. Observa la terminal del servidor. ¿Qué mensaje ves? Anota el ID.***

``` A user connected - ID: Bqv_vGEsW0ky006GAAAD```

***Abre http://localhost:3000/page2 en OTRA pestaña. Observa la terminal. ¿Qué mensaje ves? ¿El ID es diferente?***

```A user connected - ID: sU5_ERGIKcqbv39ZAAAB```

***Cierra la pestaña de page1. Observa la terminal. ¿Qué mensaje ves? ¿Coincide el ID con el que anotaste?***

```User disconnected - ID: Bqv_vGEsW0ky006GAAAD, si coincide con el id```


***🧐🧪✍️Experimenta***

***Mueve la ventana de page1. Observa la terminal del servidor. ¿Qué evento se registra (win1update o win2update)? ¿Qué datos (Data:) ves?***

```Received win1update from ID: NGv9dd_yaSjt5D56AAAC Data: { x: 225, y: 299, width: 500, height: 291 }```

- El evento es win1update y los datos (Data:) corresponden a la posición y tamaño de la ventana de Page1 (x, y, width, height).

Cada vez que se mueve la ventana, aparece un nuevo win1update con las coordenadas actualizadas (x, y).

***Mueve la ventana de page2. Observa la terminal. ¿Qué evento se registra ahora? ¿Qué datos ves?***

```Received win2update from ID: jYsl1CFOdheZFlnCAAAD Data: { x: 1313, y: 252, width: 500, height: 354 }```

Experimento clave: cambia socket.broadcast.emit(‘getdata’, page1); por socket.emit(‘getdata’, page1); (quitando broadcast). Reinicia el servidor, abre ambas páginas. Mueve page1. ¿Se actualiza la visualización en page2? ¿Por qué sí o por qué no? (Pista: ¿A quién le envía el mensaje socket.emit?). Restaura el código a broadcast.emit.

 Page2 no se actualiza, porque ```socket.emit(...)``` envía el mensaje solo al cliente que originó la acción (en este caso page1), mientras que ```socket.broadcast.emit(...)``` lo envía a todos los demás clientes conectados excepto al emisor.
Entonces, al quitar broadcast, el evento no llega a page2.

***🧐🧪✍️ Experimenta***

***Inicia el servidor. ¿Qué mensaje ves en la consola? ¿En qué puerto dice que está escuchando?***

```Server is listening on http://localhost:3001```



***Intenta abrir http://localhost:3000/page1. ¿Funciona?***

No funciona


***Intenta abrir http://localhost:3001/page1. ¿Funciona?***

Si funciona.
```
A user connected - ID: FduPChtBtW22FqjeAAAB
Received win1update from ID: FduPChtBtW22FqjeAAAB Data: { x: 0, y: 0, width: 1920, height: 945 }
```


***¿Qué aprendiste sobre la variable port y la función listen? Restaura el puerto a 3000.***

La variable port define dónde escucha el servidor. server.listen(port) abre la conexión en ese número de puerto; si lo cambias, las URLs deben usar el nuevo puerto.


## Actividad 04

***🧐🧪✍️ Experimenta***


***Refresca la página page2.html. Observa la consola del navegador. ¿Ves algún error relacionado con la conexión? ¿Qué indica?***

<img width="522" height="47" alt="image" src="https://github.com/user-attachments/assets/55de7944-595b-42a6-95f5-463b70733f79" />

***Vuelve a iniciar el servidor y refresca la página. ¿Desaparecen los errores?***

Sí desaparecen.

<img width="517" height="20" alt="image" src="https://github.com/user-attachments/assets/4f2c7b57-e95f-4519-a3fb-1829207f7354" />

🧐🧪✍️ Experimenta

<img width="493" height="203" alt="image" src="https://github.com/user-attachments/assets/f496fe68-9c7e-4db2-8d74-58154a78d87f" />


***¿Qué pasó? ¿Por qué?***

Al inicio no se sincronizaron las páginas porque al comentar el socket.emit('win2update') dentro del connect, page2 ya no avisó de su estado inicial al servidor. La sincronización solo empezó cuando moví page2, ya que en ese momento se emitió manualmente un win2update con los datos actualizados. Porque la línea comentada era la que enviaba la señal inicial de identificación y estado al servidor. Sin esa señal, el servidor no sabía nada de page2 ni de sus datos, por eso page1 no recibió información al inicio. Solo cuando page2 cambió su posición se generó un nuevo win2update que activó el flujo de sincronización.

***🧐🧪✍️ Experimenta***

***Asegúrate de tener este console.log en page2.js.***

***Abre ambas páginas.***

***Mueve la ventana de page1. Observa la consola del navegador de page2. ¿Qué datos muestra?***

<img width="521" height="139" alt="image" src="https://github.com/user-attachments/assets/d8760827-51de-414e-b709-452ab135183f" />

Las coordenadas y el tamaño de la pestaña de page1

***Mueve la ventana de page2. Observa la consola de page1. ¿Qué pasa? ¿Por qué?***

Cuando muevo la ventana de page2, normalmente no veo que la consola de page1 muestre datos nuevos o cambios. Esto ocurre porque en el código original, solo la ventana page1 está enviando sus datos a la otra ventana (page2)



***🧐🧪✍️Experimenta***

***Observa checkWindowPosition() en page2.js y modifica el código del if para comprobar si el código dentreo de este se ejecuta.***

``` js
 if (currentPageData.x !== previousPageData.x || currentPageData.y !== previousPageData.y || 
    currentPageData.width !== previousPageData.width || currentPageData.height !== previousPageData.height) {

    console.log('Cambio detectado en ventana:', currentPageData);

    point2 = [currentPageData.width / 2, currentPageData.height / 2];
    socket.emit('win2update', currentPageData, socket.id);
    previousPageData = currentPageData; 
```

***Mueve cada ventana y observa las consolas.***
***¿Qué puedes concluir y por qué?***


<img width="517" height="53" alt="image" src="https://github.com/user-attachments/assets/c6757bbe-bb38-4356-ba52-c9d912570740" />


Al ejecutar el código y mover la ventana, la consola del navegador me mostró el mensaje "Cambio detectado en ventana:" seguido de los datos de posición y tamaño.
Esto me confirma que la función checkWindowPosition() sí se está ejecutando correctamente dentro del ciclo draw() y que está evaluando las condiciones del if para detectar cambios.
También confirma que el socket está funcionando porque el estado SYNCED ya se alcanzó y los datos se están enviando al servidor.

Por lo tanto, puedo concluir que:

La detección de movimiento de ventana está bien implementada,

El cliente está emitiendo correctamente los datos,

Y el flujo de sincronización está funcionando como se espera.

***🧐🧪✍️ Experimenta***

***Cambia el background(220) para que dependa de la distancia entre las ventanas. Puedes calcular la magnitud del resultingVector usando let distancia = resultingVector.mag(); y luego usa map() para convertir esa distancia a un valor de gris o color. background(map(distancia, 0, 1000, 255, 0)); (ajusta el rango 0-1000 según sea necesario).***


<img width="1082" height="410" alt="image" src="https://github.com/user-attachments/assets/83b8c6fa-a044-4df4-9106-27265a23082c" />


<img width="1370" height="399" alt="image" src="https://github.com/user-attachments/assets/f739e6ca-6e08-4ecc-bc04-fffeca189077" />


``` js
function draw() 
{
    if (!isConnected) {
        background(220);
        showStatus('Conectando al servidor...', color(255, 165, 0));
        return;
    }

    if (!hasRemoteData) {
        background(220);
        showStatus('Esperando conexión de la otra ventana...', color(255, 165, 0));
        return;
    }

    if (!isFullySynced) {
        background(220);
        showStatus('Sincronizando datos...', color(255, 165, 0));
        return;
    }

    
    let vector1 = createVector(currentPageData.x, currentPageData.y);
    let vector2 = createVector(remotePageData.x, remotePageData.y);
    let resultingVector = p5.Vector.sub(vector2, vector1);
    let distancia = resultingVector.mag();

   
    let fondo = map(distancia, 0, 1000, 255, 0); 
    background(fondo); 


    drawCircle(point2[0], point2[1]);
    checkWindowPosition();

    stroke(50);
    strokeWeight(20);
    drawCircle(resultingVector.x + remotePageData.width / 2, resultingVector.y + remotePageData.height / 2);
    line(point2[0], point2[1], resultingVector.x + remotePageData.width / 2, resultingVector.y + remotePageData.height / 2);
}

```
***Inventa otra modificación creativa.***

<img width="1047" height="403" alt="image" src="https://github.com/user-attachments/assets/5550fce2-1beb-4dcf-ba62-cf95e15549f0" />


<img width="1830" height="408" alt="image" src="https://github.com/user-attachments/assets/535eab69-2ff2-4d15-aff8-b95845af0101" />


```js
function drawCircle(x, y) {
   
    let vector1 = createVector(currentPageData.x, currentPageData.y);
    let vector2 = createVector(remotePageData.x, remotePageData.y);
    let distancia = p5.Vector.sub(vector2, vector1).mag();

    
    let tam = map(distancia, 0, 1000, 50, 200);

    fill(255, 0, 0);
    ellipse(x, y, tam, tam);
}
```
## Actividad 05

🧐🧪✍️ En tu bitácora

***Explica tu idea y realiza algunos bocetos.***

Semáforo Interactivo en Tiempo Real: Una aplicación donde dos usuarios pueden controlar y observar juntos el estado de un semáforo.

Funcionamiento:

- El cliente A hace clic en un botón (“verde”, “amarillo”, “rojo”).

- El servidor recibe el cambio y lo retransmite a todos los clientes.

- El cliente B ve que el semáforo cambió de color en su pantalla al mismo tiempo.

- Ambos siempre ven el mismo estado del semáforo.

<img width="958" height="432" alt="image" src="https://github.com/user-attachments/assets/dedcadb1-70bb-4a49-9454-eceaaf532e9a" />

***Implementa tu idea.***



***Incluye todos los códigos (servidor y clientes) en tu bitácora.***


## Autoevaluacion

4: realicé 4 actividades completas y la autoevaluación.


A pesar de que me faltó terminar una de las actividades, considero que merezco una nota de 4 porque en las demás evidencias realicé un trabajo completo, con explicaciones detalladas, pruebas adicionales y aportes creativos que muestran un entendimiento sólido de los temas. El esfuerzo y la dedicación en la mayor parte del proceso reflejan compromiso con el aprendizaje y un desempeño que cumple con los objetivos principales de la unidad.


