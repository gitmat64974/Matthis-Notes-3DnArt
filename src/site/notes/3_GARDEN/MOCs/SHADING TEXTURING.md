---
{"dg-publish":true,"permalink":"/3_GARDEN/MOCs/SHADING TEXTURING/","tags":["MOC"],"ctime":"2026-04-25T23:16:42.658+02:00","mtime":"2026-04-06T00:00:41.000+02:00","dg-note-properties":{"tags":["MOC"]}}
---


> [!example]- Ressources
> - Tutos Mari
> 	- Bases de Mari, très complet et rapide : [Learning Mari, Michael Wilde](https://www.youtube.com/playlist?list=PLfcn6CVBmf7iEHKhAo7zkSEAnjAnT5a4l)
> 	- Un peu ardus : [Meshmen](https://www.youtube.com/channel/UCl8q9Uiq_fRPW4mYK71C-oA)
> 	- [Texturing with mari, chaine the foundry](https://youtube.com/playlist?list=PLi2GhhsPL-Ror-rJLN5rmNf4-hBGdhkDZ&si=qhT7LewYwUnJgUCB)
> 
> Artistes : 
> - Jens Kafitz
> - Tom Newbury
> - Flipped Normal -> Anciens du VFX, plein tutos 

# MOC

De manière générale, pour le photoréalisme (regroupant aussi du [[3_GARDEN/MOCs/LIGHTING\|3_GARDEN/MOCs/LIGHTING]]) : [[3_GARDEN/Notes permanentes/Secrets du photorealisme\|Secrets du photorealisme]]

## Avant de commencer 

Il faut bien entendu avant de commencer le [[3_GARDEN/Notes permanentes/Shading\|Shading]] et le texturing, avoir une [[3_GARDEN/Notes permanentes/Modélisation utilisable en production\|Modélisation utilisable en production]] et de bons [[3_GARDEN/MOCs/UV\|UV]] (sur lesquels on va venir projeter les textures)

---

## Distinction shading et texturing

> [!NOTE]+ [[3_GARDEN/Notes permanentes/Shading\|Shading]] 
> - Faire le shading des principaux matériaux :  [[3_GARDEN/Notes permanentes/Matériau\|Matériau]] 
> 
> 
> voir aussi [[3_GARDEN/Notes permanentes/Matériaux de base renderman\|Matériaux de base renderman]] 
> La base : 
> - [[3_GARDEN/Notes permanentes/Diffuse\|Diffuse]]
> - [[3_GARDEN/Notes permanentes/Spéculaire\|Spéculaire]]
> - [[3_GARDEN/Notes permanentes/Iridescence\|Iridescence]] 
> - [[3_GARDEN/Notes permanentes/Verre CG\|Verre CG]]

Texturing : [[3_GARDEN/Notes permanentes/Texture\|Texture]]

Autres : 
- [[3_GARDEN/Notes permanentes/Glow\|Glow]]
- [[3_GARDEN/Notes permanentes/PxrMarschenHair\|PxrMarschenHair]]
- [[3_GARDEN/Notes permanentes/PxrVolume\|PxrVolume]]
- [[3_GARDEN/Notes permanentes/PxrBake\|PxrBake]]

## Lookdev


> [!tip]
> Comme chaque stade de la création les objets doivent être réfléchi en fonction de leur distance maximale cadré, c’est leur échelle qui déterminera leur approche en terme de matériaux.  
> Exemple : 
> 
> Un visage d’une taille de quelque pixel derrière un nuage, n’aura ni besoin d’être travailler ni même texturé, une [[3_GARDEN/Notes permanentes/Diffuse\|Diffuse]] beige fait très bien l’affaire.  
> Si la caméra passe à moins d’un millimètre de la peau d’un personnage il faudra surement penser à modéliser les couches de peaux avec différents matériaux comme du verre, du subsurface et autre.
> 
> Proche du visage un subsurface de qualité sera apprécié, avec du [[3_GARDEN/Notes permanentes/Displace\|Displace]], du bump, du [[3_GARDEN/Notes permanentes/Spéculaire\|Spéculaire]],... etc.
> 
> Plus loin une [[3_GARDEN/Notes permanentes/Diffuse\|Diffuse]] avec un belle texture et du [[3_GARDEN/Notes permanentes/Spéculaire\|Spéculaire]] serait suffisant.


[[3_GARDEN/Notes permanentes/LookDev\|LookDev]] 

-> [[3_GARDEN/Notes permanentes/Les 2 grands types d’informations en texturing\|Les 2 grands types d’informations en texturing]]

## Faire du volume en texture 

Mode, [[3_GARDEN/Notes permanentes/Displace\|Displace]], bump, roughness : [[3_GARDEN/Notes permanentes/4 Niveaux de volume en CG\|4 Niveaux de volume en CG]] 
- [[3_GARDEN/Notes permanentes/Sculpt (3D)\|Sculpt (3D)]]
En texture on peut donc jouer sur 3 niveaux : [[3_GARDEN/Notes permanentes/Displace\|Displace]], bump et roughness

## Matériaux spécifiques 

- [[3_GARDEN/Notes permanentes/Rendre le métal, CG\|Rendre le métal, CG]]
- [[3_GARDEN/Notes permanentes/Eau Maya et renderman\|Eau Maya et renderman]]
- [[3_GARDEN/Notes permanentes/Herbe modélisation Maya\|Herbe modélisation Maya]] (même si c'est plus de la modé)
- [[3_GARDEN/Notes permanentes/SSS\|SSS]] 
- [[3_GARDEN/Notes permanentes/Glow\|Glow]] 
- Cheveux : [[3_GARDEN/Notes permanentes/PxrMarschenHair\|PxrMarschenHair]] 
- Volumétriques : [[3_GARDEN/Notes permanentes/PxrVolume\|PxrVolume]]
- [[3_GARDEN/Notes permanentes/Nested Dialectrics\|Nested Dialectrics]]

## Corps Humain

[[3_GARDEN/Notes permanentes/Shading et texturing d'une tête\|Shading et texturing d'une tête]] 

---

## Stylisé

[[3_GARDEN/Notes permanentes/Stylised texturing with Normal map\|Stylised texturing with Normal map]]
[[3_GARDEN/Notes permanentes/Stylisation surfaces irrégulières et facettées\|Stylisation surfaces irrégulières et facettées]]
[[3_GARDEN/Notes permanentes/Outlines avec Renderman et Nuke\|Outlines avec Renderman et Nuke]]

---

Par logiciel : 
- [[3_GARDEN/MOCs/MARI\|MARI]]
- [[3_GARDEN/MOCs/SUBSTANCE PAINTER\|SUBSTANCE PAINTER]]
- [[3_GARDEN/MOCs/SUBSTANCE DESIGNER\|SUBSTANCE DESIGNER]]