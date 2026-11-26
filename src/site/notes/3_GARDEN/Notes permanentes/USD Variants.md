---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/USD Variants/","tags":["note_permanente"],"ctime":"2026-11-26T13:18:27.666+01:00","mtime":"2026-11-26T10:53:40.333+01:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/SOLARIS]]","[[3_GARDEN/MOCs/USD]]"],"source":["[[3_GARDEN/Notes littéraires/USD - SideFX Course]]"],"Projets":null,"tags":["note_permanente"],"creation date":"2026-11-26","aliases":null}}
---

## La note 

Les variants sont un moyen de stocker des versions différentes d'une même sous primitive dans sa primitive parent

- Les variantes sont flexibles quant à ce qu'elles peuvent stocker 
	- remplacer des matériaux, de la géométrie, ou modifier la hiérarchie enfant 
- Elles doivent être stockées sur la primitive racine (root prim) de l'asset
	- cela permet la sélection de la variante si elle est marquée comme instanciable ou si le payload est déchargé 
- Elles ne modifient pas les namespaces jusqu'à la primitive qui possède l'ensemble de variantes
	- ex) "/geo/forest/tree/model"

Cas courant d'utilisation des variants : 
- Ensemble de géos différentes
- LOD
- Ensemble de matériaux différents

### Dans Solaris 

#### Create LOD LOP

Ce node permet de créer des versions de la géométrie avec un pourcentage de faces supprimées gradatif. 

Paramètres : 
- Primitive Path : l'asset sur lequel on veut créer des LOD
- Variant Set : le nom du set de variant qu'on crée (souvent levels)
- Variant name root : nom des variant (souvent LOD_)
- ID offset : mettre à -1 pour commencer les variant à partir du LOD_0 et pas du LOD_1

Donc toute les infos de chaque géométrie des variants est stockée dans le fichier usd qui va etre exporté si on utilise uniquement ce node

#### Add variant

Ce node fait quelque chose de bien différent, au lieu d'écrire de la géométrie, il la **référence**. Donc il demande que les variants soient créés avant et qu'on les mette en input (*en input 2, le premier est le stage*)

Chaque variant doit donc etre un fichier usd (ça peut etre juste un fichier de géo par exemple) et ensuite on vient créer le set de variants dans le node add variant

#### Add variants to existing primitive

Il permet de créer des variants plus complexes comme les variants de matériaux
C'est un recipe de 2 nodes dans la version 22 (les begin et end des blocks) : 

![Capture d'écran 2026-10-22 150900.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202026-10-22%20150900.png)

Breakdown : 
- Material library : on crée ici les différents matériaux, (3 dans l'exemple plus haut)
- Configure layer : crée un layer pour les matériaux comme ça les variants de matériaux seront stockées dans un fichier usd dédié
- Reference : On vient ici ajouter chacun des matériaux dans le stage. Paramètres : 
![Capture d'écran 2026-10-22 152430.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202026-10-22%20152430.png)


Variant block begin : 
- Cocher Layer break : comme cela on vient créer un nouveau layer et ce qu'il y a avant ne va pas être save dans l'usd ROP qui servira à exporter les variants

Variant block end : 
- Primitive path : l'asset sur lequel on vient crée les variants
- Variant Set : le nom du set de variants qu'on crée (de ce cas `mtl`)


## Références


> [!example]- Flashcards
> ...




## Liens 




