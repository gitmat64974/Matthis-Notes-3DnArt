---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/HDA/","tags":["note_permanente"],"ctime":"2026-03-22T12:15:22.306+01:00","mtime":"2026-11-26T00:41:09.245+01:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/HOUDINI]]"],"source":["[[3_GARDEN/Notes littéraires/4e cours CFX]]"],"Projets":null,"tags":["note_permanente"],"creation date":202511071715,"aliases":null}}
---

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

## Références

[Houdini Digital Assets - YouTube](https://youtube.com/playlist?list=PLXNFA1EysfYnnm2-UZmxrd-MWC7LTWEVl&si=PvmKCrZQ5TDxPrYF)

> [!example]- Flashcards
> ...




## Liens 
