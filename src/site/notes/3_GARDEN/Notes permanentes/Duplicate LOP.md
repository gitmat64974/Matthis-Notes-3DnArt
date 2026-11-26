---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Duplicate LOP/","tags":["note_permanente"],"ctime":"2026-11-26T13:18:27.682+01:00","mtime":"2026-11-26T10:49:12.719+01:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/SOLARIS]]"],"source":["[[3_GARDEN/Notes littéraires/USD - SideFX Course]]"],"Projets":null,"tags":["note_permanente"],"creation date":"2026-11-26","aliases":null}}
---

## La note 

Fonctionne comme un copy and transform SOP. 

Parameters : 
- Modify source primitives : Permet de dire si la source est la première duplication, ou si elle est désactivée, ou juste cachée etc etc

***Primitive definition :*** 
- Reference type
	- **Copy** : copie toute la geo, materiaux etc. C'est donc très lourd
	- **Reference** : chaque duplication référence la source
	- Inherit : Reference plus forte (voir les layers USD)
	- Specialize : Reference plus faible (voir les layers USD)
- Make Instanceable : si c'est coché, cela veut dire que solaris va récupérer la source (en copy ou reference) et c'est tout, ne prenant pas en compte tous les overides qu'il y a pu avoir dans la chaine. C'est donc encore plus léger

Le node a un paramètre pour save les duplications dans une collection


## Références


> [!example]- Flashcards
> ...




## Liens 




