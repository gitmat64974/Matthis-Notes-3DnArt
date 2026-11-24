---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/USD Schemas and Primvars/","tags":["note_permanente"],"ctime":"2026-11-24T15:01:46.116+01:00","mtime":"2026-11-24T15:02:11.732+01:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/USD]]"],"source":["[[3_GARDEN/Notes littéraires/USD - SideFX Course]]"],"Projets":null,"tags":["note_permanente"],"creation date":"2026-11-24","aliases":null}}
---

## La note 

C'est comme le type, ça définit la primitive (geo, light, camera, etc)
Mais les schemas contiennent aussi tout ce qui a permis de créer cette primitive et rename donc tout l'historique et les attributs dans la syntaxe schema usd

Exemple de renaming : 
- P : points
- N : normals
- v : velocities
- uv : st

Primvars : Ce sont des propriétés qui n'ont pas de règle précise dans le schema. Donc par exemple tous les attributs autres de Houdini

Le renaming d'un primvar : shop_materialpath -> primvar:shop_materialpath 

On peut voir les schemas dans les details du scene graph tree de solaris

Les primvars sont importées par défaut dans Solaris


## Références


> [!example]- Flashcards
> ...




## Liens 




