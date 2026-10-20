---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/RBD Cluster/","tags":["note_permanente"],"dg-note-properties":{"MOC":null,"source":null,"Projets":null,"tags":["note_permanente"],"creation date":"2026-01-26","aliases":null}}
---

## La note 

Cela permet d'ajouter plus d'irrégularité dans une [[3_GARDEN/Notes permanentes/RBD Simulation Houdini|RBD Simulation Houdini]]

2 Manières : 
- Méthode assez bas niveau
- RBD Cluster node

#### Méthode point cluster

On va arriver à ça : des codes couleurs aléatoires définissant des groupes aléatoires de géométrie :

![cluster points houdini demo.png](/img/user/Pi%C3%A8ces%20jointes/cluster%20points%20houdini%20demo.png)

_Mettre le cluster en cluster points → points pour ne pas voir la couleur car elle est faussé, puis afficher l’attribut cluster qui lui est juste_

Cela permet de créer des contraintes par cluster

On peut dans un node RBD constraint from rules cocher use clusters

Ce node va chercher l’information à l’intérieur de la geo packée, donc il faut le mettre avant de packer les géos

Cela permet d’ajouter de la variation dans le comportement d’un matériau en définissant des régions plus fortes ou faibles (en inversant le mode du cluster entre fort et faible) :

![](https://i.imgur.com/o9Fwprr.png)




#### RBD Cluster Node

![](https://i.imgur.com/qqpEm2Y.png)


*This SOP combines fractured pieces into larger clusters, either by adjusting the `name` attribute or by grouping the intracluster and intercluster constraints. The optional incoming `cluster` attribute on the constraint geometry points can be further refined with the **Add Cluster Noise** and **Random Detach** parameters.*


Video YT Artist Creek : [Learn the Basics of RBD Clusters in Houdini! - YouTube](https://youtu.be/3ld1RK5DEo8?si=2PbzreTB9pxzQ7rb)

Le RBD cluster (et le cluster points) crée un attribut cluster qui "rassemble" certaines pieces entre elles par groupes de couleurs. 

<u>Les paramètres à changer : </u>
- Size : taille des clusters
- random detach
	- detach ratio
	- detach seed



## Références

[RBD Cluster](https://www.sidefx.com/docs/houdini/nodes/sop/rbdcluster.html)

> [!example]- Flashcards
> ...




## Liens 




