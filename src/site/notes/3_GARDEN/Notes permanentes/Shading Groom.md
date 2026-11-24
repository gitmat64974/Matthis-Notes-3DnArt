---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Shading Groom/","tags":["note_permanente"],"ctime":"2026-03-22T12:15:23.676+01:00","mtime":"2026-06-01T12:03:18.780+02:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/GROOM]]"],"source":["#cours [[Cours de lighting rendu ESMA]]"],"Projets":null,"tags":["note_permanente"],"creation date":"2025-03-05","aliases":null}}
---


## La note 

renderman : pxrsurface. Double sided avec un peu de transmit 

utilisez un pxr Vary en mode primvar avec "id_XP" comme variable
- Baisser la hue, sat et luminance (0) et augmenter le gamma (surtout lui qui est intéressant)
- On peut combiner à des pxr blend, se servir du vary comme d'un masque etc

La variable "scalpST" Pour appliquer une texture provenant des UVs du scalp utilisez un PXrmanifold2D dans un texture


![Branchement_shader_color_Xgen02.png](/img/user/Pi%C3%A8ces%20jointes/Branchement_shader_color_Xgen02.png)

Note : ramp basic 

Faire des petits poils blancs : 

Mettre un vary avec du noir en input
Luminance et gamma à fond, en additif
Brancher le result r dans le top A d'un blend

Baisser la probability dans le vary pour faire du blanc que sur certains poils
On se sert de ce vary donc comme masque -> top color quasi blanc et texture de base dans bottom RGB 

-
Speculaires : 
On peut mettre de l'edge color
et pourquoi pas un peu de rough specular en artistic (juste face color)

-
Voir aussi le pxrMarschnerHair


-

#### Rendering

descriptionShape node -> Render Density Multiplier

Lets you increase or decrease the density of the hairs for rendering. This changes the density of the hairs at render time only. The resulting hair density does not appear in scene view.


## Références



## Liens 




