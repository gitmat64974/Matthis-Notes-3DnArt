---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Gimbal lock/","tags":["note_permanente"],"ctime":"2026-09-22T09:47:09.047+02:00","mtime":"2026-09-22T08:06:20.702+02:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/HOUDINI]]","[[3_GARDEN/MOCs/MODELISATION]]","[[3_GARDEN/MOCs/ANIMATION]]","[[3_GARDEN/MOCs/RIG]]"],"source":null,"Projets":null,"tags":["note_permanente"],"creation date":null,"aliases":null}}
---


[[3_GARDEN/Notes permanentes/MOC\|MOC]] : [[3_GARDEN/MOCs/ANIMATION\|ANIMATION]] [[3_GARDEN/MOCs/3D\|3D]]
Source : #cours [[3_GARDEN/Notes littéraires/Cours d'animation ESMA\|Cours d'animation ESMA]]
Projet : 
Tags : #note_permanente 
Date : 2024-11-20

## La note 


Le gimbal lock cause des rotations non désirées sur les objets en animation 3D en fonction de comment les axes sont parentés entre eux et en fonction de comment l'ordinateur calcule les rotations : en 3D ce sont des rotations euler. 
*Se mettre en mode gimbal de rotation dans MAYA pour voir*
Le gimbal lock arrive lorsque 2 axes ont la même orientation, on perd un axe : 

![Capture d'écran 2024-11-20 144353.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202024-11-20%20144353.png)

La rotation ne se fait pas de manière droite car il y a à bouger 2 axes pour effectuer la rotation demandée : 

![Capture d'écran 2024-11-20 144341.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202024-11-20%20144341.png)

#### Avec une caméra

| ![Capture d'écran 2024-11-20 145108.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202024-11-20%20145108.png) | ![Capture d'écran 2024-11-20 145119.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202024-11-20%20145119.png) |
| ------------------------------------------ | ------------------------------------------ |
==**Le mode local rotation axis est juste un guide, l'ordinateur calcule avec la rotation euler**==



## Références



## Liens 




