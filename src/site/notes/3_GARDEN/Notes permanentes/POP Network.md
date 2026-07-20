---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/POP Network/","tags":["note_permanente"],"dg-note-properties":{"MOC":["[[HOUDINI]]"],"source":["Houdini doc","[[Cours houdini ESMA]]"],"Projets":null,"tags":["note_permanente"],"creation date":"2026-01-27","aliases":["Popnet"]}}
---

## La note 

Le POP Network est une sorte de script pour créer la structure initiale nécessaire à la simulation de particule dans un [[3_GARDEN/Notes permanentes/DOP Houdini|DOP Network]] 




> [!tip]+ 2 méthodes de génération des particules : impulse et constant
> - **Impulse** : nombre de particules générées toutes les frames
> - **Constant** : nombre de particules générées pour 24 frames (une seconde)
> 
> <u>Dans l'onglet birth : </u>
> 
> ![Pasted image 20260127114956.png](/img/user/Pi%C3%A8ces%20jointes/Pasted%20image%2020260127114956.png)
> 
> 
> 
> *Impulse activation* : activer le mode impulse
> *Impulse count* : nombre de particules générées à chaque frame
> 
> *Const activation* : activer le mode constant
> *Const birth Rate* : nombre de particules générées pour 24 frames


#### Collision

Il est préférable d'avoir la geometrie et une version vbd : 

![Pasted image 20260127121301.png](/img/user/Pi%C3%A8ces%20jointes/Pasted%20image%2020260127121301.png)

Setup le collider dans le pop net : 

![Pasted image 20260127121728.png](/img/user/Pi%C3%A8ces%20jointes/Pasted%20image%2020260127121728.png)

Static object : on import la geo et la geo proxy (vdb) 

Le merge vient créer une relation entre 2 solver, l'input de gauche impactant la simu de droite


#### POP Streams

[Streams](https://www.sidefx.com/docs/houdini/dopparticles/streams.html)

Ce sont des groups de particules (plus efficaces que le POP group node) 
En regardant les infos du solver, on peut voir tous les groups de particules existants

POP Collision behavior : 
Ce node permet d'assigner un group au particules qui entrent en collision
Il permet également de leur assigner un comportement de base (die, stick etc)
-> A mettre après le POP Source

![Pasted image 20260127143906.png](/img/user/Pi%C3%A8ces%20jointes/Pasted%20image%2020260127143906.png)

Pop Stream : permet de récupérer le group (ou en créer un directement)
Pop replicate : permet de duppliquer les particules et de gérer leur comportement
- Birth : tous les paramètres de birth comme dans le POP Source
- Shape : gérer la forme que la duplication suit
	- Uniform scale : permet de rapprocher ou éloigner les particules dupliquées de leur particule d'origine (sur la capture d'écran le uniform scale est à 0.1)




## Références


> [!example]- Flashcards
> ...




## Liens 




