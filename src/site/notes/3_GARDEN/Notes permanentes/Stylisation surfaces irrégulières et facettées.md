---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Stylisation surfaces irrégulières et facettées/","tags":["note_permanente"],"ctime":"2026-04-06T00:01:05.000+02:00","mtime":"2026-10-20T22:48:47.386+02:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/SHADING TEXTURING]]"],"source":["#cours [[Cours de lighting rendu ESMA]], remplacement 3d2 de Mr Bultingaire par Gaël Bourdeu"],"Projets":["[[6_ARCHIVES/Projets/3D3/Projet cabane esma 3d2]]"],"tags":["note_permanente"],"creation date":"2025-03-19","aliases":null}}
---


## La note 

![Capture d'écran 2025-03-19 161756.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202025-03-19%20161756.png)

*Softwares: Maya, Renderman, Substance Painter*

Ce style graphique, présent dans Ninja Turtles: Teenage Years, Puss in Boots: The Last Wish, The
Wild Robot, etc., repose en partie sur un rendu irrégulier des surfaces, avec parfois des coups
de brosse visibles. Pour obtenir un résultat similaire, nous devons modifier la normale de
l'asset.

#### Workflow Substance

Etape 1 : new project
Etape 2 : Bake maps (notamment la world space normal)
###### Etape 3 : Créer une "custom World Space Normal"

Pour cela, nous devons créer un nouveau channel dédié. Il est possible d'utiliser un channel
existant (Base Co/or, Roughness, Meta/lie, etc.), mais pour des raisons d'export et
d'organisation, il est préférable d'en utiliser un vierge.
- Dans la fenêtre "Texture Set Settings", allez dans l'onglet "Channels".
- Cliquez sur l'icône"+".
- Faites défiler jusqu'en bas du menu déroulant, dans la section "User Channels".
- Sélectionnez un channel vide, comme "UserO" par exemple.

![Capture d'écran 2025-03-19 162446.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202025-03-19%20162446.png)


###### Peindre la custom world space normal

- Afficher la "Custom World Space Normal" dans le viewport
- Créer un Fill Layer.
- Dans les propriétés du Fill Layer, désactiver tous les channels sauf "Custom World Space Normal".

Comme base de ce Fill Layer, nous allons appliquer la map de World Space Normal.
- Ouvrir la fenêtre Library et aller dans l'onglet Project -> Rechercher la map World Space Normal -> Remplacer l'Uniform Color du channel "Custom World Space Normal" en faisant un glisser-déposer de cette map dessus. 
- Add paint au fill layer
	- pipette (touche P) pour prélever des couleurs sur la World Space Normal.
	- L'outil Brush pour repeindre et casser les dégradés trop parfaits

![Capture d'écran 2025-03-19 162917.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202025-03-19%20162917.png)

###### Exporter les textures

- Dans la fenêtre "Export Texture" (Ctrl + Shift + E), allez dans l'onglet "Output Template",puis cliquez sur l'icône"+" pour créer un nouveau template d'export.
- Ajoutez un channel d'export "RGB" dans "Output Maps".
- Renommez le channel d'export en utilisant la nomenclature pour les UDIMs ($udim).
- Glissez-déposez depuis les "Input Maps" le channel "User0" (celui que nous avons utilisé pour repeindre notre custom World Space Normal) dans le carré "RGB" du channel d'export dans "Output Maps". 
- Enregistrez le nouveau template en cliquant sur "Save Settings".
- Export maps -> brancher cette nouvelle map dans le node "PxrNormalMap", lui-même
connecté à l'input "Bump Normal" du pxrSurface.

![Capture d'écran 2025-03-19 163213.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202025-03-19%20163213.png)


## Références



## Liens 




