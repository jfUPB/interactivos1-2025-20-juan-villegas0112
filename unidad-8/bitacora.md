
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







