---
{"dg-publish":true,"permalink":"/3_GARDEN/MOCs/USD/","tags":["note_permanente","MOC"],"dg-note-properties":{"MOC":["[[HOUDINI]]","[[SOLARIS|Solaris]]"],"source":["[[Cours Houdini semaine 3]]"],"Projets":null,"tags":["note_permanente","MOC"],"creation date":"2026-10-26","aliases":null}}
---


# Cartographie


# Définition

Qu'est ce que l'USD ?
C'est un format de fichier assez différent du fbx, obj, abc etc

En réalité ce n’est pas à proprement parler un format mais c'est plutôt une description de scène où on peut stocker n’importe quoi (géo, textures, matériaux, lights, caméras, rendersettings etc)

USD veut dire *Universal Scene description* : Qu’importe le moteur de rendu, l’USD est une description de scène universelle

> [!success]+ Intérêt de l'USD : 
> - Le partage de fichiers dans de grandes productions est extrêmement plus efficace car on a un seul type de fichier pour tout, qui en plus est non propriétaire donc potentiellement compatible avec tout. 
> - On peut faire des références à l’infini. Ce qui fait que les fichiers peuvent être extrêmement petits (quelques ko), référençant constamment en chaîne des choses sur le disque. Tout est cloisonné en plein de petits bouts. 

On voit donc avec tout ça l'importance d'une organisation très solide avec nommage ultra carré

Dans l’USD, tout est stocké sur le disque 
- Tout doit être disponible sur le disque, utilisable depuis n’importe quel logiciel ou même sans (juste en ligne de commande pour lancer des rendus sur des farms par exemple)


Petit historique : 
L'usd était un format propriétaire de Pixar qu’ils ont révisé en open source en 2016. C’est une évolution du RIB. 


# Structure


- [[3_GARDEN/Notes permanentes/Créer un asset USD dans Houdini|Créer un asset USD dans Houdini]]

*Solaris est un logiciel qui a été construit autour de l’USD*


#### USD Asset Creation

- [[3_GARDEN/Notes permanentes/Component Builder|Component Builder]]
	- [[3_GARDEN/Notes permanentes/Créer des variants avec le component builder|Créer des variants avec le component builder]]

### USD set dress et layout

[[3_GARDEN/Notes permanentes/Techniques pour répartir un asset avec des variants dans un set - Solaris|Techniques pour répartir un asset avec des variants dans un set - Solaris]]


# Appropriation et réflexions 

#### Réflexions


#### Essais





# Ressources


- [USD Basics with Solaris \| SideFX](https://www.sidefx.com/tutorials/usd-basics-with-solaris/)
- [LOPs for Solo Artists - YouTube](https://youtu.be/WfC16LYYIAw?si=QeNJYXRO0nbNTAvi)
- [Introduction - Usd Survival Guide](https://lucascheller.github.io/VFX-UsdSurvivalGuide/)




