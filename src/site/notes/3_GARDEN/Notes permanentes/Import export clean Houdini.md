---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Import export clean Houdini/","tags":["note_permanente"],"ctime":"2026-03-22T12:15:22.394+01:00","mtime":"2025-11-28T17:19:18.913+01:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/HOUDINI]]","[[3_GARDEN/Notes permanentes/Alembic]]","[[3_GARDEN/MOCs/CFX]]"],"source":["[[3_GARDEN/Notes littéraires/5e cours CFX]]"],"Projets":null,"tags":["note_permanente"],"creation date":"2025-11-28","aliases":null}}
---

---

## La note 


### Import

On cherche ici à importer correctement une geometrie pour le [[3_GARDEN/Notes permanentes/Appliquer une simu Houdini sur un mesh High poly (avec épaisseur etc)\|Setup de simulation Houdini proxy to high poly]]


#### Import alembic

![Pasted image 20251128142942.png](/img/user/Pi%C3%A8ces%20jointes/Pasted%20image%2020251128142942.png)

Convert : pour que chaque primitive soit lue, et pas des primitives packées

> [!example]+ Préparer une géo avec de l'épaisseur pour simu : 
> 
> #### Exemple pour une geo type cube
> 
> *Le workflow qui suit n'est qu'un exemple*
> 
> On va enlever l'épaisseur : 
> 
> ![](https://i.imgur.com/gA9RVi7.png)
> 
> - node delete -> normal -> spread angle à 60 environ 
> - node transform : on vient venir écraser la modé : scale 0 sur z, y ou x en fonction de la mode
> - fuse : pour merge les points écrasés  
> - Remesh : quad vers triangles
> - Attribute delete : on conserve uniquement la P (position) et normal
> 
> ---
> 
> #### Exemple pour une geo type tube
> 
> *Le workflow qui suit n'est qu'un exemple*
> 
> 
>   ![](https://i.imgur.com/FfckdmR.png)
> 
> 
> 
> - For each connected pieces : Cela crée un attribut class à la valeur différente pour chaque connected piece (c'est à dire un ensemble de faces connectées entre elles)
> 	- add : on transforme la geo en points
> 	- fuse : on cherche à avoir une seule suite de points alignés -> monter un peu le snap distance
> 	- Add2 : polygon -> bygroup : construire une curve à partir des points
> 	- resample : *comme un rebuild dans maya* : lengh : 0.02
> 	- sort : reverse point sort : reverse l'ordre des points pour que le point 0 soit en haut. 
> 	- group expression : appeler le group "pin_rope" et dans le VEXpression : `@ptnum == 0;` : pour avoir un group pour chaque ptnum 0
> 	- Attribute delete : on conserve uniquement la P (position) et normal





## Références

Pour la suite de cela : [[3_GARDEN/Notes permanentes/Simulation de tissu dans Houdini\|Simulation de tissu dans Houdini]]


> [!example]- Flashcards
> ...




## Liens 




