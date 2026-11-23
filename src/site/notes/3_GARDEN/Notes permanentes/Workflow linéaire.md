---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Workflow linéaire/","tags":["note_permanente"],"ctime":"2026-03-21T20:44:25.545+01:00","mtime":"2026-04-04T12:57:39.720+02:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/LIGHTING]]","[[3_GARDEN/MOCs/3D]]","[[3_GARDEN/MOCs/COULEUR]]"],"source":["[[3_GARDEN/Notes littéraires/Chris Brejon, CG Cinematography book chapter 1, note litt]]"],"Projets":null,"tags":["note_permanente"],"creation date":202510041727,"aliases":null}}
---

## La note 

> [!quote] Jeremy Selan
> Nous préconisons donc de penser un long métrage d’animation comme la création d’un « plateau de tournage virtuel » dans l’ordinateur, avec une caméra virtuelle, un stock de négatifs virtuel et un stock d’impression virtuel. 

![Pièces jointes/5691fba89d0fd4f1eab8c3bf2cdeeafe_MD5.jpg](/img/user/Pi%C3%A8ces%20jointes/5691fba89d0fd4f1eab8c3bf2cdeeafe_MD5.jpg)

**les moniteurs disposent d’une correction [[3_GARDEN/Notes permanentes/Gamma\|Gamma]] pour afficher correctement les images.** Il s’agit d’une norme de l’industrie en matière de confort visuel _Dans la plupart des cas, si un ordinateur exécute le système d’exploitation Windows, nous pouvons obtenir des couleurs proches de l’idéal en utilisant un moniteur avec une valeur [[3_GARDEN/Notes permanentes/Gamma\|Gamma]] de 2,2, la valeur [[3_GARDEN/Notes permanentes/Gamma\|Gamma]] standard pour Windows._ vos rendus ne seront **JAMAIS** corrects si vous n’utilisez pas une fonction de transfert linéaire pour votre espace de rendu. **Le rendu (et l’affichage) en sRGB simple est tout simplement faux !**

_De la note : renderman color management :_

Pour simplifier à l’extrême, décomposons l’ensemble d’un pipeline de rendu en trois étapes simples :

![Pièces jointes/924cc4b2523ff0a45c04892093a65b13_MD5.jpg](/img/user/Pi%C3%A8ces%20jointes/924cc4b2523ff0a45c04892093a65b13_MD5.jpg)

(Source : [Pixar's RenderMan \| Tutorial \| Color Management](https://renderman.pixar.com/color-management))

> [!NOTE] Pour qu’un flux de travail linéaire fonctionne :
> 
> Tous les calculs doivent être effectués en gamma linéaire, mais tous les affichages (entrée/sortie) doivent se faire en gamma sRGB.

![Pièces jointes/bfa74221230e907b60dd825cadfdd1b7_MD5.jpg](/img/user/Pi%C3%A8ces%20jointes/bfa74221230e907b60dd825cadfdd1b7_MD5.jpg)

![Pièces jointes/f1a82ad400b0c51bb6ae23f475c5aa7b_MD5.jpg](/img/user/Pi%C3%A8ces%20jointes/f1a82ad400b0c51bb6ae23f475c5aa7b_MD5.jpg)

La lumière fonctionne de manière linéaire et ne fonctionne donc correctement que lorsqu’elle éclaire des valeurs linéaires. Mais l’image linéaire résultante n’est pas adaptée à la visualisation, mais contient toutes les données appropriées.


## Références


> [!example]- Flashcards
> ...




## Liens 
