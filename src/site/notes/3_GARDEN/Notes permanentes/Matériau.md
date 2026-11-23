---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Matériau/","tags":["note_permanente"],"ctime":"2026-03-21T20:44:42.130+01:00","mtime":"2026-04-24T17:43:18.850+02:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/MODELISATION]]","[[3_GARDEN/MOCs/SHADING TEXTURING]]"],"source":["[[3e cours de lighting esma 3d1a]] / [[Secrets of photorealism, Blender guru]]"],"Projets":null,"tags":["note_permanente"],"creation date":"2024-09-13","aliases":null}}
---


## La note

**Il n’y a que deux types de matériaux dans le monde :
Diélectriques et conductifs.**

#### Diélectriques

![Capture d'écran 2024-10-02 212534.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202024-10-02%20212534.png)

Il y aura toujours de la réflexion et de la réfraction ([[3_GARDEN/Notes permanentes/Diffuse\|Diffuse]]), soit la couleur de l'objet. Tous les matériaux réfléchissent, c'est pourquoi il est important en CG de toujours mettre de la réflexion (au moins 50%), quitte à mettre la roughness au maximum pour un matériau qui ne semble absolument pas réfléchissant 
Les diélectriques ont toujours du [[3_GARDEN/Notes permanentes/SSS\|SSS]] à plus ou moins grande échelle (des fois ça ne se voit pas), responsable de la refraction. Ils ont aussi très souvent de la [[3_GARDEN/Notes permanentes/Roughness\|Roughness]]
#### Conductifs

![Capture d'écran 2024-10-02 213618.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202024-10-02%20213618.png)

Les métaux sont purement de la réflexion, et certains teintent cette réflexion. 
Bien sur la réflexion suit le principe du [[3_GARDEN/Notes permanentes/Fresnel\|Fresnel]]

#### En CG dans renderman :


le PxrSurface est un Matériau basique et multifonction, convient aux objets solides.
Le PxrLayerSurface est un matériau à "étage". on peut superposer plusieurs matériaux grâce à des masques.
PxrLama est un materiau nodal, chaque lobe à son propre node


## Références 

- Vantablack : matériau le plus absorbant du monde (sinon c le charbon) 
- [[3_GARDEN/Notes permanentes/Spéculaire\|Spéculaire]]
## Liens 
