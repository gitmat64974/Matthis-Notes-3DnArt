---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/POP Network/","tags":["note_permanente"],"ctime":"2026-03-22T12:15:23.339+01:00","mtime":"2026-11-26T22:10:09.792+01:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/HOUDINI]]"],"source":["Houdini doc","[[3_GARDEN/Notes littéraires/Cours houdini ESMA]]"],"Projets":null,"tags":["note_permanente"],"creation date":"2026-01-27","aliases":["Popnet"]}}
---

## La note 

Le POP Network est une sorte de script pour créer la structure initiale nécessaire à la simulation de particule dans un [[3_GARDEN/Notes permanentes/DOP Houdini\|DOP Network]] 

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


### Exemple 1 : Abstract Dust around object

On entre dans popnet avec un scatter de points sur une géo

![](https://i.imgur.com/PXbwo3u.png)


Emission Type : All points
$F dans la global seed du scatter pour générer des points toutes les frames

##### Gérer les forces : POP Vop avant le merge

On va mettre un curl noise dans un premier temps
ça fait déjà un bon taff

![](https://i.imgur.com/2GhgUy0.png)

Pour sticker les points à la surface de la géo on va utiliser un SOP Solver juste après le POP Vop
A l'intérieur on va donc mettre un ray pour projeter les points du pop sur la geo (importer la geo avec un object merge)

On peut rajouter ensuite aussi un popwind pour donner plus de mouvement organique aux particules

![](https://i.imgur.com/tOP1nQp.png)

Ensuite on met un noise pour delete certaines parties et on anim le noise
on supprime tous les attributs sauf la position puis autre popnet

Le deuxième est bien plus simple on joue un peu avec des pop wind pour avoir un mouvement curlé mais doux

![](https://i.imgur.com/DlRHPhZ.png)

![](https://i.imgur.com/eGrLpti.png)

-

On peut utiliser la vitesse pour colorer les particles par la suite


## Références


> [!example]- Flashcards
> ...




## Liens 




