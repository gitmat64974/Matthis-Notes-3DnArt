---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Créer des variants avec le component builder/","tags":["note_permanente"],"ctime":"2026-11-03T20:02:00.051+01:00","mtime":"2026-11-05T21:36:18.134+01:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/SOLARIS|Solaris]]","[[3_GARDEN/MOCs/HOUDINI]]","[[3_GARDEN/MOCs/USD]]"],"source":null,"Projets":null,"tags":["note_permanente"],"creation date":"2026-11-03","aliases":null}}
---

## La note 

### Material Variants

On a juste à créer plusieurs shaders dans le material library puis à faire autant de component material nécessaires

![Capture d'écran 2026-11-03 103607.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202026-11-03%20103607.png)

Variant name : le nom du node component material 

Dans le component output, on peut ensuite si on veut dire quel est le defaut variant pour la geo et pour le mtl. Si ce n'est pas setup, ce sera tout simplement le dernier de la liste

---
### Geo + Material Variants

On 2 méthodes qui vont produire des résultats différents : 
1. Variants de géo et de matériaux indépendants : *permet de mettre n'importe quel variant de mtl sur n'importe quelle géo*
2. Variants de géo et de matériaux liés : *permet de simplement sélectionner un variant de géo et d'avoir tous ses shaders bien assignés*

#### Méthode 1

On va simplement combiner les deux méthodes précédents : Geometry variants et material variants

Ici il ne faut donc pas penser qu'on assigne des shaders en fonction des variants de géo mais plutôt de manière générale, comme s'il n'y avait pas de variants de géo

![Capture d'écran 2026-11-03 224216.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202026-11-03%20224216.png)

*Avec 3 variants de géo et 3 variants de mtl on peut donc créer 9 variants !*

Dans le component output : 
- Variant Layers : 
	- Variant set : geo ou mtl


#### Méthode 2


*On va chercher ici à Attacher un matériau à une géo dans les variants dans le but d'avoir des variants à la fois de geo mais aussi de mtl*

Il suffit simplement de mettre un ``component material`` juste après chaque ``component geometry`` puis de rentrer tout ça dans un ``component geometry variants``. 

Les variants seront donc sur la geo mais avec un mtl en overides pour chaque geo

![Capture d'écran 2026-11-03 164937.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202026-11-03%20164937.png)

Le network typique : 

![Capture d'écran 2026-11-03 211943.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202026-11-03%20211943.png)

Dans le component output : 
- Variant Layers : 
	- Variant set : geo ou mtl

-> *Sans faire cela, l'asset overide tous les layers de matériau avec celui du dernier variant*




## Références

[[3_GARDEN/Notes permanentes/Techniques pour répartir un asset avec des variants dans un set - Solaris\|Techniques pour répartir un asset avec des variants dans un set - Solaris]]

#### Ressources

- [H20.5 Foundations \| Solaris Market 2 \| Create Assets with Variants - YouTube](https://youtu.be/ggV2boEfHzM)

> [!example]- Flashcards
> ...




## Liens 




