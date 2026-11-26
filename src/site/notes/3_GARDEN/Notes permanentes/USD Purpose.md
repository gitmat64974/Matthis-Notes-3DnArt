---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/USD Purpose/","tags":["note_permanente"],"ctime":"2026-11-26T10:59:27.186+01:00","mtime":"2026-11-26T11:00:04.762+01:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/USD]]","[[3_GARDEN/MOCs/SOLARIS]]"],"source":["[[3_GARDEN/Notes littéraires/USD - SideFX Course]]"],"Projets":null,"tags":["note_permanente"],"creation date":"2026-11-26","aliases":null}}
---

## La note 

Dans Houdini Solaris (et plus largement dans le format USD - Universal Scene Description), le **Purpose** (l'objectif ou la finalité) est un attribut fondamental utilisé pour catégoriser la géométrie selon le contexte dans lequel elle doit être affichée.

L'intérêt principal du Purpose est la **performance**. Il permet de stocker dans un même fichier USD à la fois des modèles ultra-détaillés pour le rendu final et des versions allégées pour garder un viewport (la vue 3D) fluide, le système basculant automatiquement de l'un à l'autre.

Il existe **4 catégories standard** de Purpose en USD :

* **Default (Par défaut) :** La géométrie s'affiche partout, aussi bien dans le viewport qu'au rendu. C'est le comportement de base si aucun Purpose n'est assigné.
* **Render (Rendu) :** La géométrie (souvent très lourde et haute résolution) n'est visible **que lors du rendu final** (avec Karma, Arnold, RenderMan, etc.). Elle est masquée dans le viewport pour ne pas ralentir la machine.
* **Proxy :** Une version allégée de la géométrie (modèle low-poly, proxy, ou même une simple boîte) visible **uniquement dans le viewport**. Elle est ignorée au moment du rendu.
* **Guide :** Des éléments purement visuels destinés à aider le travail de l'artiste (repères, courbes de contrôle, zones d'influence, locators). Ils s'affichent dans le viewport mais n'apparaissent jamais au rendu.

#### Comment utiliser le Purpose dans Solaris

1. **À la création (Component Workflow) :** Si vous utilisez le nœud `Component Geometry`, celui-ci possède des entrées distinctes pour "Render" et "Proxy". Solaris se charge de configurer les bons attributs USD automatiquement.
2. **À l'importation :** Le nœud `SOP Import` possède un menu déroulant "Purpose" vous permettant de taguer la géométrie que vous importez.
3. **Sur des primitives existantes :** Le nœud `Configure Primitive` (en contexte LOP) permet d'écraser ou de définir l'attribut Purpose de n'importe quel élément de votre scène.
4. **Comme attribut en SOP** : On peut très bien également le faire en SOPs avec un wrangle sur les primitives : ``s@usdpurpose = "render";``

Dans le viewport de Solaris (en haut à droite, via l'icône de l'œil "Display Options"), vous pouvez cocher ou décocher les Purposes que vous souhaitez afficher (par exemple, forcer l'affichage de la géométrie *Render* dans le viewport pour vérifier un détail).


---


## Références


> [!example]- Flashcards
> ...




## Liens 




