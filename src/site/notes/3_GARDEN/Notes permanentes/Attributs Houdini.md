---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Attributs Houdini/","tags":["note_permanente"],"dg-note-properties":{"MOC":["[[HOUDINI]]"],"source":null,"Projets":null,"tags":["note_permanente"],"creation date":"2026-01-10","aliases":null}}
---

## La note 

Les attributs sont au cœur d'Houdini. 
Ce sont des données stockées sur de la géométrie (*points, vertices, primitives, ou detail*) qui peuvent être utilisées par les nœuds suivant pour effectuer une opération

Un attribut est une paire clé-valeur stockée sur de la géométrie
On peut donc dégager 4 composantes d'un attribut : 


> [!abstract]+ Les 4 composantes d'un attribut
> - Nom : ( ex : *P*)
> - Valeur : ( ex : *1.5, 2.5, 0.2*)
> - Type : Le type de données ( ex : *vecteur 3*)
> 	- String : chaine de caractère (a@ en VEX, pour ASCII)
> 	- Integer : nombre entier (i@ en VEX)
> 	- Float : nombre pouvant être à virgule (f@ en VEX)
> 	- Vector : vecteur à 3 dimensions (v@ en VEX)
> - Class : Là où est stocké l'attribut ( ex : *Points*)

**Class** - Attributes can belong to Points, Primitives, Details and Vertices. This will affect how they get used down the chain. 
**Type** - You can set up float, integer or string attribute types amongst others


> [!info]+ Geometry spreadsheet 
> permet d'avoir une vue précise des attributs contenu dans le noeud sélectionné




## Références

[Geometry attributes](https://www.sidefx.com/docs/houdini/model/attributes.html)

[What are Attributes? \| Houdini Tutorial - YouTube](https://youtu.be/rMELSl3P1tE?si=r6x6TrFJwceJqHMg)


> [!example]- Flashcards
> ...




## Liens 




