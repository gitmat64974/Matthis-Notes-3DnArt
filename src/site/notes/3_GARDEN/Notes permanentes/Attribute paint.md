---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Attribute paint/","tags":["note_permanente"],"ctime":"2026-03-22T12:15:21.619+01:00","mtime":"2026-11-26T23:03:59.600+01:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/HOUDINI]]","[[3_GARDEN/MOCs/CFX]]"],"source":["[[3_GARDEN/Notes littéraires/Cours houdini ESMA]]","[[3_GARDEN/Notes littéraires/Cours CFX ESMA]]"],"Projets":null,"tags":["note_permanente"],"creation date":"2025-12-12","aliases":null}}
---

## La note 


![](https://i.imgur.com/KhjJn69.png)


Attribute Paint crée ou modifie des attributs **de points** en peignant directement dans le viewport. 
Chaque coup de pinceau change la valeur de l’attribut sur les points touchés, et ces valeurs restent attachées aux points pour être réutilisées plus loin

[Attribute Paint](https://www.sidefx.com/docs/houdini/nodes/sop/attribpaint.html)

==Pour les versions d'Houdini précédant la 21, définir le nom de l’attribute avant sinon on devra tout repeindre==


> [!tip] Peindre
> Handle tool pour peindre
> Ctrl + MMB : taille brush
> Shift : smooth 
> Ctrl : paint background

> [!example] Paramètres
> Parameter window : 
> Attributes : 
> - Définir le ou les attributes à créer 
> Symmetry : 
> - Activer la symétrie


#### Récupérer le paint sur une autre géo

A savoir que si la géo change, le paint n'est absolument pas perdu, il suffit de faire *recache -> recache strokes* et le paint sera reprojeté sur la nouvelle géo


## Références


> [!example]- Flashcards
> ...




## Liens 




