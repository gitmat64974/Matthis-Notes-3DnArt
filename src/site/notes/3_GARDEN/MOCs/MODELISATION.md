---
{"dg-publish":true,"permalink":"/3_GARDEN/MOCs/MODELISATION/","tags":["MOC"],"ctime":"2026-03-21T20:44:12.887+01:00","mtime":"2026-11-08T17:56:08.341+01:00","dg-note-properties":{"aliases":["modélisation 3D","Modélisation"],"tags":["MOC"],"MOC":["[[3_GARDEN/MOCs/SCIENCES]]","[[3_GARDEN/MOCs/3D]]"]}}
---

# Définition

En 3D la modélisation est la base d’une forme plus ou moins complexe. Chaque modèle 3d est composé de 3 éléments : points, arêtes et faces. 

<u>Chaque objet en 3D a 2 éléments principaux :</u> 
- **Transform** : *Position*
    - Nom
    - Échelle, taille, distance, position
    - Orientation 
- **Shape** : *Forme / géométrie*
    - Vertices, faces, edges
    - Pour le [[3_GARDEN/MOCs/RIG\|RIG]] il faut qu’il ait qu’un seul shape unique pour chaque objet

*Group : les groupes dans maya ne sont que des transform, ils n’ont pas de shape.*

Un des aspects les plus importants de la modélisation sont les angles. Ce sont des moments critiques où la lumière change de comportement lorsqu'elle rebondit sur l'objet.

**3 types de modélisation :** 
- surfacique (polygones ou surfaces paramétriques à partir de courbres (automobile, aviation etc)), 
- en solide (on a un volume qu'on extrude -> solidworks), 
- voxel (volume element -> fluide : liquide, fumée)

==A noter que par convention, on dirige toujours la modé (ou le "regard" de la modé) selon l'axe z positif==. 

> [!example]- Ressources
> Chaînes yt : 
> - https://youtube.com/@MHTutorials3D?si=tbqw0OtzNA3oMJdG
> - Elementza 
> - JL Mussi
> - On mars 3D 
> - https://www.youtube.com/@johnkcee/playlists
> 
> Modeliser un corps en entier : [Modeling base mesh in maya](https://youtube.com/playlist?list=PLgala72Uap1ph3qoTXHzZX2at0C9VaweM&si=LOvXdKN4D2-P_h1V)
> 
> Textures : textures.com

# MOC

Dans MAYA : 
première chose : [[3_GARDEN/Notes permanentes/Bases d'utilisation de Maya\|Bases d'utilisation de Maya]]

-> Méthodo complète de Modé : [[3_GARDEN/Notes permanentes/Méthodologie modélisation\|Méthodologie modélisation]]

Concepts importants : 
- [[3_GARDEN/Notes permanentes/Topology edge flow\|Topology edge flow]] 
	- [[3_GARDEN/Notes permanentes/Simplifications de maillage\|Simplifications de maillage]] avec aussi par exemple la [[3_GARDEN/Notes permanentes/Méthodologie subdivision de cercles\|Méthodologie subdivision de cercles]]
- [[3_GARDEN/Notes permanentes/Subdivisions en modélisation\|Subdivisions]]

Mode, [[3_GARDEN/Notes permanentes/Displace\|Displace]], bump, roughness : Ce sont les [[3_GARDEN/Notes permanentes/4 Niveaux de volume en CG\|4 Niveaux de volume en CG]] 
- [[3_GARDEN/Notes permanentes/Sculpt (3D)\|Sculpt (3D)]]

#### Clean 

- [[3_GARDEN/Notes permanentes/Modélisation utilisable en production\|Modélisation utilisable en production]] 
- [[3_GARDEN/Notes permanentes/Retopologie\|Retopologie]]

#### Autres

- [[3_GARDEN/Notes permanentes/Différence point et vertex\|Différence point et vertex]]
- [[3_GARDEN/Notes permanentes/Cloth simulation maya\|nCloth]]

#### Modélisation organique


[[3_GARDEN/Notes permanentes/Modélisation d'ailes d'insecte\|Modélisation d'ailes d'insecte]]

### Modelisation humaine

[[3_GARDEN/Notes permanentes/Dents modélisation\|Dents modélisation]]
[[3_GARDEN/Notes permanentes/Modélisation orbites occulaires\|Modélisation orbites occulaires]]

