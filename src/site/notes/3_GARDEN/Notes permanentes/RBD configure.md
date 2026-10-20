---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/RBD configure/","tags":["note_permanente"],"dg-note-properties":{"MOC":["[[HOUDINI]]"],"source":["[[Cours Houdini semaine 14]]"],"Projets":null,"tags":["note_permanente"],"creation date":202601230907,"aliases":null}}
---

## La note 

==-> Initialiser la configuration de l’objet RBD==

On va pouvoir définir la **densité**, **masse**, etc propre à la physique de l’objet

→ *Trouver ces infos précises pour les matériaux sur des gros sites de constructeurs ou des ressources scientifiques*

#### Régler plusieurs matériaux :
###### Méthode 1 : 

![rbd_configure_regler_plusieurs_mat.png](/img/user/Pi%C3%A8ces%20jointes/rbd_configure_regler_plusieurs_mat.png)

On peut sélectionner un groupe en particulier et créer plusieurs attributs (un pour chaque objet)

Mais cela va s’afficher seulement sous forme d’onglets avec des numéros et pas le nom des groups → pas très lisible

###### Méthode 2 


Donc on peut sinon stacker plusieurs RBD Configure à la suite :

![rbd_configure_stacking.png](/img/user/Pi%C3%A8ces%20jointes/rbd_configure_stacking.png)

_Ici le rbd config defaut configure l’ensemble de l’objet avec des paramètres généraux (par exemple un bois pour une cabane), pour être sur d’avoir toujours l’ensemble de la geo configurée pour la simu. Les configurations qu’on mettra après viendront prendre la priorité sur celle là bien sur_

#### Régler les volumes de collisions :

En les visualisant temporairement :
- visualize : collision padding
- collision shape : règler le collision padding

---


## Références


> [!example]- Flashcards
> ...




## Liens 
