---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/USD Layers/","tags":["note_permanente"],"ctime":"2026-11-24T15:05:32.002+01:00","mtime":"2026-11-24T15:10:31.649+01:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/USD]]"],"source":["[[3_GARDEN/Notes littéraires/USD - SideFX Course]]"],"Projets":null,"tags":["note_permanente"],"creation date":"2026-11-24","aliases":null,"banner":"https://images.unsplash.com/photo-1580477667929-3ef27c684b7a?q=80&w=1470&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=NHwxMjA3fDA%3D"}}
---

## La note 

Un layer est un conteneur de données (souvent un fichier indépendant comme `.usd`, `.usda` ou `.usdc`) qui contient soit la création d'éléments 3D, soit des modifications non destructives apportées à ces éléments.

> [!quote]+ Le principe : l'empilement non destructif
> Dans un workflow 3D traditionnel, si le département « Lighting » veut changer la couleur d'un objet créé par le « Modeling », il doit souvent dupliquer la scène ou écraser le fichier source.
> 
> En USD, on procède par empilement :
> 1. **Layer de base (Modeling) :** Définit la forme géométrique d'une voiture (ex. `/World/Car`).
> 2. **Layer supérieur (Shading) :** Ne recrée pas la géométrie, il ajoute simplement : « _sur `/World/Car`, applique ce matériau de carrosserie rouge_ ».
> 3. **Layer de Shot (Lighting / Layout) :** Décide d'uniquement modifier la couleur : « _remplace le rouge par du bleu et déplace la voiture de 2 mètres à gauche_ ».
> 
> Le résultat visible dans le viewport est la composition de toutes ces couches empilées selon un ordre de priorité précis.

#### Ce que contient un layer

Un layer ne stocke pas obligatoirement une scène complète. Il peut contenir :

- **Des définitions complètes :** Une géométrie, des caméras, des lumières.
- **Des deltas (ou « over ») :** Uniquement la différence ou la modification d'un paramètre (une translation, un changement d'intensité d'une lumière, un masquage de primitive).
- **Des références à d'autres layers :** L'assemblage d'autres fichiers via des sous-couches (_sublayers_).
    
#### Dans Solaris (Houdini)

Dans le contexte LOPs / Solaris :
- **Chaque nœud génère ou modifie un layer :** Quand tu poses un nœud (par exemple pour déplacer un objet ou assigner un shader), Solaris ne détruit pas le modèle en mémoire ; il écrit une opinion/modification sur un layer actif.
- **Le panneau Scene Graph Layers :** Il te permet de voir visuellement la pile de layers USD empilés pour former la scène finale, et d'isoler ou muter un calque spécifique pour voir son impact sans toucher au fichier d'origine. Plus un layer est haut, plus il est fort
- **Les couleurs autour des nodes** : Dans Solaris, les nodes qui ont la même couleur de contour appartiennent au même layer (la couleur est assignée random)
- **Dans un usd ROP** : on peut choisir de flatten les layers (écraser et créer donc qu'une seul fichier) ou de les séparer (donc créer plusieurs fichiers usd)

#### L'overide en USD

Si on remplace un élément dans Solaris par un autre exactement au même endroit et d'exactement le même type, on peut overide cet élément.

**C'est comme cela qu'on va faire l'équivalent de l'[[3_GARDEN/Notes permanentes/Alembic Merge\|Alembic Merge]] en USD**. ***L'avantage est que ce n'est pas limité à de la géométrie, on peut le faire avec absolument tout et n'importe quoi. En plus, c'est totalement non destructif et procédural.***

Exemple : 
1. On a un asset usd complet avec matériaux etc
2. On crée ensuite un matériau dans un material library
3. Ce matériau on le place (chemin du destination primitive) exactement à la place du matériau de l'asset

###### Exemple du cas "alembic merge" : 

| ![Capture d'écran 2026-11-08 221141.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202026-11-08%20221141.png) | ![Capture d'écran 2026-11-08 221208.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202026-11-08%20221208.png) |
| ------------------------------------------ | ------------------------------------------ |
| l'Asset USD avec shaders et textures       | L'anim de la géo uniquement                |

le scene graph de la géo animée : 
```text
- Pig_anim
	- PigEyes
	- PigFace
	- PigNeck
	- PigThroat
```

Le setup : 

![Capture d'écran 2026-11-08 221709.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202026-11-08%20221709.png)


#### Layer break LOP

Il vient dire à Houdini que tout ce qu'il y a après ce node est dans un nouveau layer et que tous les layers précédents ne vont pas être 

Exporter en USD dans ce cas : 
- Avant chaque layer break on peut donc **usd ROP en mode flatten layers** pour save chaque layer sur le disk 

Si on veut exporter uniquement avec un usd ROP à la fin : 
- **mode flatten** : tout sort dans un seul fichier usd
- **mode separate layers / décoché strip layers above layer names** : tout sort dans des usd différents, référencés, mais c'est tout le stage qui est éclaté à l'export, chaque layer de base plus les layers définis par les layers break. ça export aussi un master usd qui référence tout le reste comme il faut. 
- **mode separate layers / coché strip layers above layer names** : là ça ignore tout ce qui est au dessus des layers break donc ça va surement exporter un usd avec rien du tout dedans

Importer un layer : node sublayer

#### Configure layer LOP

*Alternative très intéressante au layer break LOP pour construire un stage avec des layers*

![Capture d'écran 2026-10-16 151413.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202026-10-16%20151413.png)

Il fait exactement la même chose que le layer break LOP mais permet en plus de spécifier un chemin d'export, donc pas besoin de mettre un usd ROP spécifiquement après. 

Chemin conseillé : 
- Master usd file
- Folder (name : layers)
	- $OS.usd

*Ce node là crée un layer à partir de ce qui le précède, à l'inverse du layer break*

Paramètres : 
- Also Set Metadata on Stage Root Layer : vient dire que ce layer est le root. généralement que le premier layer
- Flatten input : mode de flatten. En général on ne flatten que le premier layer car on ne veut pas que les suivants écrasent et donc contiennent les précédents. En cochant do not flatten on ne garde que ce qu'il y a après le précédent Configure Layer LOP
- Start new layer : à quasiment toujours cocher -> créer un nouveau layer à la suite
- Set Input Active Layer to Explicit : à toujours cocher. Cela vient indiquer à solaris qu'on veut explicitement définir ce layer

*Le nom du layer est d'ailleurs le nom donné au node*

> [!success]+ USD ROP à la fin du stage :
> ***Cet usd ROP va exporter chaque layer défini dans les configure layer LOPs ainsi qu'un master usd file qui référence chacun des layers ***
> 
> Paramètres : 
> - Save style : Flatten implicit layers. Comme ça tous les layers implicit seront écrasés et seulement les layers explicites, donc définis avec les configure layer LOP seront exportés
> - Output processors : 
> 	- Match Output Layer Extension
> 	- Use Relative Paths
> 
> ![Capture d'écran 2026-10-16 152653.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202026-10-16%20152653.png)
> 
> Import ensuite : 
> On peut donc ensuite juste importer le master avec un sublayer LOP et tout va s'importer, ou importer un seul layer avec un sublayer LOP si besoin




## Références

Force des layers les uns par rapport aux autres : [[3_GARDEN/Notes permanentes/USD Opinions and strength\|USD Opinions and strength]]

> [!example]- Flashcards
> ...




## Liens 




