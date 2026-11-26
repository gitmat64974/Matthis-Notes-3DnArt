---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes littéraires/4e cours CFX/","tags":["note_litteraire","cours"],"ctime":"2026-03-21T20:44:15.714+01:00","mtime":"2025-12-12T17:46:24.897+01:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/HOUDINI]]","[[3_GARDEN/MOCs/CFX]]"],"source":["[[3_GARDEN/Notes littéraires/Cours CFX ESMA]]"],"Projets":null,"tags":["note_litteraire","cours"],"creation date":"2025-11-07"}}
---



## HDA


<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/3_GARDEN/Notes permanentes/HDA/#la-note" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">



## La note 

[Digital assets](https://www.sidefx.com/docs/houdini/assets/index.html)

Houdini digital asset : groupe de node qu'on peut grouper et export / importer comme un gizmo dans nuke


### Installer un HDA
Asset -> install asset library : pour importer un hda (digital asset)

Installer en manuel : 
Mettre le fichier HDA dans le dossier `C:\Users\Utilisateur\Documents\houdini<version>\otls` 

(*si le dossier otls n'existe pas, c'est qu'il n'y a pas encore eu d'HDA customs, il faut donc le créer*)
#### Modification HDA

Attention à bien modifier le layout des paramètres dans la fenetre type properties et pas dans edit parameter interface

---
### Crée un HDA

`C:\Utilisateurs\<VotreNom d'utilisateur>\Documents\houdini<version>\otls` : dossier où sont stockés les hda

Créer : clic droit sur le subnet -> create digital asset
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

---


### Création de paramètres

#### Menus

##### Créer un menu

Type de paramètrre : Ordered Menu
Puis régler le menu dans le sous onglet menu

##### Afficher masquer des parms en fonction du menu
Pour afficher ou masquer dynamiquement des paramètres en fonction du choix de votre menu, vous devez utiliser l'option **Hide When** (Masquer quand) dans les propriétés de votre HDA.

1. Ouvrez à nouveau les **Type Properties...** de votre HDA.
2. Dans l'onglet **Parameters**, sélectionnez le paramètre que vous souhaitez masquer.
3. Dans la partie inférieure, cliquez sur l'onglet **Conditionals** (dans les versions récentes d'Houdini) ou cherchez directement le champ **Hide When** dans l'onglet _Parameter Description_.
4. Saisissez une expression conditionnelle entre accolades `{ }` en utilisant le _Name_ (le nom interne) de votre menu et le _Token_ de la valeur choisie.

**Exemples de syntaxe :**

Exemple où votre menu s'appelle `choix_mode`, avec le Token `0` pour l'Option 1 et `1` pour l'Option 2.
- Pour cacher le paramètre lorsque l'Option 2 est sélectionnée :
    `{ choix_mode == 1 }`
- Pour cacher le paramètre _sauf_ si l'Option 1 est sélectionnée (très utile si vous ajoutez plus de 2 options plus tard) :
    `{ choix_mode != 0 }`
Si vous avez plusieurs paramètres liés à l'Option 1 (comme des sliders de taille, de force, etc.), vous devez coller cette expression `{ choix_mode != 0 }` dans le champ **Hide When** de chacun de ces paramètres.

**Alternative : Disable When**

Si vous préférez que les paramètres restent visibles mais soient grisés (non modifiables) lorsque l'Option 2 est active, placez simplement la même expression `{ choix_mode == 1 }` dans le champ **Disable When** au lieu de _Hide When_.

#### Créer une couleur permanente pour l'HDA

1. Faites un clic droit sur votre nœud HDA dans le **Network Editor** et choisissez **Type Properties...**
2. Allez dans l'onglet **Scripts**.
3. Dans le menu déroulant **Event Handler**, sélectionnez **On Created**.
4. Assurez-vous que le langage est réglé sur **Python**, puis collez le code suivant :

```python
import hou

node = kwargs["node"]
color = hou.Color((0.6, 0.3, 0.7))  # Valeurs RGB entre 0.0 et 1.0
node.setColor(color)
```


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
  



