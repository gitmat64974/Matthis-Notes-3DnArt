---
{"dg-publish":true,"permalink":"/3_GARDEN/MOCs/USD/","tags":["note_permanente","MOC"],"ctime":"2026-03-21T20:44:54.918+01:00","mtime":"2026-11-26T21:53:26.052+01:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/HOUDINI]]","[[3_GARDEN/MOCs/SOLARIS|Solaris]]"],"source":["[[3_GARDEN/Notes littéraires/Cours Houdini semaine 3]]"],"Projets":null,"tags":["note_permanente","MOC"],"creation date":"2026-10-26","aliases":null,"banner":"https://i.imgur.com/3k4TDUs.jpeg"}}
---

# Définition


> [!quote]+ Yann Pannetier
> En 2016, le studio Pixar a mis à disposition en open-source son langage de description de scène, l’USD - pour Universal Scene Description, utilisé en production depuis
> de nombreuses années. 
> 
> Ce format permet de stocker tous les types d’informations 3D et surtout d’organiser la chaîne de production (le pipeline) de façon très structurée, dynamique, en facilitant
> la collaboration entre départements (modeling, lookdev, animation, lighting, rendering).
> 
> - C’est un système de layers non-destructif, Chaque fichier USD (car l’USD est aussi un format) est un layer, et peut comporter une “scène” complète où l’on peut importer d’autres fichiers USD.
> - Un layer est un fichier USD écrit sur le disque. Un Sub-layer est une des composantes de ce layer 
> 


USD veut dire *Universal Scene description* : Qu’importe le moteur de rendu, l’USD est une description de scène universelle

> [!success]+ Intérêt de l'USD : 
> - Le partage de fichiers dans de grandes productions est extrêmement plus efficace car on a un seul type de fichier pour tout, qui en plus est non propriétaire donc potentiellement compatible avec tout. 
> - On peut faire des références à l’infini. Ce qui fait que les fichiers peuvent être extrêmement petits (quelques ko), référençant constamment en chaîne des choses sur le disque. Tout est cloisonné en plein de petits bouts. Le procédurale est donc au centre de la philosophie et la propreté et le cloisonnage des étapes est bien plus simple à gérer à de grosses échelles de production

On voit donc avec tout ça l'importance d'une organisation très solide avec nommage ultra carré

Dans l’USD, tout est stocké sur le disque 
- Tout doit être disponible sur le disque, utilisable depuis n’importe quel logiciel ou même sans (juste en ligne de commande pour lancer des rendus sur des farms par exemple)

#### Terminologie 

**[[3_GARDEN/MOCs/SOLARIS\|SOLARIS]]** : L'ensemble d'outils Houdini dédiés à la création de scènes, à l'éclairage, à la mise en scène et au pipeline. C'est là que nous pouvons effectuer le rendu via les délégateurs Hydra.
- **Stage** : Nom du contexte Houdini dans lequel nous utilisons les nœuds LOP propres à Solaris
- **LOPs** : Nom désignant l'ensemble des nœuds/outils utilisés pour travailler avec USD dans Solaris.

#### Formats et Extensions

Extensions de fichiers usd : 

| **Extension** | **Format**      | **Commentaires**                                                                                                                                                                                                                                                        |
| ------------- | --------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **.usd**      | Binaire / ASCII | Le format par défaut, binaire : Ces fichiers offrent des lectures plus rapides et des tailles réduites, mais ne sont pas lisibles par un humain. Ils sont idéaux pour de grandes scènes contenant un nombre élevé d'objets géométriques.                                |
| **.usda**     | ASCII           | Ces fichiers entraînent des lectures plus lentes et des fichiers plus volumineux, mais présentent l'avantage d'être lisibles par un humain. Ils peuvent être utilisés pour de petites scènes ou des _assets_, et s'avèrent très utiles pour déboguer des problèmes.<br> |
| **.usdc**     | Binaire         | Format strictement binaire                                                                                                                                                                                                                                              |


Dans le cas de l'extension `.usd`, le format est enregistré en Binaire (« Crate ») par défaut. Si vous souhaitez enregistrer votre fichier `.usd` en ASCII, vous devez ajouter le a à l'extension


# Structure

#### Généralités

[[3_GARDEN/Notes permanentes/Primitive USD\|Primitive USD]] : comment les éléments de l'usd sont classés et organisés
[[3_GARDEN/MOCs/SOLARIS\|SOLARIS]] : L'espace où on gère tout ce qui est relatif à l'USD dans Houdini

---
#### Importation d'éléments dans Solaris

[[3_GARDEN/Notes permanentes/Importation dans Solaris\|Importation dans Solaris]]
- (*[[3_GARDEN/Notes permanentes/MAYA USD Export\|MAYA USD Export]]*)
- [[3_GARDEN/Notes permanentes/Geometry subset\|Geometry subset]]

[[3_GARDEN/Notes permanentes/Créer et gérer des USD animés\|Créer et gérer des USD animés]]

Les données plus profondes contenues dans l'USD : [[3_GARDEN/Notes permanentes/USD Schemas and Primvars\|USD Schemas and Primvars]]

---
#### USD Asset Creation

- [[3_GARDEN/Notes permanentes/Component Builder\|Asset USD]]
	- [[3_GARDEN/Notes permanentes/Créer des variants avec le component builder\|Créer des variants avec le component builder]]
	- [[3_GARDEN/Notes permanentes/LOD\|LOD]] 

*Pour aller plus loin :* 
- [[3_GARDEN/Notes permanentes/Setup une géo pour l'USD avec Solaris\|Setup une géo pour l'USD avec Solaris]]
- *[[3_GARDEN/Notes permanentes/USD Variants\|USD Variants]]* 
- *[[3_GARDEN/Notes permanentes/USD Purpose\|USD Purpose]]* 
- *[[3_GARDEN/Notes permanentes/ASWF\|ASWF]]*

---
#### USD set dress et layout

Une notion extrêmement importante : [[3_GARDEN/Notes permanentes/USD Layers\|USD Layers]]
- Force des layers les uns par rapport aux autres : [[3_GARDEN/Notes permanentes/USD Opinions and strength\|USD Opinions and strength]]

[[3_GARDEN/Notes permanentes/Techniques pour répartir un asset avec des variants dans un set - Solaris\|Techniques pour répartir un asset avec des variants dans un set - Solaris]]

Les différents nodes pour construire un set dans [[3_GARDEN/MOCs/SOLARIS\|SOLARIS]] : 
- [[3_GARDEN/Notes permanentes/Merge LOP\|Merge LOP]] 
- [[3_GARDEN/Notes permanentes/Duplicate LOP\|Duplicate LOP]]
- [[3_GARDEN/Notes permanentes/Instancer LOP\|Instancer LOP]] 

---
#### Annexes

Règles de sélections : [[3_GARDEN/Notes permanentes/Collections & Règles de Sélection en USD\|Collections & Règles de Sélection en USD]]
Node Solaris pour gérer le stage entier : [[3_GARDEN/Notes permanentes/Stage Manager LOP\|Stage Manager LOP]]

Importer dans SOP des éléments du LOP : [[3_GARDEN/Notes permanentes/LOPs to SOPs\|LOPs to SOPs]] 

---

# Ressources


- [USD Basics with Solaris \| SideFX](https://www.sidefx.com/tutorials/usd-basics-with-solaris/)
- [LOPs for Solo Artists - YouTube](https://youtu.be/WfC16LYYIAw?si=QeNJYXRO0nbNTAvi)
- [Introduction - Usd Survival Guide](https://lucascheller.github.io/VFX-UsdSurvivalGuide/)

- [USD Home — Universal Scene Description 26.08 documentation](https://openusd.org/release/index.html)
- [LOPs and USD Glossary](https://www.sidefx.com/docs/houdini19.5/solaris/glossary.html)


