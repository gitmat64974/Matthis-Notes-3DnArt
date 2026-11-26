---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Méthodologie grooming xgen interactive/","tags":["note_permanente"],"ctime":"2026-03-21T20:44:20.085+01:00","mtime":"2026-10-29T13:44:39.160+01:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/GROOM]]","[[3_GARDEN/MOCs/SHADING TEXTURING]]"],"source":["[[3_GARDEN/Notes littéraires/Groom, cours lighting 3D2A]]"],"Projets":null,"tags":["note_permanente"],"creation date":"2025-01-06","aliases":null}}
---


## La note

Méthodologie générale :
#### 1. Scalp

Dupliquer la modé et la modifier pour n'avoir que les parties où il y aura du poil

#### 2. Récupérer les UVs

Ramener ses UVs sur un Layout (optionnel : copier les udims sur un uvSet)

#### 3. Créer le groom

Créer une description Xgen interactive avec une densité initiale correcte : 
Dans l'editor du Xgen interactive -> create interactive groom splines
*Si non manifold : marche pas*

*Mode layer, on travaille de bas en haut* 
#### 4. Définir la densité et la longeur 

Body fur base -> Density brush 

Longueur : dans le layer scale
*On peut ajouter d'autres layer de scale (add modifier), notamment après le sculpt pour que le scale soit uniforme*

Epaisseur : width ramp (layer tout en haut)
*Cocher tube shade pour le shading plus tard*
#### 5. Sculpt

On se met en edit 
Il y a plusieurs outils, notamment le peigne pour brosser 
-> *Dans le tool settings, décocher filter backface pour que l'action du scult passe aussi à travers*
*Pas plus de 3 layers de scult sinon beug*

#### 6. Noise

Add modifier -> noise. Cela créé du fouilli et change la direction de certains poils. Peut être controlé par un ramp comme la width des poils, directement dans l'attribute editor

Le graphique de scale du noise ressemble plutôt à ça : en fonction des refs

![IMG_0813.jpeg](/img/user/Pi%C3%A8ces%20jointes/IMG_0813.jpeg)
#### 7. Cut

Add modifier -> cut
Cut mode relatif : raccourcie en fonction du pourcentage 

2 façons de faire : 
- rand(0,60) dans un node xgm se branche dans le mode relatif du cut : couper aléatoirement -> viens adoucir le poil
- mettre un noise dans le mask, plus de flexibilité, de contrôle et potentiellement de réalisme. Tjrs en mode relatif par contre.
	- Frequency ratio et frenquency au max
	- On peut mettre un scale en dessous du cut pour combler la perte de longueur.
#### 8. Clump (mèches)

Add modifier 
Clump points : density

Si noise avant : le noise agit sur la mèche, si le noise est après il agit poil par poil 

#### 9. Noise aléatoire

Noise tout en haut
Magnitude très haute (8 par exemple)
Et brancher dans la magnitude un ramp avec les paramètres suivants : 

![Capture d'écran 2025-01-31 115347.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202025-01-31%20115347.png)

dans la couleur blanche : mettre une valeur de 10 en data
#### 11. Noise correlation

On peut aussi ajouter un autre noise avec une correlation très forte, cela va faire un effet de faut clumping très intéressant pour les poils courts. 
#### 10. Shading

[[3_GARDEN/Notes permanentes/Shading Groom\|Shading Groom]]
## Références 

## Liens 
