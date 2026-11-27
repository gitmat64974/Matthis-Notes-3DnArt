---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Add Groom to APEX Rig/","tags":["note_permanente"],"ctime":"2026-09-29T16:38:31.637+02:00","mtime":"2026-11-26T23:58:05.040+01:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/HOUDINI]]","[[3_GARDEN/MOCs/RIG]]","[[3_GARDEN/MOCs/RIG HOUDINI]]"],"source":null,"Projets":null,"tags":["note_permanente"],"creation date":"2026-09-29","aliases":null}}
---

## La note 

*Prérequis : il faut absolument que la géo ait un attribut N ou tangentu (le polyframe SOP génère les 2 automatiquement) que c'est en fonction de ces attributs que le apex add groom vient attacher le groom au skin*

Très simple : Apex Add groom node avec le groom en deuxième entrée
et c'est tout ! 

Juste nommer Primitive Basename "Hairs" pour la propreté

#### Créer des joints pour rigger le groom

![](https://i.imgur.com/HWT7WbQ.png)


Dans la section joints, créer un control group

Là, avec le sélecteur group, on a juste à sélectionner quelques curves du groom dans le viewport et des joints seront automatiquement créés et skinneront le groom avec un weighting automatique

*Cocher orient to Skin Vector Attribute*

On peut ensuite, à l'anim dans APEX très facilement appliquer un mouvement secondaire automatique à ces joints 

## Références

[APEX Add Groom](https://www.sidefx.com/docs/houdini/fur/addgroom.html)

> [!example]- Flashcards
> ...




## Liens 




