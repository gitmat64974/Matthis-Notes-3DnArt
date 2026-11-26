---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/LOD/","tags":["note_permanente"],"ctime":"2026-11-26T13:18:27.673+01:00","mtime":"2026-11-26T10:57:50.442+01:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/USD]]","[[3_GARDEN/MOCs/SOLARIS]]"],"source":["[[3_GARDEN/Notes littéraires/USD - SideFX Course]]"],"Projets":null,"tags":["note_permanente"],"creation date":"2026-11-26","aliases":null,"banner":"https://www.cgspectrum.com/hs-fs/hubfs/different-LODs-3d-modeling.jpg?width=1350&height=941&name=different-LODs-3d-modeling.jpg"}}
---

## La note 

*Level of Detail*

Ce sont différentes versions de la géométrie qui se swappent en fonction de la distance à la caméra (LOD_0 en closeup c'est le mesh High Poly, LOD_3 en background, c'est le mesh le plus low poly)

### Dans Solaris

Pour la création des LODs voir [[3_GARDEN/Notes permanentes/USD Variants\|USD Variants]]
  
#### Auto select LOD LOP

*C'est une feature disponible dans Solaris, mais pas en usd de manière générale. Elle utilise bien sur les LOD usd, mais n'est pas une feature usd en tant que telle.
Donc si on export en usd, les informations de LOD seront exportées en frame statique, mais si on export en animé, le mouvement de caméra ne sera pas pris en compte et donc les LOD ne changeront pas. 
Il faut donc garder ce node dans les derniers setups de rendu par exemple, ou gérer les scènes en fonction*

Permet de automatiquement selectionner le bon LOD en fonction de la distance à la caméra

![Capture d'écran 2026-10-22 153739.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202026-10-22%20153739.png)

---



## Références


> [!example]- Flashcards
> ...




## Liens 




