# Unidad 2

## 🔎 Fase: Set + Seek

### 🛵Actividad 01🛵
``` Py 
from microbit import *
import utime

class Pixel:
    def __init__(self,pixelX,pixelY,initState,interval):
        self.state = "Init"
        self.startTime = 0
        self.interval = interval
        self.pixelX = pixelX
        self.pixelY = pixelY
        self.pixelState = initState

    def update(self):

        if self.state == "Init":
            self.startTime = utime.ticks_ms()
            self.state = "WaitTimeout"
            display.set_pixel(self.pixelX,self.pixelY,self.pixelState)

        elif self.state == "WaitTimeout":
            if utime.ticks_diff(utime.ticks_ms(),self.startTime) > self.interval:
                self.startTime = utime.ticks_ms()
                if self.pixelState == 9:
                    self.pixelState = 0
                else:
                    self.pixelState = 9
                display.set_pixel(self.pixelX,self.pixelY,self.pixelState)

pixel1 = Pixel(0,0,0,1000)
pixel2 = Pixel(4,4,0,500)

while True:
    pixel1.update()
    pixel2.update()
``` 

***Describe detalladamente cómo funciona este ejemplo.***

Este codigo permite crear la aparicion de dos luces en el tablero del micro:bit, haciendo que se enciendan y se apaguen de forma especifica cada uno; se prenden y apagan con diferente velocidad y ubicacion.

🔦Luz 1 ó pixel1: Esta ubicado en la esquina superior izquierda (0,0). Y esta misma cambia cada 1000 milisegundos; se prende y apaga a esa velocidad.

🔦Luz 2 ó pixel2: Esta ubicado en la esquina inferior derecha (4,4). Y esta misma cada 500 milisegundos; se prende y apaga a esa velocidad.

***¿Cuáles son los estados en el programa?***

Hay 2 estados que cada Pixel puede tener:

Init — El pixel esta iniciando. Aquí prende o apaga la luz por primera vez y recuerda el tiempo.

WaitTimeout  — El pixel esta esperando a que pase el tiempo para prender o apagar la luz otra vez.

***¿Cuáles son los eventos/inputs en el programa?***

Como este programa no tiene botones ni sensores, hace que los eventos sean el paso del tiempo. Esto quiere decir que cuando pasa el tiempo suficiente (500 ms o 1000 ms), se activa el evento de encender el pixel.

***¿Cuáles son las acciones en el programa?***

- Encender o apagar la luz en una posición de la pantalla.

- Recordar el momento en que cambió la luz (con startTime).

- Alternar entre 0 (apagado) y 9 (encendido).

### 🚦Actividad 02🚦

``` py
from microbit import *
import utime

class Semaforo:
    def __init__(self):
        self.estado = "Rojo"
        self.tiempo_inicio = utime.ticks_ms()

    def encender_led(self, x, y):
        display.clear()
        display.set_pixel(x, y, 9)

    def actualizar(self):
        ahora = utime.ticks_ms()
        tiempo_pasado = utime.ticks_diff(ahora, self.tiempo_inicio)

        if self.estado == "Rojo":
            self.encender_led(2, 0)  # LED superior (Rojo)
            if tiempo_pasado > 3000:
                self.estado = "Verde"
                self.tiempo_inicio = ahora

        elif self.estado == "Verde":
            self.encender_led(2, 4)  # LED inferior (Verde)
            if tiempo_pasado > 3000:
                self.estado = "Amarillo"
                self.tiempo_inicio = ahora

        elif self.estado == "Amarillo":
            self.encender_led(2, 2)  # LED medio (Amarillo)
            if tiempo_pasado > 1000:
                self.estado = "Rojo"
                self.tiempo_inicio = ahora

# Crear el semáforo
mi_semaforo = Semaforo()

# Bucle principal
while True:
    mi_semaforo.actualizar()

```
***Estados***:

🔴Rojo: LED en (2,0)

🟡Amarillo: LED en (2,2)

🟢Verde: LED en (2,4)

***Eventos (inputs)***:

Tiempo transcurrido desde que comenzó el estado actual.

***Acciones***:

Mostrar un LED según el estado.



Esperar un tiempo determinado.



Cambiar de estado al siguiente y reiniciar el temporizador.



