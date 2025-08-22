# Unidad 3


## 🛠 Fase: Apply

### 🦎Actividad 06🦎

***1. El código fuente de la bomba en p5.js. Debes utilizar la técnica de máquina de estados y la biblioteca de manejo de serial que estamos trabajando en el curso.***

``` javascript
let bombTask;

function setup() {
  createCanvas(400, 400);
  textAlign(CENTER, CENTER);
  textSize(32);

  bombTask = new BombTask();
}

function draw() {
  background(220);
  bombTask.update();
}


class BombTask {
  constructor() {
    this.PASSWORD = ['A','B','A'];
    this.key = new Array(this.PASSWORD.length).fill('');
    this.keyindex = 0;
    this.count = 20;
    this.startTime = millis();
    this.state = 'CONFIG';
  }

  update() {
    if (this.state === 'CONFIG') {
      fill(0);
      text("CONFIG: " + this.count, width/2, height/2);

    } else if (this.state === 'ARMED') {
      // cada segundo bajar count
      if (millis() - this.startTime > 1000) {
        this.startTime = millis();
        this.count -= 1;
        if (this.count <= 0) {
          this.count = 0;
          this.state = 'EXPLODED';
        }
      }
      fill(255,0,0);
      text("ARMED: " + this.count, width/2, height/2);

    } else if (this.state === 'EXPLODED') {
      fill(255,0,0);
      text("💀 BOOM!", width/2, height/2);
      textSize(20);
      text("(press L to reset)", width/2, height/2+50);
      textSize(32);
    }
  }

  pressKey(k) {
    if (this.state === 'CONFIG') {
      if (k === 'A') {
        this.count = min(this.count + 1, 60);
      }
      if (k === 'B') {
        this.count = max(this.count - 1, 10);
      }
      if (k === 'S') { // S = shake
        this.startTime = millis();
        this.state = 'ARMED';
      }
    }
    else if (this.state === 'ARMED') {
      if (k === 'A') {
        this.key[this.keyindex] = 'A';
        this.keyindex++;
      }
      if (k === 'B') {
        this.key[this.keyindex] = 'B';
        this.keyindex++;
      }

      if (this.keyindex === this.key.length) {
        let passIsOK = true;
        for (let i=0; i<this.key.length; i++) {
          if (this.key[i] !== this.PASSWORD[i]) {
            passIsOK = false;
            break;
          }
        }

        if (passIsOK) {
          this.count = 20;
          this.keyindex = 0;
          this.key.fill('');
          this.state = 'CONFIG';
        } else {
          this.keyindex = 0;
          this.key.fill('');
        }
      }
    }
    else if (this.state === 'EXPLODED') {
      if (k === 'L') { // touch simulado con tecla L
        this.count = 20;
        this.startTime = millis();
        this.state = 'CONFIG';
      }
    }
  }
}

// Teclas
function keyPressed() {
  let k = key.toUpperCase();
  // A, B = botones
  // S = shake
  // L = touch
  if (['A','B','S','L'].includes(k)) {
    bombTask.pressKey(k);
  }
}
```

### 🦜Actividad 07🦜

1. Código p5.js

``` py
let bombTask;
let serial; 
let portName = "COM3"; // puerto de tu micro:bit

function setup() {
  createCanvas(400, 400);
  textAlign(CENTER, CENTER);
  textSize(32);

  bombTask = new BombTask();

  serial = new p5.SerialPort();
  serial.list();
  serial.open(portName);

  serial.on('data', serialEvent);
}

function draw() {
  background(220);
  bombTask.update();
}

function serialEvent() {
  let data = serial.readLine().trim();
  if (data.length > 0) {
    let k = data.toUpperCase();
    if (['A','B','S','L'].includes(k)) {
      bombTask.pressKey(k);
    }
  }
}

class BombTask {
  constructor() {
    this.PASSWORD = ['A','B','A'];
    this.key = new Array(this.PASSWORD.length).fill('');
    this.keyindex = 0;
    this.count = 20;
    this.startTime = millis();
    this.state = 'CONFIG';
  }

  update() {
    if (this.state === 'CONFIG') {
      fill(0);
      text("CONFIG: " + this.count, width/2, height/2);

    } else if (this.state === 'ARMED') {
      if (millis() - this.startTime > 1000) {
        this.startTime = millis();
        this.count -= 1;
        this.startTime = millis();
        if (this.count <= 0) {
          this.count = 0;
          this.state = 'EXPLODED';
        }
      }
      fill(255,0,0);
      text("ARMED: " + this.count, width/2, height/2);

    } else if (this.state === 'EXPLODED') {
      fill(255,0,0);
      text("💀 BOOM!", width/2, height/2);
      textSize(20);
      text("(press L to reset)", width/2, height/2+50);
      textSize(32);
    }
  }

  pressKey(k) {
    if (this.state === 'CONFIG') {
      if (k === 'A') this.count = min(this.count + 1, 60);
      if (k === 'B') this.count = max(this.count - 1, 10);
      if (k === 'S') {
        this.startTime = millis();
        this.state = 'ARMED';
      }
    }
    else if (this.state === 'ARMED') {
      if (k === 'A' || k === 'B') {
        this.key[this.keyindex] = k;
        this.keyindex++;
      }

      if (this.keyindex === this.key.length) {
        let passIsOK = true;
        for (let i=0; i<this.key.length; i++) {
          if (this.key[i] !== this.PASSWORD[i]) {
            passIsOK = false;
            break;
          }
        }

        if (passIsOK) {
          this.count = 20;
          this.keyindex = 0;
          this.key.fill('');
          this.state = 'CONFIG';
        } else {
          this.keyindex = 0;
          this.key.fill('');
        }
      }
    }
    else if (this.state === 'EXPLODED') {
      if (k === 'L') {
        this.count = 20;
        this.startTime = millis();
        this.state = 'CONFIG';
      }
    }
  }
}


function keyPressed() {
  let k = key.toUpperCase();
  if (['A','B','S','L'].includes(k)) {
    bombTask.pressKey(k);
  }
}

```

2. Enlace al editor de p5.js con tu código.

https://editor.p5js.org/juan-villegas0112/sketches/v70CI1WWO

3. Código del micro:bit.

``` py
from microbit import *


while True:
    if button_a.was_pressed():
        uart.write("A\n")   # Enviar tecla A

    if button_b.was_pressed():
        uart.write("B\n")   # Enviar tecla B

    if accelerometer.was_gesture("shake"):
        uart.write("S\n")   # Enviar tecla S (shake)

    if pin_logo.is_touched():
        uart.write("L\n")
``` 


