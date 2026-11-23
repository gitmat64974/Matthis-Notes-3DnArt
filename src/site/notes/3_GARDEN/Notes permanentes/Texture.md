---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Texture/","tags":["note_permanente"],"ctime":"2026-03-21T20:44:24.453+01:00","mtime":"2026-04-24T17:43:19.007+02:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/LIGHTING]]","[[3_GARDEN/MOCs/LIGHTING]]","[[3_GARDEN/MOCs/SHADING TEXTURING]]"],"source":["[[3_GARDEN/Notes littéraires/1er cours de rendu esma 3d2a]]"],"Projets":null,"tags":["note_permanente"],"creation date":"2024-10-08","aliases":["texturing"]}}
---


## La note

En CG, les textures ou maps sont les infos en plus, variations des infos du [[3_GARDEN/Notes permanentes/Shading\|Shading]].

#### Déterminer la résolution des textures

Les textures sont généralement en 4k mais ce sont les UVs des objets qui vont déterminer la résolution qu'elles prendront. d’où l'importance d’un bon Layout d’UVs.  
Si la face d’un objet prend au maximum 500 Pixels dans le cadre, en utilisant un format 1920*1080, cette face en UV prend la place de 500 pixels, en plus d’une petite marge, dans le tile.

Elle servira ensuite de base pour la gestion des échelles pour les autres faces.

Texel density - Get - set.

Si les UVs de l’objet dépasse le Tile 1001, on continuera sur le 1002 et on fera alors une texture UDIM. U-Dimension -> Voir [[3_GARDEN/Notes permanentes/UDIM's\|UDIM's]]

## Références 

- Maps déjà faites : [[3_GARDEN/Notes permanentes/Quixel Megascans\|Quixel Megascans]]
## Liens 
