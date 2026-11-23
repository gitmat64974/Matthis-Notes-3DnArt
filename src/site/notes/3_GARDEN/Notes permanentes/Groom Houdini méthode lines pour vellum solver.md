---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Groom Houdini méthode lines pour vellum solver/","tags":["note_permanente"],"ctime":"2026-03-21T20:44:38.615+01:00","mtime":"2026-04-06T00:01:03.000+02:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/HOUDINI]]","[[3_GARDEN/MOCs/GROOM]]"],"source":["[[3_GARDEN/Notes littéraires/6e cours CFX]]","[[3_GARDEN/Notes littéraires/5e cours CFX]]"],"Projets":null,"tags":["note_permanente"],"creation date":"2025-11-28","aliases":null}}
---

## La note 



#### Création des curves de base


> [!abstract]+ Duplication de curves préparées pour la simu sur une géo
> 
> ![Pasted image 20251205162442.png](/img/user/Pi%C3%A8ces%20jointes/Pasted%20image%2020251205162442.png)
> 
> Line : 
> - direction : 0,0,1
> - length : 0.2
> - points : 20
> 
> Node group expression
> ***Avec le node group expression, on vient définir un groupe correspondant au point 0, point qui sera le point pin attaché à la géo pour chaque curve :*** 
> 
> - Group type : points
> - Group name : pin_hair
> - VEXpression : ``@ptnum ==0;``
> 
> Scatter : *scatter des points sur la géo qui vont servir de points de duplication de la curve d'origine avec le copytopoint*

##### Simu groom 

Après avoir bien préparé les curves pour la simu (voir plus haut, surtout le group expression pour l'attach), on vient les simuler. 

> [!abstract]+ Vellum solver et constraints
> On utilise aussi le [[3_GARDEN/Notes permanentes/Simulation de tissu dans Houdini\|Vellum Solver]]
> Avec dans le vellum constraint le mode hair
> Et un autre vellum constraint en attach to geo avec les group pin hair et le group de la geo d'attache (*voir [[3_GARDEN/Notes permanentes/Simulation de tissu dans Houdini\|Simulation de tissu dans Houdini]] pour plus de détail sur l'attach to geometry*)


## Références


> [!example]- Flashcards
> ...




## Liens 




