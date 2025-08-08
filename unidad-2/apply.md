# Unidad 2


## 🛠 Fase: Apply

### 💣Actividad 04💣

Diseño de la lógica de una bomba temporizada

<img width="637" height="680" alt="image" src="https://github.com/user-attachments/assets/81af2160-66f8-4b6b-a457-54d9018ac029" />



### 🧨Actividad 05🧨

``` py
from microbit import *
import utime

STATE_BOMB_DESARMADA = 0
STATE_BOMB_ARMADA = 1
STATE_BOMB_EXPLOTA = 2

current_STATE = STATE_BOMB_DESARMADA
start_time = 0

tiempo_normal = 20000
tiempo_min = 10000
tiempo_max = 60000

pin_touch = pin_logo

esperando_activar_bomba = False
momento_shake = 0

while True:
    if current_STATE == STATE_BOMB_DESARMADA:
        if esperando_activar_bomba:
            display.show(Image.YES)
            if utime.ticks_diff(utime.ticks_ms(), momento_shake) >= 2000:
                current_STATE = STATE_BOMB_ARMADA
                start_time = utime.ticks_ms()
                esperando_activar_bomba = False
        else:
            display.show(str(tiempo_normal // 1000))

            if button_a.was_pressed():
                if tiempo_normal < tiempo_max:
                    tiempo_normal += 1000

            if button_b.was_pressed():
                if tiempo_normal > tiempo_min:
                    tiempo_normal -= 1000

            if accelerometer.was_gesture("shake"):
                esperando_activar_bomba = True
                momento_shake = utime.ticks_ms()

    elif current_STATE == STATE_BOMB_ARMADA:
        elapsed_ms = utime.ticks_diff(utime.ticks_ms(), start_time)
        tiempo_restante = tiempo_normal - elapsed_ms

        if tiempo_restante >= 0:
            display.show(str(tiempo_restante // 1000))
        else:
            current_STATE = STATE_BOMB_EXPLOTA
            display.show(Image.SKULL)

    elif current_STATE == STATE_BOMB_EXPLOTA:
        if pin_touch.is_touched():
            tiempo_normal = 20000
            current_STATE = STATE_BOMB_DESARMADA
            display.show(str(tiempo_normal // 1000))

```

***Vectores de Prueba*** 
- Cuando se inica debe de salir los numeros de tiempo 
- Cuando se presione a o b debe mostrar el numero nuevo
- Cuando se haga el sake debe salir la imagen del check
- Luego del check debe salir el conteo regresivo con los numeros en pantalla
- Cuando llegue a 0 debe salir la imagen de skull
- Cuando se presione el toiuch volver a iniciar 

