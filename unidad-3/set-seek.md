# Unidad 3

## 🔎 Fase: Set + Seek

### Actividad 01

``` py
from microbit import *
import utime

class Semaforo:
    def __init__(self,tr,ta,tv,col):
        self.tr = tr
        self.ta = ta
        self.tv = tv
        self.col = col
        self.startTime = utime.ticks_ms()
        display.set_pixel(self.col,0,9)
        self.STATE = "WAITINRED"

    def update(self):
        if self.STATE == "WAITINRED":
           if utime.ticks_diff(utime.ticks_ms(),self.startTime) >= self.tr:

               display.set_pixel(self.col,0,0)
               display.set_pixel(self.col,1,9)
               self.startTime = utime.ticks_ms()
               self.STATE == "WAITINYELLOW"

        elif self.STATE == "WAITINYELLOW":
            if utime.ticks_diff(utime.ticks_ms(),self.startTime) >= self.ta:

               display.set_pixel(self.col,1,0)
               display.set_pixel(self.col,2,9)
               self.startTime = utime.ticks_ms()
               self.STATE == "WAITINGREEN"

        elif self.STATE == "WAITINGREEN":
            if utime.ticks_diff(utime.ticks_ms(),self.startTime) >= self.tv:

               display.set_pixel(self.col,2,0)
               display.set_pixel(self.col,0,9)
               self.startTime = utime.ticks_ms()
               self.STATE == "WAITINRED"
    
    
    

semaforo1 = Semaforo(5000, 2000, 3000, 0)
semaforo2 = Semaforo(3000, 1000, 2000, 2)
semaforo3 = Semaforo(4000, 3000, 2000, 4)

while True:
    semaforo1.update()
    semaforo2.update()
    semaforo3.update()

```
### Actividad 02


