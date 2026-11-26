---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Wrangle d’animation périodique/","tags":["note_permanente"],"ctime":"2026-03-21T20:44:31.944+01:00","mtime":"2025-11-07T17:18:14.875+01:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/HOUDINI]]"],"source":["[[3_GARDEN/Notes littéraires/1er cours CFX]]"],"Projets":null,"tags":["note_permanente"],"creation date":202511071718,"aliases":null}}
---

## La note 

```C
@P.y += sin(1 + $F * chf("period")) * chf("amplitude") + chf("amplitude");
```

Ce wrangle fait bouger l’objet en entrée de haut en bas selon une fonction sinusoïdale en fonction des paramètres période et amplitude qu’il crée (-> crée donc 2 glissières période et amplitude)


## Références


> [!example]- Flashcards
> ...




## Liens 
