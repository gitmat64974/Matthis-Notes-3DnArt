---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Modélisation utilisable en production/","tags":["note_permanente"],"ctime":"2026-03-22T12:15:23.021+01:00","mtime":"2026-04-24T17:43:18.857+02:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/LIGHTING]]","[[3_GARDEN/MOCs/RIG]]","[[3_GARDEN/MOCs/SHADING TEXTURING]]","[[3_GARDEN/MOCs/MODELISATION]]"],"source":null,"Projets":null,"tags":["note_permanente"],"creation date":"2024-10-06","aliases":["Clean de modé"],"Source":["[[3_GARDEN/Notes littéraires/Cours de modélisation ESMA]]","[[3_GARDEN/Notes littéraires/1er Cours de rig 3d2]]"]}}
---


## La note

Avant de rigger ou de texturer on doit toujours s’assurer que les infos de la mode sont bonnes :  
2 noeuds dans une modé :
- Transform
    - Nom
    - Échelle, taille, distance, position
    - Orientation
- Shape (géométrie)
    - Vertices, faces, edges
    - Pour le rig il faut qu’il ait qu’un seul shape unique pour chaque objet

Il faut : 
maillage fluide, homogène et élégant avec des quads pour le smooth et le skin, des edges loops pour les plis et les blendshapes. Il faut pouvoir retoucher chaque vertex. Si ce n'est possible c'est trop highPoly. Une fois les volumes décoincé il faut être extrêmement propre. 
Bien ajuster les lignes qui suivent les volumes, éviter les zigzags, maximiser les quads, ne pas avoir peur des étoiles à 5 branches qui marque les changements de direction. Mais placer des edges loops sur les zones sensibles

Si la modé de base n’est pas parfaitement abouti, tout ce qui en découle sera de plus en plus médiocre. Il faut être le plus juste possible sur le volume général et les détails dès le départ

> [!warning]+ Erreurs en  modélisation pour subdivision à éviter
> - trop de tensions : pas de faces tordues ou étirées, on rajoute des edges ou on change la topo.
> - Edges trop rapprochées : quand on appuie sur 3 les edges ne doivent quasiment pas s’écarter.
> - Homogénéité (moins grave que les tensions et les edges) : pour la subdivision et la [[3_GARDEN/Notes permanentes/Displace\|Displace]] : ça va subdiviser trop à certains endroits ou y a pas forcément besoin
> - Triangles : compliqué de subdiviser les triangles
> - Ngon : pas super grave dans les endroits pas trop importants ou plats, ça va subdiviser en quad comme les triangles. Mais pas à la fin de la mode on doit pouvoir subdiviser. Mais on va quand même essayer de rajouter une edge pour casser le ngon
> - Non manifold : quand les UV ou les edges sont connectées à trop de faces
> - Overlap de mode, faces qui se rentrent dedans. On évite au maximum.
> - Du trop LowPoly. Une subdivision va "aplatir" les volumes. Les informations vont se décalées sur la projection, les uvs, le texturing. Donc il faut que le mesh en preview smooth se rapproche au plus près du mesh sans smooth (sans trop de subdivision pour rester optimisé).
> - Un objet trop petit (moins de 1 carreau). La projection et le sculpt seront plus compliqué car les valeurs trop petites.

#### Clean des géométries (voir le [[3_GARDEN/Notes permanentes/Cleanup dans Maya\|Cleanup dans Maya]]):

- non quad (tris, ngons)
- Trous : display border edges
- Non manifold
- Laminas
- zéro geo area
- Concave faces

#### Dernières étapes

- renommer les objets, nomenclature
- Center pivot : met le pivot au centre de la bounding box de la sélection
- Centrer l'objet sur la grille

- Freeze transform (attention qu’il n’y ait pas de clé d’anim) :
	- Géométrie : oui
	- Curves : non
	- Joints : oui

- Delete history 

- Faire de beaux UVs 


## Références 

[[3_GARDEN/Notes permanentes/Méthodologie modélisation\|Méthodologie modélisation]]

## Liens 

