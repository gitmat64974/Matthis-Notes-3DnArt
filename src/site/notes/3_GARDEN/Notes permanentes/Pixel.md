---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Pixel/","tags":["note_permanente"],"ctime":"2026-03-21T20:44:55.073+01:00","mtime":"2026-04-24T17:43:18.909+02:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/COMPOSITING]]"],"source":["[[3_GARDEN/Notes littéraires/3e et 4e cours compositing esma 3d2]]"],"Projets":null,"tags":["note_permanente"],"creation date":"2025-05-12","aliases":null}}
---


## La note

La plupart des images numériques que l’on manipule ont 3 Couches (=Channels) pour décrire la couleur d’une image. Chacune de ces Couches est en nuances de gris, qui codera la valeur contenue dans chaque pixel: 

![Pasted image 20241108070511.png](/img/user/Pi%C3%A8ces%20jointes/Pasted%20image%2020241108070511.png)

> [!info] Alpha
> L’information d’Opacité des images numériques se trouve dans une quatrième Couche, appellée ‘Alpha’ — ou ‘A’. Les données contenues sont décrites dans une échelle de gris entre 0 et 1.
> ==**⚠️ Les formats .JPG & .JPEG ne contiennent pas de channel Alpha — Privilégier donc les formats .EXR, .TIF, .TIFF & .PNG ⚠️**==

Ensuite, ces valeurs sont ajoutées par synthèse additive 

#### Pixel Depth

L’unité de valeur de la donnée numérique s’appelle un ‘Digit’, qui a une valeur de 0 ou de 1. Les digits sont regroupés par groupes, appelés ‘Bit’ — On peut définir la ‘Pixel Depth’ comme étant la quantité de Digits qui forment un Bit.

> [!NOTE]+ Pixel depth en fonction des Maps d’export : 
> Scalar : 32 Bits 
> Color : 8bits (16 bits si color correction par dessus)


![Pasted image 20241108070739.png](/img/user/Pi%C3%A8ces%20jointes/Pasted%20image%2020241108070739.png)

![Capture d'écran 2024-11-08 070834.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202024-11-08%20070834.png)

#### Systèmes colorimétriques

![Pasted image 20241108071302.png](/img/user/Pi%C3%A8ces%20jointes/Pasted%20image%2020241108071302.png)


## Références 

## Liens 
