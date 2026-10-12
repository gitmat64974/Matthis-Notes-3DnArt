---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Cloth modeling - Houdini/","tags":["note_permanente"],"dg-note-properties":{"MOC":["[[CFX]]","[[HOUDINI]]"],"source":["https://youtu.be/Z9eqknbHjJY?si=tO1PlugE-xehJ7mJ"],"Projets":null,"tags":["note_permanente"],"creation date":"2026-10-12","aliases":null}}
---

## La note 

Outre toutes les techniques de modélisation qui peuvent être utiles (voir [[3_GARDEN/MOCs/MODELISATION|MODELISATION]] et [[3_GARDEN/MOCs/PROCEDURAL MODELING|MODELISATION PROCEDURALE]]), ce qui est détaillé ici est la modélisation de vêtements dans Houdini à partir de patron 2D construits avec des curves

#### Etape 1 : Patron

##### Créer le patron 2D
Là c'est très simple, on vient créer son patron en 2D avec le node curve puis on en crée un patch

![Capture d'écran 2026-10-12 232157.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202026-10-12%20232157.png)

#### Mirror le patron pour entourer le perso

Là on va mirror sous tous les angles le patron pour entourer le perso

![Capture d'écran 2026-10-12 232213.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202026-10-12%20232213.png)
#### Etape 2 : Couture

![Capture d'écran 2026-10-12 233231.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202026-10-12%20233231.png)

Mettre un vellum configure cloth en mode cloth
Puis un vellum drape : permet de venir stitch des edges entre elles
- ici on va rentrer les groups qui seront weld


## Références


> [!example]- Flashcards
> ...




## Liens 




