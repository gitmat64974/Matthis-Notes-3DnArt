---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Stone wall modeling Houdini/","tags":["note_permanente"],"ctime":"2026-11-26T13:18:27.659+01:00","mtime":"2026-11-26T10:32:47.082+01:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/HOUDINI]]","[[3_GARDEN/MOCs/PROCEDURAL MODELING]]"],"source":null,"Projets":null,"tags":["note_permanente"],"creation date":"2026-11-26","aliases":null}}
---

## La note 

![stone_wall_demo_houdini.png](/img/user/Pi%C3%A8ces%20jointes/stone_wall_demo_houdini.png)

Le principe est très simple : 
- On vient voronoi fracture un cube avec une line d'abord pour créer des lignes horizontales
- Ensuite on traite chaque partie créée individuellement dans un for each. On voronoi fracture avec une line horizontale cette fois
- On crée un attribute rand au préalable qu'on référencera dans la seed du point jitter pour créer des variations aléatoire pour chaque ligne


## Références


> [!example]- Flashcards
> ...




## Liens 




