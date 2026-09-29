---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Animation stepping Houdini/","tags":["note_permanente"],"dg-note-properties":{"MOC":["[[ANIMATION]]","[[HOUDINI]]"],"source":["[[RIG & ANIMATE A STYLIZED CRAB - Houdini learning course - APEX]]"],"Projets":null,"tags":["note_permanente"],"creation date":"2026-09-29","aliases":null}}
---

## La note 


*Context SOP, à la sortie d'une géo animée, quelle qu'elle soit*

Le but : Changer procéduralement le stepping de l'anim (24 fps, 12 fps etc)

On a besoin que de 2 nodes : wrangle et timeshift

![](https://i.imgur.com/Xi4teie.png)

Wrangle en mode detail après la géo animée : 

```C
int step = chi("frame_step");
float stepped_frame = floor((@Frame - 1) / step) * step + 1;
f@stepped_time = stepped_frame;
```

Puis on vient dans un timeshift appliquer l'attribut créé avec cette expression : 

``detail(0, "stepped_time",0)``

Et voilà 


## Références


> [!example]- Flashcards
> ...




## Liens 




