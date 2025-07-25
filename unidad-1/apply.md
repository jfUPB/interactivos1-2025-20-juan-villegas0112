# Unidad 1

## 🛠 Fase: Apply

### Actividad 05

#### Inputs

##### micro:bit
Botón A:

Si el usuario presiona el botón A, se considera una entrada física.



##### p5.js
Botón de conexión:

El botón "Connect to micro:bit" inicia o detiene la conexión serial entre la micro:bit y la interfaz web.

#### Outputs

Color del rectángulo:

Rojo: si se presiona el botón A ('A')

Verde: si no se presiona ('N')



### Actividad 06

#### p5.js

``` js
let port;
let connectBtn;
let connectionInitialized = false;


function setup() {
  createCanvas(400, 400);
  background(220);
  port = createSerial();
  connectBtn = createButton("Connect to micro:bit");
  connectBtn.position(80, 300);
  connectBtn.mousePressed(connectBtnClick);
  circleX = width / 2;
}

function draw() {
  background(220);

  if (port.opened() && !connectionInitialized) {
    port.clear(); 
    connectionInitialized = true;
  }

  
  if (port.availableBytes() > 0) {
    let dataRx = port.read(1); 

    if (dataRx === "A") {
      circleX -= 30; 
    } else if (dataRx === "B") {
      circleX += 30; 
    }

    
    circleX = constrain(circleX, 0, width);
  }

  
  fill("#4CAF50");
  noStroke();
  ellipse(circleX, height / 2, 50, 50);

  
  if (!port.opened()) {
    connectBtn.html("Connect to micro:bit");
  } else {
    connectBtn.html("Disconnect");
  }
}

function connectBtnClick() {
  if (!port.opened()) {
    port.open("MicroPython", 115200);
    connectionInitialized = false;
  } else {
    port.close();
  }
}
```

#### micro:bit


``` py

while True:

    if button_a.is_pressed():
        uart.write('A')
        sleep(500)
    if button_b.is_pressed():
        uart.write('B')
        sleep(500)
    else:
        uart.write('N')

    sleep(100)
```


