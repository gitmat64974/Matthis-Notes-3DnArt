---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Outlines avec Renderman et Nuke/","tags":["note_permanente"],"ctime":"2026-03-21T20:44:53.773+01:00","mtime":"2026-04-24T17:43:18.896+02:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/LIGHTING]]","[[3_GARDEN/MOCs/SHADING TEXTURING]]"],"source":["#cours [[Cours de lighting rendu ESMA]], cours remplacement Gael Bourdeu"],"Projets":null,"tags":["note_permanente"],"creation date":"2025-04-28","aliases":null}}
---


![Capture d'écran 2025-04-28 210353.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202025-04-28%20210353.png)
## La note 

> [!abstract] Vue brève des différentes techniques : 
> - Le facing ratio
> - Peindre les lines à la main (dans [[3_GARDEN/MOCs/SUBSTANCE PAINTER\|SUBSTANCE PAINTER]] par exemple) et gérer la map en aov avec le pxrTee (voir plus bas dans la note)

#### Le Facing ratio

Le [[3_GARDEN/Notes permanentes/Facing Ratio\|Facing Ratio]] est un concept utilisé en 3D pour définir l'angle entre la surface d'un objet et la caméra.
Il est généralement exploité dans les shaders pour créer des effets dépendants de l'angle de vue, comme le Fresnel, utilisé pour les matériaux semi-transparents, entre autres.

Ici, nous l'utiliserons comme masque en fonction de l'angle de la caméra afin de générer un outline autour de nos géométries.

###### Etape 01 : Paramétrer le Facing Ratio pour le rendu

Dans l'Hypershade de Maya, nous pouvons récupérer l'information du Facing Ratio à l'aide
du node PxrFacingRatio. 

![Capture d'écran 2025-04-28 212343.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202025-04-28%20212343.png)

L'intensité du masque obtenu peut être ajustée via le paramètre [[3_GARDEN/Notes permanentes/Gamma\|Gamma]]
Dans le cas des outlines, nous resterons en mode "Camera"

nous connecterons le PxrFacingRatio à un PxrRamp.
Ce dernier permet non seulement de modifier l'aspect du dégradé, mais aussi d'y introduire de la couleur pour créer des effets spécifiques (atmosphère terrestre, vision thermique, etc).

![Capture d'écran 2025-04-28 214326.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202025-04-28%20214326.png)

Ramp pour des outlines : 

![PxrFacingRatio_outline_ramp.png](/img/user/Pi%C3%A8ces%20jointes/PxrFacingRatio_outline_ramp.png)

• Le premier Pxrlayer correspondra à notre shader principal.
• Le second sera dédié aux outlines, délimités par le duo PxrFacingRatio - PxrRamp.
Ainsi, nous pourrons superposer les outlines sur notre matériau principal. 

On peut même mélanger le pxrfacing ratio à des noises ou des textures, avec pxrblend. 

#### Etape 2 : Exporter le masque des Outlines pour l'utiliser en Comp

Bien qu'il soit tout à fait possible de rendre les outlines directement avec le shader principal, il peut être préférable de les rendre séparément afin de mieux les manipuler sur Nuke. Pour exporter les outlines, nous allons créer un AOV spécifique pour les accueillir.

Voici les étapes :
Connectez notre duo PxrFacingRatio-PxrRamp à un PxrTee.
Dans le PxrTee, nommez l'AOV que vous souhaitez rendre. Dans notre cas, nous allons
l'appeler "Outlines".

![Capture d'écran 2025-04-28 223359.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202025-04-28%20223359.png)

nous allons ajouter un attribut vierge à notre PxrSurface qui n'aura aucune incidence sur le rendu de la Beauty. Voici les étapes:
- Allez dans l'onglet "UtilityPattern" des attributs du PxrSurface.
- Faites un clic droit sur la petite roue dentée à côté de l'onglet et choisissez "Append". 
- glisser-déposer le PxrTee sur le nouvel attribut créé 
- Dans Render Settings, sous l'onglet "Renderman", allez dans l'onglet "AOVs" -> add new channel (nommer outlines) -> le connecter au channel de la beauty -> ajouter dans cet aov le nom de l'aov choisi dans le pxrTee

Ensuite dans Nuke : Shuffle pour isoler l'aov
Au lieu du pxrfacing ratio, on peut tester avec le pxrcurvature aussi

> [!tip] Offset d'outlines
> - On peut soit générer nos outlines sur une geo dupliquée et gonflée par de la displace sans texture branchée. (mettre map d'outlines dans la presence). 
> 	- Alternative : sans duppliquer la modé, on peut mettre 2 matériaux sur une même modé avec le mode override des renderLayers
> - On peut sinon offset dans nuke avec un transform mais l'offset sera 2D et pas 3D



## Références

[[3_GARDEN/Notes permanentes/Render Layers\|Render Layers]]

## Liens 




