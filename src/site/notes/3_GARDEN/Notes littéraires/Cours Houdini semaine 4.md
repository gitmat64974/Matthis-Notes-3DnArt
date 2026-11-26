---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes littéraires/Cours Houdini semaine 4/","tags":["note_litteraire","cours"],"ctime":"2026-03-21T20:44:15.323+01:00","mtime":"2025-10-13T23:40:57.266+02:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/HOUDINI]]"],"source":["[[3_GARDEN/Notes littéraires/Cours houdini ESMA]]"],"Projets":null,"tags":["note_litteraire","cours"],"creation date":"2025-10-13"}}
---


### Construction d’un Set dans Houdini

Au _Scene Level_, créer un node **LOP Network**

> [!Tip] Attention
> Dans _Maya_, l’organisation du _scenegraph_ est modifiable manuellement. Avec l’USD, il convient de prévoir à l’avance comment sera structuré ce _scenegraph_.
> 

Le *scenegraph* est en quelque sorte comme l’outliner
Un _scenegraph_ bien organisé est un gage de sérénité lors du rendu

> [!Abstract]+ Node primitive :
> 
> ```c
> /set_canyon
> /set_canyon/terrain
> /set_canyon/mineral
> /set_canyon/vegetation
> ```
> 
> - _Primitive Type_ = **`Scope`**.

Le scenegraph devra ensuite ressembler à ça

![IMG_1294.png](/img/user/Pi%C3%A8ces%20jointes/IMG_1294.png)

Référencer un asset USD :

> [!Abstract]+ Node Asset Reference
> - _Destination Primitive_ : où on va stocker dans le scenegraph
> - Onglet _**Reference**_ :
>     - _Reference File_ : aller chercher l’asset usd
> 
> Noeud instancer pour instancer des assets usd

> [!Abstract]+ Noeud instancer avec exemple
> - **Instancer** “instancer_blocs” :
>     - _Primitive Path_ : `/rochers/instances` _C’est l’endroit où seront rangé les instances dans le_ scenegraph
>     - Bloc déroulant _Target Points_ : _Définit les points à utiliser pour le scattering._
>         - _Location Source_ : **`External SOP`**
>         - _Sop Path_ : `/obj/scatter_rochers/POINTS_DE_DUPLICATION`
>     - Bloc déroulant _Prototypes_ :
>         - _Prototype Primitives_ : `/rochers/blocs/**` _Définit les primitives à dupliquer. La double étoile permet d’importer l’ensemble de l’asset, y compris le shader._
>         - _Prototype Source_ : **`First Input`**
>         - Sous-bloc déroulant _Options_ :
>             - _Prototype Index_ : **`Name Attribute`**
>             - _Name Attribute_ : `name` _Cela va permettre d’associer les blocs aux points en fonction de leurs noms respectifs._
> 
> 

Noeud pour “merge” les assets dans le set :

> [!Abstract]+ Noeud Graft Branch
> 
> - _Primitive Path_ : primitive path du 2e input
> - _Source Prim Path_ : path de ce qu’il y a à “ajouter” au set _En cas de doute, utiliser_ Ctrl-Icône Flèche _(à droite du paramètre) pour choisir la primitive à greffer dans une fenêtre dédiée._
> 
> ![IMG_1295.png](/img/user/Pi%C3%A8ces%20jointes/IMG_1295.png)


> [!Abstract]+ Noeud **USD ROP →** Export du set
> Rentrer l’output file puis cliquer sur save


