---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/DOP flip simulation/","tags":["note_permanente","en_cours"],"ctime":"2026-03-22T12:15:22.041+01:00","mtime":"2026-03-21T20:44:34.971+01:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/HOUDINI]]","[[3_GARDEN/MOCs/FLUID SIMULATIONS HOUDINI]]"],"source":null,"Projets":null,"tags":["note_permanente","en_cours"],"creation date":"2026-01-27","aliases":null}}
---

## La note 




> [!abstract]+ Les 4 entrées du flip solver : 
> 1. Fluid to solve : le flip object
> 2. particle velocity : entrée pour un pop solver pour gérer le comportement du fluid avec des particules
> 3. volume velocity : idem mais avec des volumes
> 4. sourcing : Source d'emission. *brancher un volume source par exemple pour utiliser un vdb comme source d'emission*


Volume motion -> Velocity transfer : 
- FLIP (Splashy) : permet d'avoir un fluid qui produira beaucoup de splashes
- APIC (swirly) : permet d'avoir un liquid qui produira moins de splashes et plus de vagues


#### Gérer les colliders


Noter

#### Perte de volume (notamment en collision)


La perte de volume est due à la tentative du solver de maintenir une séparation entre les particules constantes en tuant celles qui se "collapsent" et en en ajoutant là où il en manque. C'est ce qu'on appelle le reseeding. 

Donc lorsque les particules se compressent trop (à cause d'une collision par exemple), beaucoup sont kill

![Pasted image 20260210220308.png\|672](/img/user/Pi%C3%A8ces%20jointes/Pasted%20image%2020260210220308.png)

Par exemple : 

3 particules arrivent assez vite et elles rencontrent une geometrie de collision : 

![](https://i.imgur.com/ylZZpTK.png)

Elles vont se compresser et seulement une seule particule survira

Autre exemple dans un verre : 

![430](https://i.imgur.com/Uw4dJO4.png)

La couche du dessus contient les particules qui ont le moins de voisin, elles vont donc etre kill. Puis la couche d'en dessus sera ensuite celle qui aura le moins de voisin, elle sera kill. Puis la couche d'en dessous, et ainsi de suite. 

#### Correction de la perte de volume

Gérer le reseeding dans le flip solver -> particle motion -> reseeding

Augmenter les max sub steps

Activer la particle seperation dans le flip solver : particle motion -> separation -> apply particle separation
C'est une méthode qui permet de faire en sorte que les particules restent toujours à une certaines distance les unes des autres pour éviter qu'elles collapsent


Baisser la grid scale
Qu'est ce que la grid scale : La résolution de la grille eulérienne en tant que rapport de la séparation des particules. Une échelle de grille plus élevée correspond à une grille moins bien définie. plus la grid est petite, plus il y a de densité et de définition dans le fluid
*La mettre à 1.5 par exemple*


## Références

[Quicktip: Fluid Splashes Using FLIP - YouTube](https://youtu.be/_6SQPc961ZE?si=4jCwXJDrYZlqTmhV)

---

Dans la version 21, pour un setup ultra rapide, il y a le [[3_GARDEN/Notes permanentes/Node\|Node]] Labs splatter





> [!example]- Flashcards
> ...




## Liens 




