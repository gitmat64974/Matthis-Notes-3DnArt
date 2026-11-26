---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Verre CG/","tags":["note_permanente"],"ctime":"2026-03-21T20:44:26.517+01:00","mtime":"2026-04-24T17:43:19.027+02:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/LIGHTING]]","[[3_GARDEN/MOCs/LIGHTING]]","[[3_GARDEN/MOCs/SHADING TEXTURING]]"],"source":["[[3_GARDEN/Notes littéraires/Le rendu, google doc début d'année du prof de lighting 3D2]]"],"Projets":null,"tags":["note_permanente"],"creation date":"2024-11-26","aliases":null}}
---


## La note

Pour rendre du verre, il faut avant tout mettre les ray depth spec à 4.
La refraction et reflection doivent être à fond tous les deux.  
La réfraction color peut uniquement être changée avec Thin cocher (objet vide comme un bouteille de Vittel).

Cocher Visible in réfraction dans l’IBL sinon ça fait du noir.
Roughness pour générer du verre dépoli


Interior :
1. extinction : rempli l’objet en fonction de l'échelle de l’objet, la saturation est inversé. 
2. Single Scatter Albedo : de 0 à 1 génère un effet de fumé.

Cocher Multiscattering pour prendre en compte l'éclairage indirect dans la réfraction.
Indice de Réfraction :
- Water = 1.33
- Glass = 1.5
- Diamond = 1.85


## Références 

## Liens 
