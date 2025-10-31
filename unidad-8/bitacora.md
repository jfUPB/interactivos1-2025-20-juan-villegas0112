
# Evidencias de la unidad 8

## Actividad 01

🧐🧪✍️ Reporta en tu bitácora

***Documenta los referentes visuales que te inspiren.***

<img width="1293" height="723" alt="image" src="https://github.com/user-attachments/assets/76b47e47-48ee-485b-a3ca-d02db72cb85d" />
<img width="800" height="464" alt="image" src="https://github.com/user-attachments/assets/2edc3b2f-83e2-4313-b17f-1f9b8c5bf5cd" />

La cancion que quiero usar para la interaccions será [PassionFruit](https://www.youtube.com/watch?v=COz9lDCFHjw&list=RDCOz9lDCFHjw&start_radio=1)


***Define el concepto de las visuales que quieres crear.***

Quiero hacer que se vea un cosmos en movimiento y que mediante la interaccion con el celular y el microbit aparezcan frutas y se pueda cambiar la cantidad de estas al aparecer.



***Explica cómo el móvil y el micro:bit controlarán las visuales.***

Cada que se presione la pantalla del celular aparecera una fruta y con los botones a y b del microbit quiero que aumenten el numero de furtas que aparezcan cada que se presione la pantalla del celular.


***Haz un bocetos de todas las interfaces del sistema.***

-pantalla

<img width="1162" height="598" alt="image" src="https://github.com/user-attachments/assets/0f54495f-d5c0-4a81-9d62-1e77775be796" />

-celular

<img width="425" height="522" alt="image" src="https://github.com/user-attachments/assets/5daf31ab-f3b4-4366-90cf-5506912d9807" />


***Haz un diagrama que explique cómo se comunicarán los diferentes componentes del sistema.***

<img width="414" height="568" alt="image" src="https://github.com/user-attachments/assets/745e5c9f-35f7-43a8-a61c-a6a1ea639fac" />


## APPly

***1. Documenta todo el proceso de construcción.***

-Lo primero para empezar con el proyecto fue buscar en unidades pasadas el duncionamiento del micro:bit, para repasar y verificarcomo hacer que fucione correctamente.

- Me di cuenta que era mas sencillo si en vez de hacer que aparecieran imagenes de frutas era mejor usar emojis porq ya están implementados y no toca agregarlos.

- Ahora busue el como descargar la cancion y ver como funciona a la hora de crear la pagina. 

- Haciendo varias pruebas y viendo en la consola del desktop ya de forma online, no me deja iniciar el programa por la utilizacion de audio y no encuentro la manera de arreglarlo.

- intente mucho y hasta use ia para comprender qu epasaba con los errores, pero aun asi no funciono nada. 




***2. Incluye todos los códigos: servidor, cliente móvil, cliente de escritorio y micro:bit.***

micro:bit 

```py

from microbit import *
import bluetooth
import uart

uart.init(baudrate=115200)

while True:
    if button_a.was_pressed():
        uart.write("A\n")
    if button_b.was_pressed():
        uart.write("B\n")
    sleep(100)
```

server

```JS
const express = require('express');
const http = require('http');
const socketIO = require('socket.io');
const SerialPort = require('serialport');
const Readline = require('@serialport/parser-readline');

const app = express();
const server = http.createServer(app);
const io = socketIO(server);
const port = 3000;

// Cambia COM3 por el puerto donde esté conectado tu micro:bit
const serial = new SerialPort.SerialPort({ path: 'COM3', baudRate: 115200 });
const parser = serial.pipe(new Readline({ delimiter: '\r\n' }));

app.use(express.static('public'));

io.on('connection', (socket) => {
    console.log('New client connected');

    // Enviar datos del micro:bit al cliente
    parser.on('data', (data) => {
        console.log('From micro:bit:', data);
        io.emit('message', { type: 'microbit', value: data });
    });

    socket.on('message', (message) => {
        console.log('Received message =>', message);
        socket.broadcast.emit('message', message);
    });

    socket.on('disconnect', () => {
        console.log('Client disconnected');
    });
});

server.listen(port, '0.0.0.0', () => {
  console.log(`Server listening on http://0.0.0.0:${port}`);
});
```

desktop

```js
let socket;
let fruits = [];
let fruitCount = 1;
let stars = [];
let song;
let isPlaying = false;
let playButton;

// Detectar si es escritorio (desktop)
let isDesktop = !/Mobi|Android/i.test(navigator.userAgent);

function setup() {
  createCanvas(windowWidth, windowHeight);
  socket = io();

  // Solo crear el botón de música si es desktop
  if (isDesktop) {
    playButton = createButton('▶️ Reproducir música');
    playButton.position(20, 20);
    playButton.style('font-size', '18px');
    playButton.mousePressed(toggleMusic);
  }

  // Generar estrellas del fondo
  for (let i = 0; i < 200; i++) {
    stars.push({
      x: random(width),
      y: random(height),
      size: random(1, 3),
      speed: random(0.2, 1)
    });
  }

  // Escuchar eventos desde socket.io
  socket.on("message", (data) => {
    if (data.type === "fruit") {
      for (let i = 0; i < fruitCount; i++) {
        fruits.push({
          x: data.x + random(-50, 50),
          y: data.y + random(-50, 50),
          emoji: random(["🍎", "🍌", "🍓", "🍉", "🍍", "🍇"])
        });
      }
    }

    if (data.type === "microbit") {
      if (data.value === "A") fruitCount++;
      if (data.value === "B" && fruitCount > 1) fruitCount--;
      console.log("Fruit count:", fruitCount);
    }
  });
}

function draw() {
  background(10, 10, 30);

  // Dibujar estrellas en movimiento
  for (let s of stars) {
    fill(255);
    noStroke();
    circle(s.x, s.y, s.size);
    s.y += s.speed;
    if (s.y > height) s.y = 0;
  }

  // Mostrar frutas
  textSize(40);
  for (let f of fruits) {
    text(f.emoji, f.x, f.y);
    f.y += 0.3;
  }

  // HUD
  fill(255);
  textSize(18);
  text(`Frutas por toque: ${fruitCount}`, 20, height - 30);
}

// Solo se ejecuta en desktop
function toggleMusic() {
  if (!isDesktop) return; // Seguridad adicional

  // Habilita contexto de audio
  userStartAudio();

  if (!song) {
    // Carga el sonido solo cuando el usuario lo pide
    song = loadSound('passionfruit.mp3',
      () => {
        song.loop();
        isPlaying = true;
        playButton.html('🎵 Música reproduciéndose');
        console.log('Audio cargado correctamente.');
      },
      (err) => {
        console.error('Error al cargar audio:', err);
      }
    );
  } else if (!isPlaying) {
    song.loop();
    isPlaying = true;
    playButton.html('🎵 Música reproduciéndose');
  } else {
    song.stop();
    isPlaying = false;
    playButton.html('▶️ Reproducir música');
  }
}
```

mobile 

``` js
let socket;
let lastTouchX = null; 
let lastTouchY = null; 
const threshold = 5;

function setup() {
    createCanvas(300, 400);
    background(220);
    socket = io();

    socket.on('connect', () => {
        console.log('Connected to server');
    });

    socket.on('message', (data) => {
        console.log(`Received message: ${data}`);
    });

    socket.on('disconnect', () => {
        console.log('Disconnected from server');
    });

    socket.on('connect_error', (error) => {
        console.error('Socket.IO error:', error);
    });
}

function draw() {
    background(0);
    fill(255);
    textAlign(CENTER);
    text("Toca para generar frutas 🍉", width/2, height/2);
}

function touchStarted() {
    let touchData = { type: "fruit", x: mouseX, y: mouseY };
    socket.emit("message", touchData);
    return false;
}

```


## Mi nota es 3.0 (pero cualquier punto es cariño y se intento hasta el final)

Solo logré completar una actividad al 100%, pero en la segunda intenté avanzar y hacer todo lo que más pude. Entiendo que la nota solo se asigna cuando la actividad está completamente terminada, sin embargo, quiero resaltar que hice mi mayor esfuerzo por desarrollarla lo mejor posible dentro del tiempo y las condiciones que tuve.


🎃🎄👻¡¡¡Gracias profe por todo!!!🎃🎄👻





