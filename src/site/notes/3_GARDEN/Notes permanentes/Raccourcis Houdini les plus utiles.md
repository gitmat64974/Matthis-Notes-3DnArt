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
> > # Script Python pour créer un Object Merge depuis les nœuds sélectionnés
> import hou
> 
> selected = hou.selectedNodes()
> for node in selected:
>     parent = node.parent()
>     # Crée un object merge
>     merge = parent.createNode("object_merge", node.name() + "_merge")
>     # Positionne le nœud juste en dessous
>     merge.setPosition(node.position() + hou.Vector2(0, -1.5))
>     # Insère le chemin relatif
>     merge.parm("objpath1").set(merge.relativePathTo(node))
>     merge.setSelected(True, clear_all_selected=False)
> ```
> 
> *Rappel de comment faire : Créer un nouveau shelft tool, en le créant rentrer ce script et assigner un raccourci, celui qu'on veut*



## Références


> [!example]- Flashcards
> ...




## Liens 
