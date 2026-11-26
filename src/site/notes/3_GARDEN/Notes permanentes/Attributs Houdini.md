---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Attributs Houdini/","tags":["note_permanente"],"ctime":"2026-03-22T12:15:21.621+01:00","mtime":"2026-11-26T11:22:05.092+01:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/HOUDINI]]"],"source":null,"Projets":null,"tags":["note_permanente"],"creation date":"2026-01-10","aliases":null}}
---

## La note 

Les attributs sont donc les données stockées sur la géométrie (*points, vertices, primitives, ou detail*) qui peuvent être utilisées par les nœuds suivant pour effectuer une opération

> [!abstract]+ Les 4 composantes d'un attribut
> - Nom : ( ex : *P*)
> - Valeur : ( ex : *1.5, 2.5, 0.2*)
> - Type : Le type de données ( ex : *vecteur 3*)
> 	- String : chaine de caractère (a@ en VEX, pour ASCII)
> 	- Integer : nombre entier (i@ en VEX)
> 	- Float : nombre pouvant être à virgule (f@ en VEX)
> 	- Vector : vecteur à 3 dimensions (v@ en VEX)
> - Class : Là où est stocké l'attribut ( ex : *Points*)


> [!info]+ Geometry spreadsheet 
> permet d'avoir une vue précise des attributs contenus dans le noeud sélectionné
> 
![](https://i.imgur.com/kSCTlED.png)



#### Pseudo attributs 

Ce sont des attributs que Houdini connait de base
En voici la liste : 
- P
- N
- Cd
- pscale
- uv
- v
- up
- orient
- ptnum
- primnum
- vtxnum
- numpt
- numprim
- numvtx
- age
- id
- life
- Time
- Timelnc
- Frame

---
### Nodes de manipulation d'attributs

#### Attribute paint

Permet de peindre à la main un attribut

#### Attribute noise

Permet d'appliquer un noise sur un attribut
#### Attribute randomize

Permet de random n'importe quel attribut, même les réservés très facilement

#### Attribute from map

Transforme une map de texture en attribut (stocké sur la géo donc)

et plein d'autres...

---
### Créer ses propres attributs

> [!NOTE]+ En VEX
> Très simple : ``@monattribut = ...;``
> On peut aussi spécifier le type de data de l'attribut avant le @ (f pour float, v pour vecteur, s pour string etc) mais ce n'est pas obligatoire


## Références

- [[3_GARDEN/Notes permanentes/Attribute paint\|Attribute paint]]
- [[3_GARDEN/Notes permanentes/Attribut Curveu\|Attribut Curveu]]

#### Ressources

[Geometry attributes](https://www.sidefx.com/docs/houdini/model/attributes.html)

[What are Attributes? \| Houdini Tutorial - YouTube](https://youtu.be/rMELSl3P1tE?si=r6x6TrFJwceJqHMg)


> [!example]- Flashcards
> ...




## Liens 




