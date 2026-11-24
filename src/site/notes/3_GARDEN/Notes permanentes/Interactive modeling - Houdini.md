---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Interactive modeling - Houdini/","tags":["note_permanente"],"ctime":"2026-10-09T09:08:09.735+02:00","mtime":"2026-10-25T20:09:12.809+01:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/HOUDINI]]","[[3_GARDEN/MOCs/MODELISATION]]"],"source":["Houdini learning"],"Projets":null,"tags":["note_permanente"],"creation date":"2026-10-08","aliases":null}}
---

## La note 

![](https://i.imgur.com/nySqxOu.png)


Houdini dispose de toutes sortes d'outils pour faire de la modelisation interactive dans le viewport, comme MAYA

Le principe est que plusieurs raccourcis ou activations dans le viewport vont venir créer des nodes automatiquement

---
#### Opérations de base : 

> [!NOTE]+ Bouger des points / edges / faces 
> ![](https://i.imgur.com/JnDRT6z.png)
> 
> 1. S dans le viewport pour etre en mode selection 
> 2. 2/3/4 pour selectionner des points / edges / faces
> 3. E / R / T pour scale / rotate / translate les éléments sélectionnés
> 
> -> cela crée des nodes edit automatiquement
> 
> Tips : ***Cliquer sur use mirror tout en bas des paramètres du node pour mirror l'édition***


> [!NOTE]+ Les différents modes de pivot
> - M dans le viewport : change l'orientation du pivot (world, local, component etc)
> - Clic droit sur le handle dans le viewport -> Local Frame (by connectivity) : Place le pivot selon le dernier élément sélectionné et bouge tous les éléments selon leurs propres axes locaux


> [!NOTE]+ La touche Q
> Elle permet de refaire exactement la même opération précédente (refaire une edge loop si c'était l'outil sélectionné par exemple etc)

> [!NOTE]+ Extrude
> 
> ![](https://i.imgur.com/6mN7sxt.png)
> 
> 1. Selectionner une face dans le viewport 
> 2. tab dans le viewport et chercher extrude 


> [!NOTE]+ Edge loop
> ![](https://i.imgur.com/gWhc826.png)
> 
> Dans le viewport chercher edge loop ou polysplit



> [!NOTE]+ PolyDraw
> Cela va appeler le node topobuild
> Node très puissant qui permet de faire en un node ce que fait à la fois le quaddraw et le multicut de MAYA
> 

---

#### Merge workflow

*Comment gérer en modélisation interactive de multiples objets dans Houdini ?*

Deux méthodes : 
1. Modéliser dans des objets différents puis combine -> ça vient rassembler automatiquement dans le dernier objet sélectionné en récupérant tout le network et en créant un merge
2. Selectable template : modéliser tout dans un seul objet mais au lieu d'utiliser des merge dans un premier temps utiliser les selectable template : Fonctionne exactement comme les template mais au lieu de clic on ctrl clic sur l'icone de template du node qu'on veut et là l'objet va apparaitre en entier dans le viewport en plus de celui qui est regardé

---


*Bien sur là le but n'est pas forcément de faire du [[3_GARDEN/MOCs/PROCEDURAL MODELING\|PROCEDURAL MODELING]], plutôt du manual modeling en interactif*


## Références


[[3_GARDEN/Notes permanentes/UV - Houdini\|UV - Houdini]]

> [!example]- Flashcards
> ...




## Liens 




