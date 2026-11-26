---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Anchor point Substance Painter/","tags":["note_permanente"],"ctime":"2026-03-21T20:44:30.563+01:00","mtime":"2026-04-24T17:43:18.601+02:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/SUBSTANCE PAINTER]]"],"source":["#video [Anchor Point Magic 01 - Double Layer Setup in Substance 3D Painter | Adobe Substance 3D - YouTube](https://youtu.be/Ix4eknncFU0?si=xHg_uMWlBPnlYAgI)"],"Projets":null,"tags":["note_permanente"],"creation date":"2025-02-20","aliases":null}}
---


## La note 

Les anchors points permettent de réutiliser des informations d'un layer sur un autre, ils sont complètement dynamiques et changent en temps réel. 
Typiquement c'est une référence (comme référence dans maya) 

Utilisation : 
Mettre un anchor point là où l'on veut "freeze" les informations
Dans le calque où on veut réutiliser les infos, mettre dans un mask un fill layer : 

![Capture d'écran 2025-02-20 140110.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202025-02-20%20140110.png)

-
Utiliser les anchors points pour que les smarts masks prennent aussi effet sur les détails de volume que l'on crée dans substance (et qui ne sont donc pas bake, puisque pas de la modé) : 

Activer dans les paramètres du mask (dirt generator par exemple) les micro details, puis aller dans la micro height et mettre le anchor point du détail de height qui est dans un layer en dessous
On peut faire la même chose avec de la normal au lieu de la height

<iframe width="560" height="315" src="https://www.youtube.com/embed/HL5mZdzzgIg?si=73P5lm8xw2s43vc7" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>


## Références

Playlist complète : 
[Anchor point magic in substance 3D painter](https://youtube.com/playlist?list=PLB0wXHrWAmCxyekE6DzxfYBNYIcnFS_Ly&si=6JGYq1C7IBbAH1oU)

## Liens 




