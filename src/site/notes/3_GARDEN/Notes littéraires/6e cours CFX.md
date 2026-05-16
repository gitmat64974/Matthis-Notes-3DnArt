---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes littéraires/6e cours CFX/","tags":["note_litteraire","cours"],"dg-note-properties":{"MOC":["[[HOUDINI]]"],"source":["[[Cours CFX ESMA]]"],"Projets":null,"tags":["note_litteraire","cours"],"creation date":"2025-12-05"}}
---



## VDB


<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">



## La note 

Volume database
Ce sont des pixels mais en 3D, presque comme des voxels 
Plein de points sont scatter sur la geo, et sur chaque point il y a une sorte de card qui suit toujours la caméra. 

On règle la résolution comme une image

Utilisation : 
- Fog 
- Combine plusieurs géo en un seul maillage


---

Dans houdini par exemple : 

Polygons to VDB : vdb form polygon
VDB to Polygons : Convert VDB -> Polygon

marche aussi avec un nuage de points au lieu de polygons en entrée : vdb from particles

---



</div></div>
 

## Groom Houdini


<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/3_GARDEN/Notes permanentes/Groom Houdini méthode lines pour vellum solver/#la-note" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">



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
> On utilise aussi le [[3_GARDEN/Notes permanentes/Simulation de tissu dans Houdini|Vellum Solver]]
> Avec dans le vellum constraint le mode hair
> Et un autre vellum constraint en attach to geo avec les group pin hair et le group de la geo d'attache (*voir [[3_GARDEN/Notes permanentes/Simulation de tissu dans Houdini|Simulation de tissu dans Houdini]] pour plus de détail sur l'attach to geometry*)



</div></div>
 


