---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Explosion en RBD/","tags":["note_permanente"],"dg-note-properties":{"MOC":["[[RBD Simulation Houdini]]","[[HOUDINI]]"],"source":null,"Projets":null,"tags":["note_permanente"],"creation date":"2026-01-26","aliases":null}}
---

## La note 

Dans le subnet de dynamique du [[3_GARDEN/Notes permanentes/RBD Bullet Solver|RBD Bullet Solver]] :

- **Pop attract** : node qui attire ou repousse en fonction du placement d’un point
- **Pop force** : Pour ajouter du noise / du chaos (mettre une très forte amplitude)

#### Donner un impulsion à une frame précise

On va utiliser une expression très simple dans le paramètre d'activation du pop attract : @Frame==numero de la frame. Pour que ce soit plus propre : 

- On peut créer un paramètre custom où on veut (null, ou dans le rbd bullet solver) en integer pour définir la frame de l’explosion
- Copy parameter → Dans le paramètre d’activation des nodes POP (attract, force etc) : @Frame==paste relative reference

(_On peut également appliquer cette petite expression sur des paramètres d’activation dans les rbd configure pour activer des configs dynamiquement_)


## Références



> [!example]- Flashcards
> ...




## Liens 




