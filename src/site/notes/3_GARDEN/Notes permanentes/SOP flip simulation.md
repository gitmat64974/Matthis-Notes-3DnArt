---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/SOP flip simulation/","tags":["note_permanente"],"ctime":"2026-03-21T20:44:19.182+01:00","mtime":"2026-03-15T18:29:00.241+01:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/HOUDINI]]","[[3_GARDEN/MOCs/FLUID SIMULATIONS HOUDINI]]"],"source":["https://youtu.be/86nbP2Q7BKA?si=nU0CD7k1KOKzd89b"],"Projets":null,"tags":["note_permanente"],"creation date":"2026-01-06","aliases":null}}
---

## La note 


Setup de base : 

![Pasted image 20260106162516.png](/img/user/Pi%C3%A8ces%20jointes/Pasted%20image%2020260106162516.png)

Flip container : conteneur de la simu (qu'on appelle aussi un tank)
- A noter que l'on peut définir une geo en entrée de ce node pour par exemple avoir une géo custom qui suit le mouvement de l'asset

Fluid compress et particlefluidsurface : pour créer de la géométrie propre après la simu

Dans le flip solver, on peut ajouter de la velocity sur un axe pour donner du mouvement initial à l'eau : waterline -> additionnal velocity

#### Emettre depuis une geo

On va utiliser le node flipboundary : 

![Pasted image 20260106172354.png](/img/user/Pi%C3%A8ces%20jointes/Pasted%20image%2020260106172354.png)


#### Mask custom de stick

Activer stick on collision dans le solver

Comment créer un mask custom ? :
On va venir créer un attribute stick custom que l'on va référencer dans les attibuts du solver et du stick on collision (control field : stick)

Attention à ce que les valeurs du stick soient bien comprises entre 0 et 1 (les valeurs négatives font l'inverse en repoussant de la collision...)

Etape 1 : On crée l'attribut, on le noise, et on le rasterize

![Capture d'écran 2026-03-15 160913.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202026-03-15%20160913.png)

Alternative avec un vdb : 

![Capture d'écran 2026-03-15 182337.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202026-03-15%20182337.png)

Etape 2 : On le référence dans le solver

![Capture d'écran 2026-03-15 174732.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202026-03-15%20174732.png)

Paramètres du sopmergefield : 

![Capture d'écran 2026-03-15 174738.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202026-03-15%20174738.png)




## Références


3 Vidéos sur le SOP flip et whitewater : 
- [HOUDINI 20 - Flip/Whitewater Sop Level Course PART 1](https://youtu.be/ZsPBU8KKqTY?si=P7RUV4ZwjBBd6Ozt)
- [HOUDINI 20 - Flip/Whitewater Sop Level Course PART 2](https://youtu.be/L-o0SEijZ7U?si=4RC4Z2WfEVPJi3TA)
- [HOUDINI 20 - Flip/Whitewater Sop Level Course PART 3](https://youtu.be/4QygfLDidH8?si=rku5okew5nh2I_95)



> [!example]- Flashcards
> ...




## Liens 




