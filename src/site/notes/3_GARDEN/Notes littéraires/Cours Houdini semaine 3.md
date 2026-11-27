---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes littéraires/Cours Houdini semaine 3/","tags":["note_litteraire","cours"],"ctime":"2026-03-22T12:15:21.190+01:00","mtime":"2026-11-23T23:29:06.281+01:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/HOUDINI]]"],"source":["[[3_GARDEN/Notes littéraires/Cours houdini ESMA]]"],"Projets":null,"tags":["note_litteraire","cours"],"creation date":"2025-10-06","cssclasses":["clean-embeds"]}}
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




</div></div>
 

### Créer un asset USD dans Houdini


<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/3_GARDEN/Notes permanentes/Component Builder/#la-note" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">



## La note 

Le component builder créée un ensemble de nodes nécessaires à la création simple et complète d'un asset USD : 
- référencer la géo
- créer et assigner des shaders
- exporter l'asset USD

![Capture d'écran 2026-11-01 213928.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202026-11-01%20213928.png)

La hiérarchie des fichiers exportés par le component builder : 

![Capture d'écran 2026-11-01 214439.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202026-11-01%20214439.png)

*-> [[3_GARDEN/Notes permanentes/Payload\|Payload]]*

---
#### Component geometry

3 modes pour importer la géo : 
- **Internal SOP** : Entrer à l'intérieur pour setup la geo de render, et si on veut la geo proxy et la geo simproxy. ->*Le mode préférable*. Voir -> [[3_GARDEN/Notes permanentes/Setup une géo pour l'USD avec Solaris\|Setup une géo pour l'USD avec Solaris]]
- **File** : fichier référencé
- **External SOP** : chemin dans un SOPNet externe

On va donc avoir la possibilité de setup 3 "versions" de la géo en mode internal SOP (*le plus simple est d'entrer à l'intérieur du node*) : 
- **default / render** (*Obligatoire*) : Geo de rendu
- **Proxy** (*Optionnelle*) : Geo allégée pour la rapidité du viewport
- **SimProxy** (*Optionnelle*) : Si on veut avoir le contrôle sur la géo de proxy utilisée dans les outils de physics de solaris (comme l'edit LOP, le layout LOP etc)

---

#### Component material

Construire le shader dans le material library (Souvent un [[3_GARDEN/Notes permanentes/Mtlx Shader\|Mtlx Shader]])

Puis le component material va assigner automatiquement le shader qui vient de la deuxième entrée à la géo qui vient de la première
Le matériau va être nommée en fonction du nom qu'on donne au node 

Mode manuel : 
*S'il y a plusieurs shaders, ou des variants etc on va devoir les assigner à la main*

---
#### Component output

Assez simple, gère tout l'output de l'asset
- Root prim : nom de la primitive qui contiendra la geo et les shaders
- Location dans caching : l'endroit où l'asset sera sauvegardé sur le disque
- Cliquer sur save to disk

Thumbnail : permet de générer une image thumbnail de présentation de l'asset (super utile pour les bibliothèques d'asset etc)


> [!info]+ Hiérarchie des fichiers d'un asset usd : (par exemple ici un pig_head.usd)
> - Le pig_head.usd vient charger le payload.usd
> - Le payload.usd vient charger ensuite le geo.usd et mtl.usd

*A noter qu'on peut rentrer dans le component output pour mettre des nodes spéciaux de traitement comme un rendergeometrysettings pour gérer la subdivision au rendu par exemple*

---


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
 

