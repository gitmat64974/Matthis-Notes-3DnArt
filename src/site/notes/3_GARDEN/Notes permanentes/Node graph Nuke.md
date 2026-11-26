---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Node graph Nuke/","tags":["note_permanente"],"ctime":"2026-03-21T20:44:27.748+01:00","mtime":"2026-04-24T17:43:18.879+02:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/COMPOSITING]]"],"source":["[[3_GARDEN/Notes littéraires/2e cours compositing esma 3d2a]]"],"Projets":null,"tags":["note_permanente"],"creation date":"2025-05-12","aliases":null}}
---


## La note

![Pasted image 20241107220739.png](/img/user/Pi%C3%A8ces%20jointes/Pasted%20image%2020241107220739.png)

Dans un graphique, l'information doit toujours circuler :  
- de haut en bas,  
- de gauche à droite ;  

Tous les troncs/branches de scripts doivent toujours être fusionnés sur le tronc de script principal : 

![Pasted image 20241107221426.png](/img/user/Pi%C3%A8ces%20jointes/Pasted%20image%2020241107221426.png)

#### Noeuds

![Capture d'écran 2025-02-27 083903.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202025-02-27%20083903.png)

Appuyer sur TAB n'importe où dans le node graph pour ouvrir las élection des noeuds 

Un nœud peut avoir : 
- un nombre quelconque d'entrées en haut, à gauche et à droite du nœud ; 
- une seule sortie en bas du nœud

D : désactive le noeud

Connecter des nœuds : 

![Capture d'écran 2024-11-07 221845.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202024-11-07%20221845.png)

#### Read, Write

![Capture d'écran 2025-02-27 083932.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202025-02-27%20083932.png)
#### Noeud Merge

Raccourci M 

Pour organiser l’espace 2D nodal dans Nuke, on emploie les convention suivantes: 
1. L’information se déplace de haut en bas & de droite à gauche. 
2. Tout information passant au-dessus d’une autre ira se connecter à l’Input A du Merge; 
3. Toute information passant en-dessous d’une autre ira dans les Inputs B du Merge;

> [!info] Modes de fusion souvent utilisés: 
> - Over / Under — This is the default operation. Layers image A over / under B according to the alpha of image A. 
> - Multiply — Multiplies the values but stops two negative values from becoming a positive number. 
> - Divide — Divides the values but stops two negative values from becoming a positive number. 
> - Plus — The sum of image A and B. 
> - Minus — The difference between image A and B. 
> - Mask — This is the reverse of the ‘in’ operation. Only shows the areas of image B that overlap with the alpha of A. 
> - Stencil — This is the reverse of the ‘out’ operation. Only shows the areas of image B that do not overlap with the alpha of A.

![Capture d'écran 2025-02-27 084240.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202025-02-27%20084240.png)


## Références 

## Liens 
