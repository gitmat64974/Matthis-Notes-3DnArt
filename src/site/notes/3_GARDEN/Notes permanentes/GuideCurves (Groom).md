---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/GuideCurves (Groom)/","tags":["note_permanente"],"ctime":"2026-03-22T12:15:22.285+01:00","mtime":"2026-04-24T17:43:18.718+02:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/GROOM]]","[[3_GARDEN/MOCs/3D|CG]]"],"source":["#cours [[Groom, cours lighting 3D2A]]"],"Projets":null,"tags":["note_permanente"],"creation date":"2025-01-29","aliases":null}}
---


## La note 

**Les guidesCurves** donnent la taille et la direction du poil = 80% du temps de travail sur le poil
_Pourquoi des guides et pas du sculpt ?_ Plus propre car non destructif, 
Vision plus claire de la direction générale.
Permet de pouvoir simuler le poils plus facilement (si besoin)

### Création guides Xgen Interactive

Créer des curves → ce seront les guides
créer un xgen interactive groom spline
enlever scult, scale et add modifier guides.
Shift select les curves et le modifier → input guide → use selected curve as guide

### Méthodos

**Méthodo rigoureuse**

Modé en make live
Select ep curve tool → faire les guides avec 3 cv

| ![Capture d'écran 2025-01-29 200853.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202025-01-29%20200853.png) | ![Capture d'écran 2025-01-29 200949.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202025-01-29%20200949.png) |
| ------------------------------------------ | ------------------------------------------ |
Ensuite relever les guides en plaçant le pivot à la base de chaque curve ([[3_GARDEN/Notes permanentes/Script sPivotOnCv\|Script sPivotOnCv]]) puis rotate en mode objet. 
On ne relève jamais les guide à 90°, plutôt dans les 45° 

Nombre de guides mauvais : 

**Au max une guide par face**

| ![Capture d'écran 2025-01-29 200709.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202025-01-29%20200709.png) | ![Capture d'écran 2025-01-29 200806.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202025-01-29%20200806.png) |
| ------------------------------------------ | ------------------------------------------ |
| Pas assez                                  | Trop                                       |

**Méthodo plus rapide (un peu shlag)**

Generate → make paintable
Peindre avec le paintfx tool à la tablette
convert les paintfx en curve
rebuild
## Références

[[3_GARDEN/Notes permanentes/Script sPivotOnCv\|Script sPivotOnCv]] 
[[3_GARDEN/Notes permanentes/Mask Xgen\|Mask Xgen]] 

## Liens 

