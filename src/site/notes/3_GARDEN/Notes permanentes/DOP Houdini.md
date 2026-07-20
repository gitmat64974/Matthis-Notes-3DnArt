---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/DOP Houdini/","tags":["note_permanente"],"dg-note-properties":{"MOC":["[[HOUDINI]]"],"source":["CG Weeky"],"Projets":null,"tags":["note_permanente"],"creation date":"2026-01-22","aliases":["DOP Network"],"banner":"https://forums.odforce.net/uploads/monthly_2020_01/DOP_Velocity.jpg.849809f525017834350ab23d9f1be3b6.jpg"}}
---

## La note 

![](https://forums.odforce.net/uploads/monthly_2020_01/DOP_Velocity.jpg.849809f525017834350ab23d9f1be3b6.jpg)

On entre dans un **contexte de dynamics** :
C’est là dedans que se trouve ce qu’il y a en dessous du rbd bullet solver, ou du vellum solver par exemple


> [!quote] CG Weeky
> Dops aren't sops (obviously), they don't directly model the flow of points through a graph, rather they setup behaviors and relationships. ==Remember that a sim is all about calculating based on the results of the previous frame==, so thats what DOP networks are there to help you setup; a way to set an initial state, then a loop where data flows through, gets to the bottom, is fed into the top again, every frame.

### Les éléments de base d'un système DOP

- Les **DOP source** importent des géométries dans le réseau DOP ou créent des géométries.
- Les **DOP objet** sont des conteneurs pour les systèmes DOP. Pour des éléments tels que les simulations de fumée, ils représentent un cube voxel. Pour d'autres éléments, tels que les systèmes de particules, il n'y a pas de conteneur physique, mais c'est le nœud qui stocke les données des particules. Il en existe de nombreux types :
	- **popObject** pour les particules
	- **rbdObject** pour les corps rigides
	- **wireObject** pour les simulations de fils
	- **groundplane** pour un plan de sol statique infini
	- **staticObject** pour intégrer des géométries de collision
- Les **DOP Solver** sont utilisés pour calculer les simulations. Là encore, il existe de nombreux types pour chaque type de simulation (pop, flip, smoke, rbd, etc.).
- Les **DOP Merge** ressemblent aux SOP Merge, mais sont utilisés pour configurer les relations de collision. Par défaut, les entrées de gauche affectent les entrées de droite, vous devez donc merge un objet statique à gauche d'un solveur pop pour que les particules entrent en collision avec la géométrie.
- Les nœuds **Force** gèrent les forces, évidemment. Leur influence dépend de leur position par rapport aux nœuds merge. Par exemple, deux flux entrant dans un nœud merge. Placez la force avant le merge, elle n'affectera qu'une seule entrée. Placez-la après, elle affectera les deux.


*L'exécution Dop se fait de haut en bas, puis de gauche à droite. Étant donné que chaque image utilise le résultat de l'image précédente, l'ordre semble sans importance, mais en réalité, il est essentiel.*

### Tips et setups récurrents

Venir récupérer la velocity d'un objet en mouvement (la vitesse : v) : 
**Node trail** en Compute Velocity -> va automatiquement créer l'attribut v avec les valeurs correspondantes





## Références

[[3_GARDEN/Notes permanentes/POP Network|POP Network]]

> [!example]- Flashcards
> ...




## Liens 




