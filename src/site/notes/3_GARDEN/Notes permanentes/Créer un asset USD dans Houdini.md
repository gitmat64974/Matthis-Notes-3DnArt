---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Créer un asset USD dans Houdini/","tags":["note_permanente"],"ctime":"2026-03-21T20:44:55.216+01:00","mtime":"2026-11-03T14:28:11.658+01:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/HOUDINI]]"],"source":["[[3_GARDEN/Notes littéraires/Cours Houdini semaine 3]]"],"Projets":null,"tags":["note_permanente"],"creation date":202510132311,"aliases":null}}
---

## La note 

Créer un LOP Network (On entre dans Solaris)
Créer ensuite un component builder : script qui va créer les nodes nécessaires à la construction de l'asset USD : 
- référencer la géo
- créer et assigner des shaders
- exporter l'asset USD

![](https://i.imgur.com/6pryHK2.png)

#### Importer la géo 

> [!NOTE]+ Importer la géo : 
> Dans le node component geometry 2 choix
> - Internal 
> 	- Rentrer dans le node et ajouter un object merge avec la geo que l'on connecte à l'output defaut (polyreduce connecté au proxy si on veut aussi)
> - External
> 	- Chercher le chemin de la geo

Pour différents matériaux assignés à différentes parties de la géométrie : la géo est splittée selon le name. Si le name est le même pour toute la géo alors il n'y a qu'une seule géo etc

> [!tip]+ Faire des variants de géométrie en construisant un asset USD :
> Il suffit de mettre plusieurs component geo qui seront les variants puis un component geometry variants juste après
> 
> ![](https://i.imgur.com/WGOnuDR.png)
> 

#### Construire le shader

*Note : On peut connecter une dome light temporairement après le component output pour mieux voir le shader que l'on fait*

Construire le shader dans le material library (un peu comme l'hypershade dans maya) 

Setup de base : 

![Capture11.png](/img/user/Pi%C3%A8ces%20jointes/Capture11.png)

> [!tip]- Node Mtlx Mix pour combiner 2 shaders en fonction d’attributs géométrique
> - Brancher en fg et bg les textures ou shaders à mixer
> - Ajouter un node ***MtlX Usd Primvar Reader***
> 	- Chercher l'attribut et bien régler la signature correspondante 
> 	- Brancher sa sortie dans le mix du Mtlx Mix
> 
> ![](https://i.imgur.com/0kr1Rvh.png)

#### Export de l’asset USD

Ça se passe dans le node component output : 
- Root prim : nom de la primitive qui contiendra la geo et les shaders
- Location dans caching : l'endroit où l'asset sera sauvegardé sur le disque
- Cliquer sur save to disk

Il y aura toujours un fichier geo, mtl et payload et c’est normal il faut surtout pas les renommer
- Geo : geo
- MTL : matériau
- Payload : référence de la geo et du matériau

L’export génère aussi une thumbnail pour l’asset automatiquement 

> [!info]- .usd vs.usda
> *.usd / .usda : Comme .ma et .mb* 
> *.usda : beaucoup plus lourd mais fichier lisible dans un éditeur de texte (ASCII)* 
> ---
> 
> PS : le .usdnc : 
> - usd non commercial → Pas un bon asset USD, fait pour ne pas faire de l’usd propre avec la version nc


## Références


Ressources : 
- [Creating USD Assets with Component Builder \| Chris Rydalch \| Solaris Workshop](https://vimeo.com/639704886?fl=pl&fe=sh)

> [!example]- Flashcards
> ...




## Liens 
