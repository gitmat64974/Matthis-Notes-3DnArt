---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes littéraires/Cours Houdini semaine 3/","tags":["note_litteraire","cours"],"ctime":"2026-03-21T20:44:16.016+01:00","mtime":"2026-10-02T21:39:38.054+02:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/HOUDINI]]"],"source":["[[3_GARDEN/Notes littéraires/Cours houdini ESMA]]"],"Projets":null,"tags":["note_litteraire","cours"],"creation date":"2025-10-06","cssclasses":["clean-embeds"]}}
---


Quaternion : vecteur à 4 dimensions / coordonnées 
-> [[3_GARDEN/Notes permanentes/Quaternion\|Quaternion]]
### Raccourcis Houdini



<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/3_GARDEN/Notes permanentes/Raccourcis Houdini les plus utiles/#la-note" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">



## La note 

Raccourci d’UI : Shift S -> Changer le style des connections des noeuds. 

- **L** : Réorganiser les noeuds automatiquement
- **D** : Pour ouvrir les display options dans le viewport (permet notamment d'augmenter le "floating gnomon size").,
- **R** sur un node : voir son résultat
- **Espace + H** : Pour centrer le viewport.,
- **Espace + F ou G** : Aussi pour centrer le viewport.,
- **W et / ou Shift + W** : Pour le wireframe.,
- **Alt + Clic sur le nom ou le paramètre** : Pour mettre une clé d'animation.,
- **Shift + Clic sur un paramètre** : Ouvre l'animation editor.

Dans le viewport : X → menus de snap

Créer un merge : 
- **Maintenir Alt :** Sélectionnez plusieurs nœuds, maintenez la touche `Alt` enfoncée, puis cliquez et faites glisser à partir de la sortie de l'un des nœuds sélectionnés vers le bas

Créer un object merge à partir du node sélectionné : 

> [!example]- Snippet de code pour créer un object merge à partir du node sélectionné
> ```python
import hou
> 
> network = hou.ui.curDesktop().paneTabUnderCursor()
> networkpath = network.pwd().path()
> pos = network.cursorPosition()
> 
> clipboard = hou.ui.getTextFromClipboard()
> 
> n = 0
> 
> if clipboard:
>     list = clipboard.split()
>     for item in list:
>         if hou.node(item) != None:
>             merge = hou.node(networkpath).createNode('object_merge','merge_'+item.split('/')[-1])
>             merge.parm('objpath1').set(str(item))
>             merge.setPosition(pos)
>             merge.move([n*2,0])
>             if n == 0:
>                 merge.setSelected(True,True)
>             else:
>                 merge.setSelected(True,False)
>             n = n + 1
> ```
> 
> *Rappel de comment faire : Créer un nouveau shelft tool, en le créant rentrer ce script et assigner un raccourci, celui qu'on veut*

Créer un node transform à partir du node sélectionné : 

> [!example]- Snippet de code pour créer un node transform à partir du node sélectionné
> ```python
> import hou
> 
> # 1. Récupérer les nœuds actuellement sélectionnés
> selected_nodes = hou.selectedNodes()
> 
> if selected_nodes:
>     # On prend le premier nœud de la sélection
>     selected_node = selected_nodes[0]
>     
>     # On identifie le réseau (parent) dans lequel on se trouve
>     parent_node = selected_node.parent()
>     
>     # 2. Créer le nœud Transform dans ce même réseau
>     transform_node = parent_node.createNode('xform')
>     
>     # 3. Connecter le Transform à la sortie du nœud sélectionné
>     transform_node.setInput(0, selected_node)
>     
>     # 4. Ajuster la position visuelle et les flags
>     transform_node.moveToGoodPosition() # Place le nœud proprement en dessous
>     transform_node.setDisplayFlag(True)
>     transform_node.setRenderFlag(True)
>     
>     # (Optionnel) Sélectionner le nouveau nœud à la place de l'ancien
>     selected_node.setSelected(False)
>     transform_node.setSelected(True)
>     
> else:
>     # Message d'erreur si rien n'est sélectionné
>     hou.ui.displayMessage("Veuillez d'abord sélectionner un nœud.")
> ```


</div></div>
 

### USD


<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/3_GARDEN/MOCs/USD/#la-note" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">





# Cartographie


# Définition

Qu'est ce que l'USD ?
C'est un format de fichier assez différent du fbx, obj, abc etc

En réalité ce n’est pas à proprement parler un format mais c'est plutôt une description de scène où on peut stocker n’importe quoi (géo, textures, matériaux, lights, caméras, rendersettings etc)

USD veut dire *Universal Scene description* : Qu’importe le moteur de rendu, l’USD est une description de scène universelle

> [!success]+ Intérêt de l'USD : 
> - Le partage de fichiers dans de grandes productions est extrêmement plus efficace car on a un seul type de fichier pour tout, qui en plus est non propriétaire donc potentiellement compatible avec tout. 
> - On peut faire des références à l’infini. Ce qui fait que les fichiers peuvent être extrêmement petits (quelques ko), référençant constamment en chaîne des choses sur le disque. Tout est cloisonné en plein de petits bouts. Le procédurale est donc au centre de la philosophie et la propreté et le cloisonnage des étapes est bien plus simple à gérer à de grosses échelles de production

On voit donc avec tout ça l'importance d'une organisation très solide avec nommage ultra carré

Dans l’USD, tout est stocké sur le disque 
- Tout doit être disponible sur le disque, utilisable depuis n’importe quel logiciel ou même sans (juste en ligne de commande pour lancer des rendus sur des farms par exemple)


Petit historique : 
L'usd était un format propriétaire de Pixar qu’ils ont révisé en open source en 2016. C’est une évolution du RIB. 


# Structure


- [[3_GARDEN/Notes permanentes/Créer un asset USD dans Houdini\|Créer un asset USD dans Houdini]]

*Solaris est un logiciel qui a été construit autour de l’USD*


#### USD Asset Creation

- [[3_GARDEN/Notes permanentes/Component Builder\|Component Builder]]
	- [[3_GARDEN/Notes permanentes/Créer des variants avec le component builder\|Créer des variants avec le component builder]]

### USD set dress et layout

[[3_GARDEN/Notes permanentes/Techniques pour répartir un asset avec des variants dans un set - Solaris\|Techniques pour répartir un asset avec des variants dans un set - Solaris]]


# Appropriation et réflexions 

#### Réflexions


#### Essais





# Ressources


- [USD Basics with Solaris \| SideFX](https://www.sidefx.com/tutorials/usd-basics-with-solaris/)
- [LOPs for Solo Artists - YouTube](https://youtu.be/WfC16LYYIAw?si=QeNJYXRO0nbNTAvi)
- [Introduction - Usd Survival Guide](https://lucascheller.github.io/VFX-UsdSurvivalGuide/)






</div></div>
 

### Créer un asset USD dans Houdini


<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/3_GARDEN/Notes permanentes/Créer un asset USD dans Houdini/#la-note" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">



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



</div></div>
 

### Flipbook Houdini


<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/3_GARDEN/Notes permanentes/Flipbook Houdini/#la-note" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">



## La note 

*Rappels : Pour créer une clé d’animation : Alt-LMB sur un paramètre*

##### 1. Calculer le filpbook

À l’aide d’un _RMB_ sur l’icône de carnet située en bas à gauche du _Viewport_, cliquer sur _Flipbook with New Settings_ pour ouvrir la fenêtre _Render Flipbook_. Dans celle-ci :
- Onglet _**Size**_ :
    - _Resolution_ = `1920` x `1080`
- Cliquer sur le bouton **`Start`** pour lancer le calcul d’un _Flip Book_ (équivalent à un _playblast_ de Maya).

Une nouvelle application s’ouvre, le _MPlay_, qui concatène les images. 

##### 2. Exporter le flipbook

Une fois le calcul terminé, ouvrir le menu _File_, et choisir _Export / FFmpeg_ :
- _Output File_ : Choisir un chemin et un nom de fichier, en conservant bien l’extension .mp4 à la fin.
- _Quality =_ 100
- Cliquer sur **`Save`**.

----

### Faire un Flipbook en max res 

Il ne faut pas passer par le viewport mais par le context out et là on crée un node flipbook. Tout fonctionne pareil avec des paramètres en plus et la résolution pourra ici enfin être au max


</div></div>
 

