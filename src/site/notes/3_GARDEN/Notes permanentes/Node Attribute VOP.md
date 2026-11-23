---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Node Attribute VOP/","tags":["note_permanente"],"ctime":"2026-03-21T20:44:27.951+01:00","mtime":"2025-11-21T21:32:09.885+01:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/HOUDINI]]"],"source":["[[3_GARDEN/Notes littéraires/4e cours CFX]]"],"Projets":null,"tags":["note_permanente"],"creation date":202511071715,"aliases":["VOP"]}}
---

## La note 

C en gros un wrangle mais visuel, sans besoin de coder. 

Il faut rentrer dedans pour l'utiliser
(C'est un peu comme le node graph d'unreal)

> [!tip]+ Fonction promote
> Clic droit sur un paramètre (sur le node directement ou roud dentée à coté du paramètre dans le node properties) -> promote parameter : permet d"amener un paramètre au niveau supérieur". En gros ça va afficher le paramètre en question sur le node du niveau au dessus, ce qui permet de ne pas avoir besoin de rentrer de le node et chercher le paramètre à chaque fois 
> 
> #### Modifier ses paramètres : 
> Entrer dans l'interface de paramètres : 
> 
> ![Capture d'écran 2025-11-07 152056.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202025-11-07%20152056.png)
> Renommer, mettre des dossiers etc et cela va modifier la parameter window du node. 
> Par exemple : 
> ![](https://i.imgur.com/skpSDYl.png)
> Cela donne : 
> ![Capture d'écran 2025-11-07 152304.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202025-11-07%20152304.png)

#### Exemple d'utilisations

##### Noise sur la position des points d'une grid : 

![](https://i.imgur.com/cD2Qn4B.png)


##### Animation procédurale

**Le but est de remplacer une simulation vellum par une animation procédurale**

> [!example]+ Setup de base pour ocean ou drapeau procedural
> Noeuds de base : grid -> remesh -> attribute vop
> 
> ![Capture d'écran 2025-11-07 151816.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202025-11-07%20151816.png)
>


## Références


> [!example]- Flashcards
> ...




## Liens 
