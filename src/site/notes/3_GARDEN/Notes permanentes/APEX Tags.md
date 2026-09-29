---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/APEX Tags/","tags":["note_permanente"],"dg-note-properties":{"MOC":["[[HOUDINI]]","[[RIG HOUDINI]]","[[RIG]]"],"source":null,"Projets":null,"tags":["note_permanente"],"creation date":"2026-09-29","aliases":null}}
---

## La note 

![](https://www.sidefx.com/docs/houdini/images/char/kinefx_prepareskel_tags.jpg)


> [!NOTE] A quoi ça sert
> Les tags sont super utiles pour créer des rigs procéduraux dans APEX
> On vient regrouper au préalable des joints en leur donnant le même tag pour qu'ils aient un comportement automatiquement assigné dans les ``APEX autorig component``
> 

Comment créer des tags : *L'attribute adjust array*
1. A la fin du skeleton, mettre un attribute adjust array en mode point
2. Dans le viewport, selectionner plusieurs joints 
3. Appuyer sur A pour donner un nom au tag 
4. Voilà tout ces joints sont taggés avec le même tag

![](https://i.imgur.com/mTRopmn.png)

Ensuite dans le ``APEX autorig component`` il suffit de mettre le nom du tag dans driven -> segments 
(Bien add FK and Bone deform components dans le pack character pour que ça fonctionne)

## Références


> [!example]- Flashcards
> ...




## Liens 




