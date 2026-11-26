---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Render Layers/","tags":["note_permanente"],"ctime":"2026-03-21T20:44:22.356+01:00","mtime":"2026-11-05T23:07:31.618+01:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/LIGHTING]]","[[3_GARDEN/MOCs/LIGHTING]]","[[3_GARDEN/MOCs/COMPOSITING]]"],"source":["#cours [[Cours de lighting rendu ESMA]] -> [[Outlines avec Renderman et Nuke]]"],"Projets":null,"tags":["note_permanente"],"creation date":"2025-04-28","aliases":null}}
---


## La note 

Les Render Layers permettent de séparer différents éléments d'une scène. Chaque layer peut recevoir des objets différents. C'est par exemple utile pour rendre séparément un personnage en mouvement d'un décors fixe, nous faisant optimiser considérablement les rendus et donnant plus de flexibilité au comp.

Chaque Renderlayer peut également avoir ses propres paramètres de rendu et matériaux, grâce aux overrides. Les overrides permettent de modifier certains attributs d'un élément sans affecter la scène principale. On peut avoir ainsi plusieurs "versions" d'un élément

==Bien sûr, chaque RenderLayer contient tous les Layers & Passes setupés dans l’onglet des AOVs!==
#### Avec Renderman dans MAYA

![Capture d'écran 2025-04-28 224421.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202025-04-28%20224421.png)

![Material_override_renderlayers_renderman_img.png](/img/user/Pi%C3%A8ces%20jointes/Material_override_renderlayers_renderman_img.png)

cliquer sur l'icône en forme de "clap" permettre au layer de se rendre. 
L'icone en forme d'oeil est l'affichage dans le viewport (on ne peut afficher dans le viewport qu'un layer à la fois, mais lors du batch tous ceux qui ont un clap vont se rendre)

En faisant un batch, Maya et Renderman vont rendre 1 fichier .exr par Layer. Ainsi, en activant le clap sur le masterLayer et le Layer "matériau Gonflé", nous obtiendront deux fichiers .exr que nous devront merger ensemble dans nuke.

> [!warning]+ Limite des renderlayers : 
> comment conserver les interactions entre le personnage et le décor? (ex:
> ombres portées du personnage sur le sol, reflets du personnage sur un élément du décor, occlusions, etc) 
> -> Solutions : [[Holdout (VFX)\|Holdout (VFX)]]

## Références

[[3_GARDEN/Notes permanentes/Render passes unreal\|Render passes unreal]] 
Render Layers appliqués au traitement du fog : [[3_GARDEN/Notes permanentes/Fog CG\|Fog CG]] 

## Liens 




