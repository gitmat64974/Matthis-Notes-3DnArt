---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/APEX Tags/","tags":["note_permanente"],"ctime":"2026-09-29T16:20:14.392+02:00","mtime":"2026-10-24T14:21:51.858+02:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/HOUDINI]]","[[3_GARDEN/MOCs/RIG HOUDINI]]","[[3_GARDEN/MOCs/RIG]]"],"source":["[[3_GARDEN/Notes littéraires/RIG & ANIMATE A STYLIZED CRAB - Houdini learning course - APEX]]"],"Projets":null,"tags":["note_permanente"],"creation date":"2026-09-29","aliases":null}}
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

---

Alternative au node attribute adjust array si on veut faire en VEX : le rig attribute wrangle : 
```
append(s[]@tags, 'nom-du-tag');
```

## Références


> [!example]- Flashcards
> ...




## Liens 




