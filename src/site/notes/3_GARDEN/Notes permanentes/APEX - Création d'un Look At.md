---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/APEX - Création d'un Look At/","tags":["note_permanente"],"dg-note-properties":{"MOC":["[[HOUDINI]]","[[RIG]]","[[RIG HOUDINI]]"],"source":null,"Projets":null,"tags":["note_permanente"],"creation date":"2026-09-29","aliases":null}}
---

## La note 

#### Etape 1 : créer les deux joints nécessaires

On crée deux joints, un en face de chaque oeil (add -> transform -> name sur les points -> rig doctor avec initialize transform pour transformer en joints -> skeleton mirror pour mirror)

Parent joints : On vient parenter ces deux joints aux bases de chacun des yeux

![Capture d'écran 2026-09-26 105454.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202026-09-26%20105454.png)

#### Etape 2 : Apex look at 

On va ajouter un apex auto rig component après l'autorig builder en mode lookat

Tout le setup va se faire dans l'onglet Driven : 
- Parent : pour que le lookat bouge avec tout le rig on le parent en général au body ou au chest ou au head en fonction du rig
- Driven : Le contrôleur qui va être influencé par le lookat. Quand on le setup, Apex va remplacer ce controleur par un nouveau, qui servira à rotate selon le lookat 
- Driver : le nom du nouveau controleur créé
- Target : le joint de lookat

![](https://i.imgur.com/gpAAGdK.png)




## Références


> [!example]- Flashcards
> ...




## Liens 




