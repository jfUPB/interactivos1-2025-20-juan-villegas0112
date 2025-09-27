
# Evidencias de la unidad 6

## Actividad 01

🧐🧪✍️ Reporte

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

🧐✍️ Reporte

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

🧐✍️ Reporte

Compara HTTP con los protocolos seriales que usaste.

***¿Qué similitudes encuentras?***

Ambos son protocolos de comunicación, es decir, un conjunto de reglas que permiten que dos dispositivos se entiendan. En el caso del micro:bit, usábamos ASCII o binario con un esquema de inicio y fin para que p5.js pudiera interpretar los datos; con HTTP, el navegador y el servidor también siguen un formato específico para que los mensajes no se confundan. En los dos casos, si no se respeta el protocolo, la información no se puede interpretar correctamente.

***¿Qué diferencias clave ves?***

La principal diferencia está en la escala y en la complejidad. Los protocolos seriales transmiten datos básicos entre dos dispositivos conectados directamente, mientras que HTTP funciona a nivel global, en internet, permitiendo que cualquier navegador pueda pedir recursos a cualquier servidor en el mundo. Además, el protocolo serial se basa en el envío de bytes o caracteres simples, mientras que HTTP organiza la información en métodos (GET, POST), cabeceras, códigos de estado y tipos de contenido. Es decir, HTTP no solo manda datos, sino también instrucciones sobre cómo deben procesarse.

***¿Por qué crees que HTTP necesita ser más complejo que un simple envío de bytes como hacías con el micro:bit?***

HTTP necesita esta complejidad porque la web no se limita a transmitir datos crudos, sino que debe manejar múltiples tipos de recursos (texto, imágenes, videos, JSON, etc.), informar sobre errores o estados de la comunicación y mantener compatibilidad universal. En cambio, con el micro:bit bastaba con enviar valores numéricos o caracteres y asegurarse de que el otro extremo los entendiera en el mismo orden.

En conclusión, mientras que los protocolos seriales son como un “idioma sencillo” entre dos dispositivos cercanos, HTTP es un lenguaje mucho más completo y estandarizado que permite que millones de computadoras en el mundo puedan comunicarse de manera efectiva.


🧐✍️ Reporte

***Piensa en una página web simple, como un formulario de login.***

***¿Qué parte crees que es HTML (ej. los campos de texto, el botón)?***

Define la estructura básica. En este caso serían los campos de texto para “Usuario” y “Contraseña”, además del botón de “Iniciar sesión”. Es como el esqueleto del formulario, sin importar aún cómo se ve.

***¿Qué parte es CSS (ej. el color del botón, el tipo de letra)?***

Se encarga de darle la apariencia visual al formulario. Aquí entran cosas como el color azul del botón de “Iniciar sesión”, el tipo y tamaño de letra en las etiquetas de los campos, los márgenes para que todo quede alineado y, en general, el diseño que hace que la página se vea atractiva y ordenada.

***¿Qué parte es JavaScript (ej. la comprobación de si escribiste algo antes de enviar, el mensaje de “contraseña incorrecta” que aparece sin recargar la página)?***

Aporta la interactividad. En el login, sería el código que revisa si los campos están vacíos antes de permitir enviar el formulario, o el que muestra un mensaje en pantalla como “Contraseña incorrecta” sin necesidad de recargar toda la página. También podría usarse para validar en tiempo real que el correo escrito tenga un formato válido.

🧐✍️ Reporte

***Compara el bucle draw() de p5.js con este modelo de “esperar a que algo pase y reaccionar”.***

***¿Qué ventajas crees que tiene el modelo basado en eventos para una interfaz de usuario web?***

1. Eficiencia: no consume recursos innecesarios porque solo ejecuta código cuando algo realmente ocurre.

2. Escalabilidad: permite manejar muchas interacciones diferentes (clics, entradas de teclado, cambios de ventana) sin necesidad de revisar todo en cada “frame”.

3. Experiencia de usuario fluida: la página se siente más ligera y responde justo cuando el usuario la necesita, en vez de estar corriendo procesos en segundo plano constantemente.


***¿Sería eficiente tener un bucle draw() redibujando toda la página 60 veces por segundo si nada ha cambiado?***

Definitivamente no. Sería un gasto enorme de procesamiento y memoria para el navegador, además de que haría más lenta la experiencia del usuario. En una página web, la mayor parte del tiempo los elementos son estáticos (texto, imágenes, botones) y solo cambian cuando el usuario interactúa. Por eso el modelo basado en eventos es mucho más apropiado: solo se actualiza lo que cambia y en el momento justo.

🧐✍️ Reporte

***¿Por qué crees que podría ser útil usar JavaScript tanto en el cliente (navegador) como en el servidor? ¿Se te ocurre alguna ventaja para los desarrolladores?***

Creo que una de las principales ventajas de usar JavaScript tanto en el navegador como en el servidor es la unificación del lenguaje. Antes, un desarrollador tenía que aprender un lenguaje para el cliente (JavaScript) y otro distinto para el servidor (como PHP, Java o Python). Con Node.js ya no es necesario cambiar de “chip” mental, porque se puede trabajar en toda la aplicación con un mismo lenguaje.

Ventajas para los desarrolladores:

Aprendizaje más simple: basta con aprender bien un solo lenguaje para poder trabajar en las dos capas de la aplicación.

Reutilización de código: funciones, validaciones o estructuras se pueden compartir entre cliente y servidor, evitando duplicar trabajo.


🧐✍️ Reporte

***Resume con tus propias palabras la diferencia fundamental entre una comunicación HTTP tradicional y una comunicación usando WebSockets/Socket.IO. ¿En qué tipo de aplicaciones has visto o podrías imaginar que se usa esta comunicación en tiempo real?***

La comunicación HTTP tradicional funciona con un esquema de petición–respuesta: el cliente pide algo y el servidor responde. Es como mandar correos electrónicos: cada vez que necesito información debo enviar una solicitud nueva. Esto funciona bien para cargar páginas o pedir recursos estáticos, pero no es eficiente si quiero actualizaciones constantes.

En cambio, los WebSockets (y Socket.IO como librería que los facilita) establecen una conexión directa y persistente entre cliente y servidor, como si fuera una llamada telefónica abierta. Una vez conectados, ambos lados pueden enviarse mensajes en cualquier momento sin necesidad de hacer nuevas peticiones HTTP. Esto permite comunicación instantánea y en tiempo real.

Aplicaciones donde se usa comunicación en tiempo real:

- Chats en línea (WhatsApp Web, Messenger, Slack).

- Videojuegos multijugador en navegador, donde los movimientos de un jugador deben verse inmediatamente en los demás.

- Aplicaciones colaborativas como Google Docs, donde ves lo que otros escriben en tiempo real.






