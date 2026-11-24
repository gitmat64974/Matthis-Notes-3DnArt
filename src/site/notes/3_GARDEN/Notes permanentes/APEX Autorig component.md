---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/APEX Autorig component/","tags":["note_permanente"],"ctime":"2026-09-28T09:15:41.467+02:00","mtime":"2026-09-26T17:46:57.374+02:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/HOUDINI]]","[[3_GARDEN/MOCs/RIG]]"],"source":null,"Projets":null,"tags":["note_permanente"],"creation date":"2026-02-07","aliases":null}}
---

## La note 

[Rigging a character using rig components](https://www.sidefx.com/docs/houdini/character/kinefx/rigcharacter.html)

Le fonctionnement est en chaine : FK, puis IK, puis Root, puis Look At  etc


### FK

Simplement mettre un autorig component en FK transform et tous les joints seront setup en FK

### IK

Component source : Multi IK

Là on va pouvoir utiliser les tags setupés précédemment (voir [[3_GARDEN/Notes permanentes/Skeleton KineFX#Tags\|Skeleton KineFX#Tags]]) dans driven -> segments : choisir l'ensemble de joints où l'on veut des IK



## Références


> [!example]- Flashcards
> ...




## Liens 




