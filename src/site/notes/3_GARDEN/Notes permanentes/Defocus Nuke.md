---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Defocus Nuke/","tags":["note_permanente"],"ctime":"2026-03-21T20:44:26.093+01:00","mtime":"2026-04-24T17:43:18.662+02:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/COMPOSITING]]"],"source":["#video[This Unreal 5 + Nuke Workflow is Actually Insane - YouTube](https://youtu.be/hFM_jGd46as?si=WZ1aR26kPI3pZrAe)"],"Projets":null,"tags":["note_permanente"],"creation date":"2025-02-16","aliases":null}}
---


## La note 

On rend sans DOF, tout est net au rendu, et on met ensuite du defocus avec la pass de depth. 

Deux types de bokeh : 

![Capture d'écran 2025-02-16 223333.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202025-02-16%20223333.png)

En CG, on cherche à avoir la plupart du temps un look anamorphic. 

Setup très simple pour anamorphic : 
(mettre le filter type dans node zdefocus sur image)

![Capture d'écran 2025-02-16 223716.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202025-02-16%20223716.png)

*Le node convolve peut remplacer zdefocus si on veut mettre du defocus de manière uniforme sur toute l'image*

Le noeud bokeh est parfois mieux que le zdefocus
On a aussi le bokehbuilder pour le filter

## Références

[[3_GARDEN/Notes permanentes/Lens flares Nuke\|Lens flares Nuke]]

## Liens 




