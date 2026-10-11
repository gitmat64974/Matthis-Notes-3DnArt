---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/RBD Simulation Houdini/","tags":["note_permanente"],"dg-note-properties":{"MOC":["[[HOUDINI]]"],"source":["Houdini doc"],"Projets":null,"tags":["note_permanente"],"creation date":"2026-01-23","aliases":["Simulation RBD Houdini","Simulation destruction Houdini"]}}
---

## La note 

> [!info]+ Comment la fracture et la destruction fonctionne dans Houdini
> La plupart des outils de fracture d'Houdini prennent en charge un flux de travail _de pré-fracture_ , où la géométrie est décomposée en morceaux dans SOP, ces morceaux étant maintenus ensemble par _des contraintes de collage_ . La pré-fracture offre un contrôle artistique total sur l'apparence de la destruction
> 
> L'objet s'effondre lorsqu'une force dépasse la résistance du collage, ou vous pouvez animer manuellement la suppression du collage pour provoquer sa destruction
> 
> > [!important]- Data flow dans les nodes RBD
> > 
> > ![](https://www.sidefx.com/docs/houdini/images/dynamics/rbdmaterialfracture_node.jpg)
> > 
> > Le nœud RBD Material Fracture et [plusieurs autres nœuds RBD SOP](https://www.sidefx.com/docs/houdini/destruction/overview.html#support) partagent un ensemble cohérent d'entrées et de sorties, qui vous permettent d'envoyer la géométrie de contrainte et la géométrie proxy à travers le réseau en même temps que la géométrie fracturée
> 
> 

---
### Pré fracture
#### RBD Material Fracture

<font color="#9bbb59">Node tout en un pour la pré-fracture :</font> 

Il simule les schémas de rupture associés à différents matériaux : **béton**, **bois** et **verre**
- Possibilité d'itérer la fracturation à plusieurs niveaux.
- Peut simuler [une géométrie proxy basse résolution](https://www.sidefx.com/docs/houdini/destruction/overview.html#proxy) et copier les transformations des pièces sur une géométrie haute résolution.
- Crée automatiquement [des contraintes de collage](https://www.sidefx.com/docs/houdini/destruction/overview.html#constraints) entre les pièces.


> [!abstract]+ Proxies :
> Le nœud RBD Material Fracture peut fonctionner sur une géométrie proxy basse résolution rapide. Vous devez configurer une géométrie haute résolution et une géométrie basse résolution avec des éléments nommés identiques (par exemple, en décomposant la géométrie haute résolution en éléments nommés, puis en copiant et en réduisant le nombre de polygones pour créer le proxy)

Vous pouvez également utiliser le nœud [RBD Paint](https://www.sidefx.com/docs/houdini/nodes/sop/rbdpaint.html "Applique des valeurs sur la géométrie ou les contraintes à l'aide de traits.") pour peindre interactivement les zones de fragilité sur la géométrie avant le nœud [RBD Material Fracture](https://www.sidefx.com/docs/houdini/nodes/sop/rbdmaterialfracture.html "Fracture la géométrie d'entrée en fonction du type de matériau.") . Cela appliquera un `density`attribut aux zones où vous souhaitez accentuer la fracturation.

*Vous pouvez également effectuer une fracturation dynamique pendant la simulation DOP : [Make Breakable](https://www.sidefx.com/docs/houdini/shelf/makebreakable.html)*

> [!tip]+ Chipping
> **Activer l'effet de chipping dans l' onglet **« chipping »** rendra votre simulation plus réaliste, car cela cassera les angles et arrondira les morceaux de béton lorsqu'ils se briseront.

Le nœud RBD Material Fracture utilise ces nœuds de niveau inférieur en interne. Vous pouvez les utiliser séparément si vous le souhaitez.

|   |   |   |
|---|---|---|
|![](https://www.sidefx.com/docs/houdini/icons/SOP/booleanfracture.svg)|[Fracture booléenne](https://www.sidefx.com/docs/houdini/nodes/sop/booleanfracture.html "Fracture la géométrie d'entrée à l'aide de surfaces de coupe.")|Utilise le [nœud booléen](https://www.sidefx.com/docs/houdini/nodes/sop/boolean.html "Combine deux objets polygonaux à l'aide d'opérateurs booléens, ou trouve les lignes d'intersection entre deux objets polygonaux.") pour découper la géométrie en morceaux à l'aide de surfaces de découpe qui s'intersectent.|
|![](https://www.sidefx.com/docs/houdini/icons/SOP/voronoifracture.svg)|[Fracture de Voronoi](https://www.sidefx.com/docs/houdini/nodes/sop/voronoifracture.html "Fractionne la géométrie d'entrée en effectuant une décomposition de Voronoi de l'espace autour des points de la cellule d'entrée")|La géométrie est fracturée par la création de cellules à partir de points dispersés à l'intérieur de la géométrie.|
|![](https://www.sidefx.com/docs/houdini/icons/SOP/explodedview.svg)|[Vue éclatée](https://www.sidefx.com/docs/houdini/nodes/sop/explodedview.html "Écarte la géométrie du centre pour créer une vue éclatée.")|Éloigne les pièces les unes des autres (en fonction de leur connectivité ou `name`de leurs attributs). Ce nœud est utile pour visualiser la forme des pièces.|

#### Méthode plus bas niveau 

##### Voronoi fracture

Utiliser le node voronoi fracture avec un scatter pour définir les points de fracture

##### Boolean fracture

Video YT Artist Creek : [Boolean fracture node for destruction](https://youtu.be/TSzdcWljfCg?si=s2D3YUfFZUCWxlNe)

Il y a également le RBD Interior detail node qui permet d'ajouter du détail seulement à l'intérieur des fractures


---
### Comportement des éléments

Si aucun élément ne doit être fracturé, on peut aller directement à cette étape
Ici on va définir le type de matériau (bois, béton, métal etc) notamment par des grandeurs comme la densité, la masse etc
On va également définir (ou redéfinir) comment les différents éléments (pré fracturés par exemple ou autres) sont liés entre eux et s'influencent pour donner par exemple un caractère plus ou moins rigide à un matériau : Ce sont les contraintes


Tout cette partie est expliquée ici : [[3_GARDEN/Notes permanentes/RBD, Régler les comportements des éléments|RBD, Régler les comportements des éléments]]
Pour ajouter plus d'irrégularité on peut utiliser les [[3_GARDEN/Notes permanentes/RBD Cluster|RBD Cluster]]

---
### RBD Bullet Solver 

C'est avec ce node que l'on va réellement effectuer la simulation

Plus de détail : [[3_GARDEN/Notes permanentes/RBD Bullet Solver|RBD Bullet Solver]] 

---

#### Noeuds de bas niveaux utiles 


These are lower-level nodes, many of which are used inside the RBD Material Fracture SOP to provide functionality. You may find them useful if you are doing complex custom fracturing.

|                                                                              |                                                                                                                                                                                                                                                                                                                   |                                                                                                                                                                                  |
| ---------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ![](https://www.sidefx.com/docs/houdini/icons/SOP/connectadjacentpieces.svg) | [Connect Adjacent Pieces](https://www.sidefx.com/docs/houdini/nodes/sop/connectadjacentpieces.html "Creates lines between nearby pieces.")                                                                                                                                                                        | Creates constraint geometry based on connectivity and proximity. This is a lower-level node providing functionality included in RBD Material Fracture.                           |
| ![](https://www.sidefx.com/docs/houdini/icons/SOP/assemble.svg)              | [Assemble](https://www.sidefx.com/docs/houdini/nodes/sop/assemble.html "Cleans up a series of break operations and creates the resulting pieces.")                                                                                                                                                                | Assigns `name` attributes to pieces based on connectivity.                                                                                                                       |
| ![](https://www.sidefx.com/docs/houdini/icons/SOP/voronoifracturepoints.svg) | [Voronoi Fracture Points](https://www.sidefx.com/docs/houdini/nodes/sop/voronoifracturepoints.html "Given an object and points of impact on the object, this SOP<br>generates a set of points that can be used as input to the Voronoi<br>Fracture SOP to simulate fracturing the<br>object from those impacts.") | Very low-level node for Voronoi fracturing.                                                                                                                                      |
| ![](https://www.sidefx.com/docs/houdini/icons/SOP/voronoisplit.svg)          | [Voronoi Split](https://www.sidefx.com/docs/houdini/nodes/sop/voronoisplit.html "Cuts the geometry into small pieces according to a set of cuts<br>defined by polylines.")                                                                                                                                        | Very low-level node for Voronoi fracturing.                                                                                                                                      |
| ![](https://www.sidefx.com/docs/houdini/icons/SOP/enumerate.svg)             | [Enumerate](https://www.sidefx.com/docs/houdini/nodes/sop/enumerate.html "Sets an attribute on selected points or primitives to sequential numbers or strings.")                                                                                                                                                  | Sets an attribute on selected points or primitives to sequential numbers or strings, which is an easy way to name your pieces with a prefix without having to use a wrangle SOP. |



## Références

[Overview](https://www.sidefx.com/docs/houdini/destruction/overview.html)

[[3_GARDEN/Notes permanentes/Explosion en RBD|Explosion en RBD]] 

> [!example]- Flashcards
> ...




## Liens 




