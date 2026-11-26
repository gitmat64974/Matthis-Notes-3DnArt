---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/MPM Solver/","tags":["note_permanente"],"ctime":"2026-09-17T18:41:12.360+02:00","mtime":"2026-11-26T22:17:06.443+01:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/HOUDINI]]"],"source":null,"Projets":null,"tags":["note_permanente"],"creation date":"2026-09-17","aliases":null}}
---

## La note 

Comment utiliser le MPM Solver d'Houdini : 

![Capture d'écran 2026-09-17 184039.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202026-09-17%20184039.png)

On connecte donc nos géos qu'on veut simuler à des MPM Source (l'entrée peut être de la géo ou du vdb qu'importe, dans tous les cas le node transforme en VDB) qui iront dans un MPM solver

Idem avec les sources de collisions si il y en a qui iront dans un mpm collide

Le MPM Solver doit avoir obligatoirement un container connecté

Ensuite on récupère et transforme les particules simulées en géo avec le mpm surface


#### Applicatif très simple : simuler un brownie

![](https://i.imgur.com/byI1i9T.png)

1. Je fais une base de brownie très simple avec des noise

![](https://i.imgur.com/bRUvhP9.png)

2. Je crée les pépittes de chocolat 

![](https://i.imgur.com/uLhJ8Kw.png)

3. Je crée un émetteur pour la sauce : une sphere qui va être animée selon une spirale 

![](https://i.imgur.com/ZdDdB6x.png)

4. On merge tout ça et on prépare à la simu chaque partie avec les mpm source. Réglage des MPM Source 
	1. brownie : chunky
	2. pepittes : viscous
	3. cream : viscous (avec très très peu de viscosity)


![](https://i.imgur.com/AaSyPFe.png)


5. On setup son collider et le MPM Solver

![](https://i.imgur.com/anCoaNn.png)

6. On extrait et converti chaque élément en géo

![](https://i.imgur.com/HX9aNbA.png)




## Références


> [!example]- Flashcards
> ...




## Liens 




