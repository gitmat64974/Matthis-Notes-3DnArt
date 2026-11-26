---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Geometry subset/","tags":["note_permanente"],"ctime":"2026-11-24T18:39:26.495+01:00","mtime":"2026-11-24T15:00:49.418+01:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/USD]]"],"source":["[[3_GARDEN/Notes littéraires/USD - SideFX Course]]"],"Projets":null,"tags":["note_permanente"],"creation date":"2026-11-24","aliases":null}}
---

## La note 

Ce sont un type de primitive qui correspond à une sous partie de la géométrie. ça correspond en gros aux groupes en context SOP

Comment les récupérer : 
- A partir de groups dans SOP : SOP import -> dans import data cocher subset groups : `*`
- A partir du name : le mesh se split automatiquement en fonction du name (ça ne crée pas de subset mais directement plusieurs meshs)

Récupérer à partir de shaders déjà faits dans SOP ou autre : 
- Version simple (que séparer les matériaux) A partir du nom de shader dans SOP : SOP import -> partition attributes -> shader name (cocher )
- Version plus complexe (séparer par matériaux puis sous séparer par subset) : 
	- path attribute -> enlever name et mettre shadername
	- partition attributes -> name


## Références


> [!example]- Flashcards
> ...




## Liens 




