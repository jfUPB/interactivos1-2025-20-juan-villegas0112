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




