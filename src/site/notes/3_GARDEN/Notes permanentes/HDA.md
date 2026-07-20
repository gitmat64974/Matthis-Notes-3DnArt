---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/HDA/","tags":["note_permanente"],"dg-note-properties":{"MOC":["[[HOUDINI]]"],"source":["[[4e cours CFX]]"],"Projets":null,"tags":["note_permanente"],"creation date":202511071715,"aliases":null}}
---

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


## Références

[Houdini Digital Assets - YouTube](https://youtube.com/playlist?list=PLXNFA1EysfYnnm2-UZmxrd-MWC7LTWEVl&si=PvmKCrZQ5TDxPrYF)

> [!example]- Flashcards
> ...




## Liens 
