---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Hscript expressions Houdini/","tags":["note_permanente"],"dg-note-properties":{"MOC":["[[HOUDINI]]"],"source":null,"Projets":null,"tags":["note_permanente"],"creation date":"2026-09-04","aliases":null}}
---

## La note 

Les incontournables : 

|Besoin|Expression|Exemple|
|---|---|---|
|Frame courante|`$F`|`$F * 0.1`|
|Frame avec sous-décimales|`$FF`|utile en motion blur|
|Temps en secondes|`$T`|`sin($T * 2)`|
|Nombre aléatoire 0-1|`rand(seed)`|`rand($F)`|
|Remapper une plage|`fit(val, old_min, old_max, new_min, new_max)`|`fit(rand($F),0,1,2,8)`|
|Remapper depuis 0-1|`fit01(val, new_min, new_max)`|`fit01(rand($PT),1,5)`|
|Lire un autre paramètre|`ch("chemin/param")`|`ch("../grid1/sizex")`|
|Lire un paramètre texte|`chs("chemin/param")`|`chs("../switch1/input")`|
|Lire une rampe|`chramp("nom", position)`|`chramp("colorramp", $PT/($NPT-1))`|
|Borner une valeur|`clamp(val, min, max)`|`clamp($F,1,100)`|
|Valeur d'un attribut de point|`point(surface, ptnum, "attrib", comp)`|`point(0,$PT,"P",1)`|


#### Bounding box

``bbox("../node", D_YSIZE)``

Il y a 9 types différents : X, Y, Z _ MIN, MAX, SIZE -> ex ``D_XMIN`` ou ``D_YMAX`` ou ``D_ZSIZE`` etc
-> Min et max sont des plans donc des positions et pas des calculs de longueur comme size




## Références


> [!example]- Flashcards
> ...




## Liens 




