# Imagerie numérique et carte microbit

## 1. Montage de base

On peut utiliser la carte microbit pour faire de l'imagerie numérique. On va essayer d'utiliser la carte microbit pour afficher de la couleur.


Le premier montage de base va nous permettre de tester le fonctionnement de la carte microbit.
Il nous faut :

- une carte microbit
- un câble USB pour relier la carte microbit à l'ordinateur
- un ordinateur où on va ouvrir l'éditeur en ligne de la carte microbit : https://python.microbit.org/v/3
- une simple LED (diode électroluminescente) pour tester le montage

1. Connecter la carte microbit à l'ordinateur avec le câble USB
2. connecter la LED sur la broche 0 de la carte microbit à l'aide d'un fil de connexion
3. Ouvrir l'éditeur en ligne de la carte microbit : https://python.microbit.org/v/3
4. Remplacer le programme par le programme suivant :
   
```python
from microbit import *

while True:
    pin0.write_digital(1)
    sleep(1000)
    pin0.write_digital(0)
    sleep(1000)
```

5. Cliquer sur le bouton "Send to micro:bit" pour envoyer le programme sur la carte microbit
6. Passez les étapes de téléchargement du programme sur la carte microbit
7. Votre LED doit s'allumer et s'éteindre toutes les secondes

## 2. Montage pour afficher de la couleur

Pour afficher de la couleur on va utiliser une bande de LED.
Il nous faut connecter la bande de LED sur la broche 0 de la carte microbit à la place de la LED.

1. Connecter la bande de LED sur la broche 0 de la carte microbit à la place de la LED

2. On va utiliser le programme suivant pour allumer la bande de LED :

```python
from microbit import *
from neopixel import *

# Fonctions
def allumer_leds(bande_led):
    for i in range(30):
        # on defini la couleur de la led actuelle
        color = ...
        bande_led[i] = color
        bande_led.show()
        sleep(100)

# Programme principal
bande_led = NeoPixel(pin0, 30)
allumer_leds(bande_led)
sleep(2000)
bande_led.clear()
```

Que fait ce programme ?

3. Compléter le programme pour allumer la bande de LED en rouge

4. Tester le programme

5. Essayez de changer la couleur de la bande de LED

## 3. A vous de jouer

1. On veut faire une fonction pour allumer la bande quand on appuie sur le bouton A de la carte microbit. Compléter le programme suivant :

```python
from microbit import *
from neopixel import *

# Fonctions
def allumer_leds(bande_led):
    for i in range(30):
        # on defini la couleur de la led actuelle
        color = ...
        bande_led[i] = color
        bande_led.show()
        sleep(100)

# Programme principal
bande_led = NeoPixel(pin0, 30)

while True:
    if ... :
        allumer_leds(bande_led)
    else:
        bande_led.clear()
```

2. On voudrait maintenant allumer la bande de LED en rouge quand on appuie sur le bouton A et en bleu quand on appuie sur le bouton B. Compléter le programme suivant :

```python
from microbit import *
from neopixel import *

# Fonctions
def allumer_leds(bande_led, couleur):
    for i in range(30):
        # on defini la couleur de la led actuelle
        color = ...
        bande_led[i] = color
        bande_led.show()
        sleep(100)

# Programme principal
bande_led = NeoPixel(pin0, 30)

while True:
    if ... :
        allumer_leds(bande_led, ...)
    elif ... :
        allumer_leds(bande_led, ...)
    else:
        bande_led.clear()
```

3. Enfin, on va essayer de faire une fonction pour allumer la bande de LED avec des couleurs aléatoires. Compléter le programme suivant :

```python
from microbit import *
from neopixel import *
from random import randint

# Fonctions
def allumer_leds(bande_led):
    for i in range(30):
        # on defini la couleur de la led actuelle
        color = ...
        bande_led[i] = color
        bande_led.show()
        sleep(100)

# Programme principal
bande_led = NeoPixel(pin0, 30)

actif = False
while True:
    if button_a.is_pressed():
        if not actif:
            actif = True
            allumer_leds(bande_led)
    else:
        bande_led.clear()
        actif = False
```