---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Skeleton KineFX/","tags":["note_permanente"],"ctime":"2026-09-28T09:15:41.354+02:00","mtime":"2026-11-19T22:53:57.081+01:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/HOUDINI]]","[[3_GARDEN/MOCs/RIG]]"],"source":"Houdini doc","Projets":null,"tags":["note_permanente"],"creation date":"2026-02-07","aliases":null}}
---

## La note 

[Working with skeletons](https://www.sidefx.com/docs/houdini/character/kinefx/skeletons.html)
#### Construire un skeleton

Le node le plus simple est le skeleton, qui va venir créer des joints automatiquement

> [!tip] Snapping : 
> - X dans le viewport pour l'activer
> - On a aussi l'icone aimant dans la toolbar verticale à gauche du viewport
> - L'icone juste en dessous permet de venir choisir le type de snapping (grid, points, primitive etc)

Les 2 modes : (*F dans le viewport pour switcher les modes*)
- **Create** (par défaut)
- **Modifiy**

> [!NOTE] Modify : 
> appuyer sur **G** pour activer le tweak mode qui va permettre de déplacer les joints
> 
> ***Option child compensate*** : lorsqu'elle n'est pas activée, bouger un joint bouge également ses enfants, lorsqu'elle est activée, bouger un joint ne bouge pas ses enfants, ce qui rend assez pratique l'édition des joints

Joint placement : On a plusieurs modes pour définir comment les joints se positionnent par défaut à la création (approximation du centre de la géo, surface, normal etc)

#### Paramètres complets des joints

Ouvrir les paramètres complets du joint sélectionné : Dans le viewport -> ==P==

On peut ici gérer précisément les translations ou les rotations (qui définissent donc au cas par cas l'orientation du joint) et plein d'autres choses

> [!tip]+ Gérer manuellement les orientations de chaque joint : 
> On peut donc gérer manuellement les orientations de chaque joint en cochant child compensate puis rotate le joint comme on veut qu'il soit orienté
> 
> H pour show handle : voir l'orientation, et gérer facilement les transformations

Ctrl + Shift pour insérer un joint entre 2 joints
## Références

Skinning : [[3_GARDEN/Notes permanentes/Skinning KineFX\|Skinning KineFX]]

[[3_GARDEN/Notes permanentes/Préparer skeleton et geo pour APEX\|Préparer skeleton et geo pour APEX]]

> [!example]- Flashcards
> ...




## Liens 




