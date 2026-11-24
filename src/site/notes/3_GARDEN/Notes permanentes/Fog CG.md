---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Fog CG/","tags":["note_permanente"],"ctime":"2026-03-22T12:15:22.211+01:00","mtime":"2026-11-11T15:17:19.190+01:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/3D|CG]]","[[3_GARDEN/MOCs/COMPOSITING]]"],"source":["[[Kickstart your VFX Career pdf]] / [[Cours 2, 4, 5 et 6 de Gael Bourdeu, remplaçant prof Lighting 3D2]]"],"Projets":null,"tags":["note_permanente"],"creation date":"2025-02-27","aliases":null}}
---


## La note 

![Capture d'écran 2025-02-27 092221.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202025-02-27%20092221.png)
![Capture d'écran 2025-02-27 092226.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202025-02-27%20092226.png)


> [!abstract] Pourquoi du fog en CG
> L'ajout de volume dans un rendu peut jouer un rôle essentiel, que ce soit pour des raisons esthétiques, narratives ou techniques.
> 
> Il peut venir soutenir une intention artistique ou émotionnelle comme évoquer une scène mystérieuse, dangereuse ou onirique par exemple.
> 
> Il contribue également au réalisme de l'image, en recréant des effets tels que la perspective atmosphérique, en adoucissant ou en modifiant la diffusion de la lumière. Il peut aussi être à l'origine de phénomènes visuels comme les God Rays.
> 
> Enfin, le volume peut aussi améliorer la lisibilité d'une image en accentuant la séparation des différents plans, aidant de ce fait, à guider le regard du spectateur.

#### En comp, la depth pass

![Capture d'écran 2025-02-27 092632.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202025-02-27%20092632.png)

En rendu 3D, on peut générer une depth pass, plus les pixels sont proches de la caméra, plus ils seront foncés. 

Tip : Dans Nuke, mettre un grade et le multiplier par 0.0001 pour pouvoir voir la map et l'utiliser, sinon elle est blanche

#### Tips lighting volume 3D

Là, il est très utile et recommandé d'utiliser le light linking. 
On va essayer de privilégier seulement une ou deux lights qui éclairent le volume et surtout pas d'IBL

#### Rendre un volume en 3D en l'isolant dans un AOV spécifique

Faire un volume en 3D (pxrVolume si c'est renderman par exemple) 

> [!abstract]
> Pour le compositing, l'idéal est d'isoler le volume dans un AOV spécifique.
> Cela permet d'avoir un contrôle total sur le volume en post-production (intensité, couleur) sans affecter l'image principale (Beauty).

| ![Capture d'écran 2026-02-09 000130.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202026-02-09%20000130.png) | ![Pasted image 20260209000138.png](/img/user/Pi%C3%A8ces%20jointes/Pasted%20image%2020260209000138.png) |
| ------------------------------------------ | ------------------------------------ |

###### Setup du RenderLayer "Volume"

* Dans la fenêtre RenderLayers de Maya, créez un renderlayer avec tout sauf le volume, puis créez un RenderLayer dédié au volume.
* Au sein de ce layer, créez une collection et ajoutez-y la géométrie du volume.
* Pour les autres éléments de la scène (environnement, personnages), créez une autre collection dans ce même layer. 
	* Appliquez-leur un override "Material Override" utilisant un shader PxrBlack. Cela les rend sombres, agissant comme un masque ou les excluant visuellement dans ce pass volume.

![Capture d'écran 2025-05-01 153042.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202025-05-01%20153042.png)

En alternative, on peut également utiliser le mode Matte object : 

![Pasted image 20260209000038.png](/img/user/Pi%C3%A8ces%20jointes/Pasted%20image%2020260209000038.png)


###### Rebuild beauty + volume NUKE

- On décompose la passe Beauty en plusieurs AOVs, correspondant aux Light Groups.
- L'idée est de reconstruire la passe Volume de la même manière que la passe Beauty, avec les mêmes Light Groups.
- Utiliser des nodes Grade placés après chaque Shuffle pour contrôler l'intensité et/ou la couleur de chaque Light Group sur le volume.
- Pour que les modifications apportées aux Grade nodes sur la Beauty (intensité, teinte, etc.) soient aussi répercutées sur le Volume, **lier les réglages entre les nodes Grade** (représenté par flèche verte ou marron entre les nodes).
	- Cela peut se faire en copiant un paramètre (clic droit > Copy) et en le collant de manière **relative** sur l'autre node (clic droit > Paste Relative) ou en clonant les nodes (Ctrl + K), la modification sur l'original étant **instantanément appliquée au clone**.

![Capture d'écran 2025-05-01 145403.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202025-05-01%20145403.png)


## Références



## Liens 




