---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes littéraires/4e cours CFX/","tags":["note_litteraire","cours"],"dg-note-properties":{"MOC":["[[HOUDINI]]","[[CFX]]"],"source":["[[Cours CFX ESMA]]"],"Projets":null,"tags":["note_litteraire","cours"],"creation date":"2025-11-07"}}
---



## HDA


<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/3_GARDEN/Notes permanentes/HDA/#la-note" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">



## La note 

[Digital assets](https://www.sidefx.com/docs/houdini/assets/index.html)

Houdini digital asset : groupe de node qu'on peut grouper et export / importer comme un gizmo dans nuke

Asset -> install asset library : pour importer un hda (digital asset)

#### Modification HDA

Attention à bien modifier le layout des paramètres dans la fenetre type properties et pas dans edit parameter interface


#### Embed des fichiers directement dans l'HDA : 

###### 1. L'ajouter à l'Asset

1. Clic droit sur l'asset > **Type Properties**.
2. Onglet **Extra Files** > Naviguez et ajoutez votre fichier (texture, géo, etc.).

###### 2. L'utiliser (Le chemin)

Pour que Houdini lise le fichier interne, utilisez cette syntaxe courte dans vos paramètres :

> `opdef:.?nom_du_fichier.extension`

- **Le `.`** signifie "cet asset".
- **Le `?`** sépare l'asset du fichier interne.

-> [Edit an asset’s user interface](https://www.sidefx.com/docs/houdini/assets/asset_ui.html)



</div></div>
 

## Node Attribute VOP


<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/3_GARDEN/Notes permanentes/Node Attribute VOP/#la-note" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">



## La note 

C en gros un wrangle mais visuel, sans besoin de coder. 

Il faut rentrer dedans pour l'utiliser
(C'est un peu comme le node graph d'unreal)

> [!tip]+ Fonction promote
> Clic droit sur un paramètre (sur le node directement ou roud dentée à coté du paramètre dans le node properties) -> promote parameter : permet d"amener un paramètre au niveau supérieur". En gros ça va afficher le paramètre en question sur le node du niveau au dessus, ce qui permet de ne pas avoir besoin de rentrer de le node et chercher le paramètre à chaque fois 
> 
> #### Modifier ses paramètres : 
> Entrer dans l'interface de paramètres : 
> 
> ![Capture d'écran 2025-11-07 152056.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202025-11-07%20152056.png)
> Renommer, mettre des dossiers etc et cela va modifier la parameter window du node. 
> Par exemple : 
> ![](https://i.imgur.com/skpSDYl.png)
> Cela donne : 
> ![Capture d'écran 2025-11-07 152304.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202025-11-07%20152304.png)

#### Exemple d'utilisations

##### Noise sur la position des points d'une grid : 

![](https://i.imgur.com/cD2Qn4B.png)


##### Animation procédurale

**Le but est de remplacer une simulation vellum par une animation procédurale**

> [!example]+ Setup de base pour ocean ou drapeau procedural
> Noeuds de base : grid -> remesh -> attribute vop
> 
> ![Capture d'écran 2025-11-07 151816.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202025-11-07%20151816.png)
>



</div></div>
  



