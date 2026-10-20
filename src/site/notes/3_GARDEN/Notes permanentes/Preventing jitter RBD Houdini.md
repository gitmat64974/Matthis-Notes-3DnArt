---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Preventing jitter RBD Houdini/","tags":["note_permanente"],"dg-note-properties":{"MOC":["[[HOUDINI]]"],"source":null,"Projets":null,"tags":["note_permanente"],"creation date":"2025-12-07","aliases":null}}
---

## La note 


<iframe width="560" height="315" src="https://www.youtube.com/embed/G11fHMJBiu0?si=7AebMYwxmTBLAs3F" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

> [!todo]+ Problème que l'on cherche à régler
> Dans les simulations RBD, les morceaux qui ont déjà atterri continuent souvent à glisser ou tourner légèrement au sol, ce qui donne un effet de « jitter » peu réaliste.
> L’objectif est de les faire se stabiliser proprement à un moment choisi, sans geler brutalement toute la simulation.

#### Process : 

***Pour la configuration, juste après la simu cachée :*** 

> [!example]+ Node Attribute adjust float : 
> - Attribute name : Cd pour tester, puis custom_drag
> - Adjustement value : 
> 	- Operation : set always
> 	- Range values : 
> 		- min : 0
> 		- max : 0.05 : *Ici on peut augmenter progressivement le paramètre avec 2 clés d'anim pour avoir une forte valeur (0.25 par exemple) à la frame où on veut qu'il n'y ait plus du tout de jitter*
> 	- Pattern type : Line -> deux points se créent dans l'espace, on peut les délpacer pour créer un ramp. Le but là est de créer un ramp de haut en bas : blanc en bas, noir en haut

Ensuite on déplace ce node dans le bullet solver, dans un sopsolver branché à l'output PRESOLVE

##### Dans le SopSolver : 

![](https://i.imgur.com/re3QFIS.png)


Le Wrangle qui est juste après : 

```C
v@v *= (1-@custom_drag);
v@w *= (1-@custom_drag);
```



## Références


> [!example]- Flashcards
> ...




## Liens 



