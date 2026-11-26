---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Displace/","tags":["note_permanente"],"ctime":"2026-03-21T20:44:25.055+01:00","mtime":"2026-04-24T17:43:18.670+02:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/LIGHTING]]","[[3_GARDEN/MOCs/LIGHTING]]","[[3_GARDEN/MOCs/SHADING TEXTURING]]"],"source":null,"Projets":null,"tags":["note_permanente"],"creation date":"2024-11-26","aliases":["Displacement","DispRGB","Scalar displacement"],"Source":["[[3_GARDEN/Notes littéraires/Le rendu, google doc début d'année du prof de lighting 3D2]]","[[3_GARDEN/Notes littéraires/Cours de lighting rendu ESMA]]"]}}
---


## La note

C'est du véritable volume ajouté en [[3_GARDEN/Notes permanentes/Texture\|Texture]] sur des millions de pixel. Attention la résolution dépend du cadre !

*On peut générer la displace de plusieurs manières : Sculpt Mudbox, Sculpt Zbrush, Heightmap MARI, Substance, l’importer d’une bank etc*
Une displace se gère par des valeurs numérique flottantes qui représentent la hauteur direct en unité dans la scène. De base 0.5 augmente le volume de 0.5 unité. 0 ne bouge pas. 

**La Displace est multipliée par le scale des objets. → Freeze les scales**
#### Bump vs displace en profondeur de pixels

![Choix_de_profondeur_image_Bump_Displace.png](/img/user/Pi%C3%A8ces%20jointes/Choix_de_profondeur_image_Bump_Displace.png)

Au moment de faire la displace et de la tester dans le [[3_GARDEN/Notes permanentes/LookDev\|LookDev]], il est préférable de désactiver tous les lobes des matériaux et de ne garder que les specs pour bien voir la displace et le bump. On peut même réarranger la modé très légèrement à certains endroits en fonction des specs etc

### DispRGB

Des fois on utilise une map de displace en RGB et non en scalar : 

> [!info] Pourquoi : 
> On va pouvoir avoir 3x plus d'informations dans une seule map et gérer les couches rgb séparément. 

> [!example] Par exemple : 
> Le rouge c‘est les basses fréquence, le vert les moyennes, le bleu les hautes, avec des valeurs de mid point différentes. On va tout venir combiner
> -> C'est ce qu'on fait souvent en [[3_GARDEN/Notes permanentes/Skin texturing MARI\|Skin texturing MARI]] pour du VFX

> [!abstract]+ Branchement dans renderman ensuite : 
> On sépare chaque couche rgb pour pouvoir les traiter séparément : 
> 
> ![Capture d'écran 2025-11-11 104559.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202025-11-11%20104559.png)
> 


#### Utiliser la dispRGB en displace, bump, roughness


Une des façons d'utiliser la dispRGB est de brancher chaque canal dans un niveau de définition de géométrie différent : 
displace, bump, roughness

![Capture d'écran 2026-02-09 004609.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202026-02-09%20004609.png)




## Références 

## Liens 
