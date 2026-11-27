---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Balance des blancs/","tags":["note_permanente"],"ctime":"2026-03-22T12:15:21.642+01:00","mtime":"2026-04-24T17:43:18.616+02:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/ETALONNAGE COLORIMETRIQUE]]","[[3_GARDEN/Notes permanentes/CINEMA]]","[[3_GARDEN/MOCs/DAVINCI RESOLVE]]","[[3_GARDEN/MOCs/COMPOSITING]]","[[3_GARDEN/MOCs/AFFINITY]]"],"source":["[[Playlist 6, cours affinity esma 3d1a]] / [[Color Grading vs. Color Correction Process for Video, A Complete Guide]] / [[3e et 4e cours compositing esma 3d2]]"],"Projets":null,"tags":["note_permanente"],"creation date":"2023-11-09","aliases":["white balance","Color neutralization"]}}
---


## La note

![WhiteBalance_01.webp](/img/user/Pi%C3%A8ces%20jointes/WhiteBalance_01.webp)

La WhiteBalance est l’opération qui vise à neutraliser colorimétriquement de manière à réduire au supprimer la Temperature & Tint ambiente d’un shot.
Votre balance des blancs doit être l’une des premières choses que vous faites, car elle affectera chaque décision que vous prendrez à partir de là.

Il y a 3 axes qui permettent de faire la balance des blancs : 
- Température : [[3_GARDEN/Notes permanentes/Température de la lumière\|Température de la lumière]] 
- Tint : balancer la quantité de Vert & de Magenta dans une image
- Intensity / exposure

#### En live action

En production LiveAction, c’est l’emploi de [ColorChecker](https://www.studiobinder.com/blog/what-is-a-color-checker-tool/) (chartes colorimétriques) qui permettent, dans un environnement lumineux donné, de donner un référentiel colorimétrique sur lequel baser la WhiteBalance. 

![WhiteBalance_00.webp](/img/user/Pi%C3%A8ces%20jointes/WhiteBalance_00.webp)

Dans le cas de prods pour du VFX avec du LiveAction ou pour process de la donnée acquise sur le set de tournage, la WhiteBalance se fait souvent par matrice sur Nuke via des nodes spécialisés dans la détection de ColorCheckers & leur process colorimétrique afin d’automatiquement faire la calibration.

![Capture d'écran 2025-05-12 172404.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202025-05-12%20172404.png)

Node Nuke de ColorNeutralization : [mmColorTarget – Nuke Gizmo :: marco meyer : visual effects artist / td](https://www.marcomeyer-vfx.de/posts/mmcolortarget-nuke-gizmo/)

#### Dans Affinity 

Dans affinity, c'est un réglage.
Le bouton sélecteur de couleur permet de corriger automatiquement la photo.


## Références 

## Liens 