# Unidad 2


## 🛠 Fase: Apply

### 💣Actividad 04💣

Diseño de la lógica de una bomba temporizada

<img width="865" height="833" alt="image" src="https://github.com/user-attachments/assets/f550e0a9-3dcd-48a8-97bf-468e553a137d" />


### 🧨Actividad 05🧨

``` py
from microbit import *
import utime

# Definimos los estados de la bomba
STATE_DESARMADA = 0  # modo configuración
STATE_ARMADA = 1     # cuenta regresiva
STATE_EXPLOTADA = 2  # bomba explotó

# Variables para tiempo
tiempo = 20  # tiempo inicial en segundos
min_tiempo = 10
max_tiempo = 60

current_state = STATE_DESARMADA
start_time = 0

while True:
    if current_state == STATE_DESARMADA:
        # Mostrar tiempo actual en pantalla (como número)
        display.show(str(tiempo))
        
        # Ajustar tiempo con botones
        if button_a.was_pressed():
            if tiempo < max_tiempo:
                tiempo += 1
        if button_b.was_pressed():
            if tiempo > min_tiempo:
                tiempo -= 1
        
        # Si hago shake, armo la bomba
        if accelerometer.was_gesture("shake"):
            current_state = STATE_ARMADA
            start_time = utime.ticks_ms()
    
    elif current_state == STATE_ARMADA:
        # Calcular tiempo que ha pasado en milisegundos
        elapsed_ms = utime.ticks_diff(utime.ticks_ms(), start_time)
        tiempo_restante = tiempo - elapsed_ms // 1000  # pasar a segundos
        
        # Mostrar el tiempo restante
        if tiempo_restante >= 0:
            display.show(str(tiempo_restante))
        else:
            # Tiempo llegó a 0, bomba explota
            current_state = STATE_EXPLOTADA
            display.show(Image.SKULL)  # imagen de explosión (simulada)
            # Activar el buzzer o sonido (si tienes uno conectado)
            # Aquí solo parpadeamos la pantalla rápido
            for _ in range(10):
                display.show(Image.SKULL)
                sleep(200)
                display.clear()
                sleep(200)
    
    elif current_state == STATE_EXPLOTADA:
        # Esperar a que toque el botón touch para reiniciar
        if pin_touch.is_touched():
            tiempo = 20  # reiniciar tiempo a 20 segundos
            current_state = STATE_DESARMADA
            display.show(str(tiempo))

```
