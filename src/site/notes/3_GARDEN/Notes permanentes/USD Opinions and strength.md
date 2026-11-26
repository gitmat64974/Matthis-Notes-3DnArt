---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/USD Opinions and strength/","tags":["note_permanente"],"ctime":"2026-11-24T18:39:26.489+01:00","mtime":"2026-11-24T15:11:10.187+01:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/USD]]"],"source":["[[3_GARDEN/Notes littéraires/USD - SideFX Course]]"],"Projets":null,"tags":["note_permanente"],"creation date":"2026-11-24","aliases":null}}
---

## La note 

Lorsque deux primitives on exactement les même attributs ou quand deux layers ont exactement le même composition, lequel gagne sur l'autre ? 

La manière la plus courante de définir une “stronger opinion” est l’ordre de la pile de layers. Mais pour les autres plus précisément : 

**LIVRPS Strength Ordering :** 
1. Local (Layer Stack) : primitive dans un layer au dessus, ou modifiée dans le même layer. Quand on empile des layers, les premiers sont les plus faibles et les derniers les plus forts. Donc dans solaris, le node suivant est plus fort que le node précédent (logique : asset de base -> modif de l'asset de base)
2. Inherits 
3. VariantSets 
4. References 
5. Payload 
6. Specializes 

Sublayers, References/Payloads, and VariantSets sont les plus communs



## Références


> [!example]- Flashcards
> ...




## Liens 




