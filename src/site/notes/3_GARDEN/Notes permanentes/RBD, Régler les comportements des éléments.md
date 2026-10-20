---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/RBD, Régler les comportements des éléments/","tags":["note_permanente"],"dg-note-properties":{"MOC":["[[HOUDINI]]"],"source":["[[Cours Houdini semaine 14]]"],"Projets":null,"tags":["note_permanente"],"creation date":202601230907,"aliases":null}}
---

## La note 

![rbd_constraint_nodes.png](/img/user/Pi%C3%A8ces%20jointes/rbd_constraint_nodes.png)

#### RBD Configure

La première étape de configuration se trouve dans le [[3_GARDEN/Notes permanentes/RBD configure|RBD configure]] (voir la note)

#### RBD Constraint from rules :

Node pour créer des contraintes entre les RBD objects

<u><font color="#9bbb59">ll y a plusieurs types de contraintes de connections :</font></u>
- centres de gravité (par défaut)
- Surface points (tous les points de la surface)
- Hinges

On va pouvoir attribuer ces contraintes seulement à un groupe (identifié par le path ou le name par exemple) pour régler des éléments différentes comme le bois, puis le métal etc

<u><font color="#9bbb59">On va pouvoir donc avec ce node créer un groupe de constraint :</font></u>
- group type : primitive group
- group name : le nommer
- Autres paramètres :
	- Constraints per pieces :
		- -1 : autant que nécessaire
	- nombre défini : nombres de contraintes de connections entre les pièces
	- Search radius :
		- Permet d’éviter que des points trop loin entre eux soient connectés


##### RBD Constraint properties :

Créer les attributs nécessaires et régler les contraintes entre objet :

Par niveau de difficulté à briser : <font color="#c0504d">glue</font> (très dur) - <font color="#de7802">hard</font> (assez dur) - <font color="#9bbb59">soft</font> (facile)

En dessous se trouvent les paramètres propes à chaque type de contraintes (stiffness, etc)

-> On va pouvoir appliquer ces propriétés de contraintes uniquement sur le group créé au node précédent



> [!example] On va pouvoir donc régler tout cela pour chaque type d’élément :
> 
> ![rbd_constraint_general_view_multiple_objects.png](/img/user/Pi%C3%A8ces%20jointes/rbd_constraint_general_view_multiple_objects.png)
> 

---


## Références


> [!example]- Flashcards
> ...




## Liens 
