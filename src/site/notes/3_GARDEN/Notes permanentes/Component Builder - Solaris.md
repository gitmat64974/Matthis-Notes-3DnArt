---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Component Builder - Solaris/","tags":["note_permanente"],"dg-note-properties":{"MOC":["[[HOUDINI]]","[[Lighting dans Houdini|Solaris]]","[[USD]]"],"source":null,"Projets":null,"tags":["note_permanente"],"creation date":"2026-11-03","aliases":null}}
---

## La note 


Le component builder créée un ensemble de nodes nécessaires à la création simple et complète d'un asset USD

![Capture d'écran 2026-11-01 213928.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202026-11-01%20213928.png)

La hiérarchie des fichiers exportés par le component builder : 

![Capture d'écran 2026-11-01 214439.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202026-11-01%20214439.png)


#### Component geometry

3 modes pour importer la géo : 
- **Internal SOP** : Entrer à l'intérieur pour setup la geo de render, et si on veut la geo proxy et la geo simproxy. ->*Le mode préférable*
- **File** : fichier référencé
- **External SOP** : chemin dans un SOPNet externe

La géo va être nommée en fonction du nom qu'on donne au node 

#### Component material

Il assigne automatiquement le shader qui vient de la deuxième entrée à la géo qui vient de la première

Le matériau va être nommée en fonction du nom qu'on donne au node 

#### Component output

Assez simple, gère tout l'output de l'asset

Thumbnail : permet de générer une image thumbnail de présentation de l'asset (super utile pour les bibliothèques d'asset etc)

## Références

[[3_GARDEN/Notes permanentes/Créer des variants avec le component builder|Créer des variants avec le component builder]]

#### Ressources


- [USD Asset Workflow in Solaris \| Gingerbread House - YouTube](https://youtu.be/tbzIABrViYg)



> [!example]- Flashcards
> ...




## Liens 




