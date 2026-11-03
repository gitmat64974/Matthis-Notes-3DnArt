---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Techniques pour répartir un asset avec des variants dans un set - Solaris/","tags":["note_permanente"],"dg-note-properties":{"MOC":["[[HOUDINI]]","[[Lighting dans Houdini|Solaris]]","[[USD]]"],"source":null,"Projets":null,"tags":["note_permanente"],"creation date":"2026-11-03","aliases":null}}
---

## La note 

*On va utiliser les techniques classiques de solaris pour instancer des assets : instancer, copy and transform, layout etc*

### 1. Copy and transform

![Capture d'écran 2026-11-03 212645.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202026-11-03%20212645.png)

1. **Asset reference** : on reference l'asset
2. **Copy and transform** : pour le dupliquer en référence
3. **Set Variant** : permet de venir prendre une instance et de changer le variant de cette instance. On peut également faire un random global avec ce node en se mettant en mode variant name by index et en mettant ce genre d'expression dans le variant name index : `floor(rand(@prim) * @numvariants)`
4. **Edit** : permet d'appliquer autant de transformations qu'on veut aux instances dans un seul node. Il permet également d'effectuer des transformations avec le mode physic activé, c'est à dire que les objets vont se collide naturellement si ils se touchent

### 2. Instancer

![Capture d'écran 2026-11-03 213242.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202026-11-03%20213242.png)

1. **Asset reference** : on reference l'asset
2. **Explore variant** : pour récupérer chaque variant sous forme de primitive usd séparée
3. **Instancer** : On met chaque variant comme Prototype primitive puis on met le prototype index en mode random : les variants sont randomize sur les points. *Pour encore plus de contrôle, on peut bien sur gérer le randomize avec un attribute randomize name sur les points en SOP, à l'intérieur de l'instancer ou en externe*. 
4. **Set Variant** : Si on veut précisément changer le variant d'une instance précisément après coup

### 3. Layout

Le node Layout permet un placement d'asset très user friendly (différents brushs etc). 
On peut soit ``set variant`` en random par la suite ou référencer chaque variant dans l'asset catalog du node

---

## Références


> [!example]- Flashcards
> ...




## Liens 




