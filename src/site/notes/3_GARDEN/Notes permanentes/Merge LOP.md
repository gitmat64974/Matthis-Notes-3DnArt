---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Merge LOP/","tags":["note_permanente"],"ctime":"2026-11-26T10:48:02.474+01:00","mtime":"2026-11-26T10:49:28.915+01:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/HOUDINI]]","[[3_GARDEN/MOCs/SOLARIS]]"],"source":["[[3_GARDEN/Notes littéraires/USD - SideFX Course]]"],"Projets":null,"tags":["note_permanente"],"creation date":"2026-11-26","aliases":null}}
---

## La note 

Ce que fait le merge LOP : comme un merge classique mais avec des spécificités au niveau des layers USD (voir plus bas : merge style parameters)

![Capture d'écran 2026-10-17 211021.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202026-10-17%20211021.png)


Merge style parameter : 
- Simple merge : Il assemble les éléments en écrasant les layers et gardant seulement le plus fort
- Separate layers : il garde les layers bien séparés
- Separate layers, file layers / File layers and SOP weakest : garde les layers bien séparés. Les layers qui viennent de fichiers et / ou de SOP deviennent les layers les plus faibles
- Flatten into first input layers : Flatten tous les layers sauf les layers du premier input. Ces layers prennent les noms des layers sensés être les plus fort
- Flatten each input : Flatten chaque layer dans le plus fort de chaque input

#### Comment bien utiliser le merge LOP

Une bonne chose est de bien définir les layers avant avec des configure layer LOP puis d'utiliser un merge en mode separate layers : 

![](https://i.imgur.com/byyx6Eh.png)


Cela peut être un outil très utile lors de la création de scènes à partir de zéro dans Solaris, par exemple pour merger dans éléments de base comme des lights ou des cameras, mais il doit être utilisé avec précaution lors du chargement de fichiers depuis le disque. Pour tout fichier USD sur le disque, vous devriez utiliser un _Sublayer_ ou un _Reference LOP_

---



## Références


> [!example]- Flashcards
> ...




## Liens 




