---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Compositing brush stylisation with Copernicus/","tags":["note_permanente"],"ctime":"2026-11-11T22:27:45.215+01:00","mtime":"2026-11-11T21:53:20.605+01:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/HOUDINI]]","[[3_GARDEN/MOCs/LIGHTING]]","[[3_GARDEN/MOCs/SOLARIS]]","[[3_GARDEN/Notes permanentes/Copernicus (Houdini)]]"],"source":null,"Projets":["[[1_PROJETS/FFE/02_PROD/RND/Recherches - Stylised rendering - FFE]]"],"tags":["note_permanente"],"creation date":"2026-01-22","aliases":null}}
---

## La note 

#### Projeter des brushs strokes sur tous les objets 

![](https://i.imgur.com/x8Ve8gr.png)

On va venir projeter une texture de brush strokes sur les objets avec les coordonnées UV de la scène (principe de la [[3_GARDEN/Notes permanentes/ST Map\|ST Map]]). Sauf qu'on va ici faire quelque chose de différent de d'habitude : au lieu de récupérer les uvs des objets, on va venir créer nous même la map st en triplanar pour ne pas dépendre des uvs des objets et que les uvs soient en triplanar pour toute la scène. 

Comment faire cela : 

*on va utiliser la pass de `position` et la pass de `normal`*
1. On vient définir 3 "variantes" d'UVs différents, chacune donc projetant sur un axe de l'espace monde
2. On va blender ces 3 variantes avec les valeurs absolues de la normales (*l'idée est que les faces qui pointent vers le haut aient la variante d'uv qui projette sur l'axe y, les faces qui pointent en direction de l'axe x aient la variante d'uv qui projette sur l'axe x, etc*)

Dans copernicus : 
On utilise un wrangle auquel on crée trois paramètres : N, pos et UV

> [!Example]- Le code VEX
> ```C
> UV_ZY = set(@pos.z, @pos.y);
> UV_XZ = set(@pos.x, @pos.z);
> UV_XY = set(@pos.x, @pos.y);
> 
> float WEIGHT_X, WEIGHT_Y, WEIGHT_Z, WEIGHT_TOTAL;
> 
> WEIGHT_X = pow(abs(@N.x), 50);
> WEIGHT_Y = pow(abs(@N.y), 50);
> WEIGHT_Z = pow(abs(@N.z), 50);
> 
> WEIGHT_TOTAL = WEIGHT_X + WEIGHT_Y + WEIGHT_Z;
> 
> WEIGHT_X /= WEIGHT_TOTAL;
> WEIGHT_Y /= WEIGHT_TOTAL;
> WEIGHT_Z /= WEIGHT_TOTAL;
> 
> @uv = (UV_ZY * WEIGHT_X) + (UV_XZ * WEIGHT_Y) + (UV_XY * WEIGHT_Z);
> ```
> 
> 

#### Slope dir distort

On va pouvoir utiliser ces brushs comme sur d'un distort by slope ensuite, ce qui va donner un fort look peint à l'image

## Références

Scaterring de brush strokes / oil paint look : 

[# COP'ing with Paint | Entagma | Equinox 2025](https://youtu.be/lJAjK3luLDw?si=KOz4wHgo-WGZ5Jit)

> [!example]- Flashcards
> ...




## Liens 




