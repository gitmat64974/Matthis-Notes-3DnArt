---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Raccourcis Houdini les plus utiles/","tags":["note_permanente"],"dg-note-properties":{"MOC":["[[HOUDINI]]"],"source":["[[Cours Houdini semaine 3]]"],"Projets":null,"tags":["note_permanente"],"creation date":202510132311,"aliases":null}}
---

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

## Références


#### Autres tools et raccourcis : 
- [[TOOLS/Houdini scripts/Import Textures|Import Textures]]


> [!example]- Flashcards
> ...




## Liens 
