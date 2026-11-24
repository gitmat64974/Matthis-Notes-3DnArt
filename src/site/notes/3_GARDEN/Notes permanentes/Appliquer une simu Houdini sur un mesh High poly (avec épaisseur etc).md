---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Appliquer une simu Houdini sur un mesh High poly (avec épaisseur etc)/","tags":["note_permanente"],"ctime":"2026-04-06T00:00:21.000+02:00","mtime":"2026-04-06T00:00:21.000+02:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/HOUDINI]]"],"source":null,"Projets":null,"tags":["note_permanente"],"creation date":"2025-11-28","aliases":["Node point deform pour Appliquer une simu Houdini sur un mesh High poly","Setup de simulation Houdini proxy to high poly","Workflow simu houdini sim mesh to final mesh","Process simulation de vêtement Houdini"]}}
---

## La note 

Pour simuler notamment du cloth dans Houdini, on ne doit pas avoir d'épaisseur, on doit avoir un maillage en triangles, pas d'UVs etc (voir notamment : [[3_GARDEN/Notes permanentes/Import export clean Houdini\|Import export clean Houdini]])

On simule donc sur un proxy puis on vient réappliquer la déformation sur le mesh d'origine

---
#### 1. Création du proxy et simulation

1. Importation et préparation du proxy : [[3_GARDEN/Notes permanentes/Import export clean Houdini\|Import export clean Houdini]]
2. Simulation : [[3_GARDEN/Notes permanentes/Simulation de tissu dans Houdini\|Simulation de tissu dans Houdini]] 

---

#### 2. Déformer le high poly par le proxy
###### Méthode 1 (pas ultra propre mais ça marche)

> [!abstract]+ Le point deform
> 
> ![Pasted image 20251128165654.png](/img/user/Pi%C3%A8ces%20jointes/Pasted%20image%2020251128165654.png)
> 
> Dans le timeshift : On enlève le $F (ctrl + click pour enlever) et on met seulement la frame 1 pour avoir la position de base
> 
> Le point deform vient deformer une geometrie par correspondance entre les points les plus proches de la géométrie déformée et de celle à déformer. Ainsi pas besoin d'avoir la même topo entre les 2 modés. 
> 
> Le point deform reprend donc tous les attributs etc du high poly !

###### Méthode 2 (plus propre, précise et légère)

> [!abstract]+ Node ray + attribute interpolate
> 
> ![Pasted image 20251205151031.png](/img/user/Pi%C3%A8ces%20jointes/Pasted%20image%2020251205151031.png)
> 
> Dans le timeshift : On enlève le $F (ctrl + click pour enlever) et on met seulement la frame 1 pour avoir la position de base
> 
> Node Ray : 
> Il permet de venir projeter sur les UVs la position des points du mesh simulé (c'est plus précis)
> - method : minimal distance
> - output : 
> 	- prim Num Attribute
> 	- Prim UVW Attribute
> 
> Attribute interpolate : 
> - Element Numbers Att : hitprim
> - UVW - Weights Attribute : hitprimuv
> 




## Références


> [!example]- Flashcards
> ...




## Liens 




