
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
