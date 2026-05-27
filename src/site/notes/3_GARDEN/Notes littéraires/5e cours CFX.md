---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes littéraires/5e cours CFX/","tags":["note_litteraire","cours"],"dg-note-properties":{"MOC":["[[HOUDINI]]","[[CFX]]"],"source":["[[Cours CFX ESMA]]"],"Projets":null,"tags":["note_litteraire","cours"],"creation date":"2025-11-28"}}
---




<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/3_GARDEN/Notes permanentes/Import export clean Houdini/#la-note" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">



## La note 


### Import

On cherche ici à importer correctement une geometrie pour le [[3_GARDEN/Notes permanentes/Appliquer une simu Houdini sur un mesh High poly (avec épaisseur etc)|Setup de simulation Houdini proxy to high poly]]


#### Import alembic

![Pasted image 20251128142942.png](/img/user/Pi%C3%A8ces%20jointes/Pasted%20image%2020251128142942.png)

Convert : pour que chaque primitive soit lue, et pas des primitives packées

> [!example]+ Préparer une géo avec de l'épaisseur pour simu : 
> 
> #### Exemple pour une geo type cube
> 
> *Le workflow qui suit n'est qu'un exemple*
> 
> On va enlever l'épaisseur : 
> 
> ![](https://i.imgur.com/gA9RVi7.png)
> 
> - node delete -> normal -> spread angle à 60 environ 
> - node transform : on vient venir écraser la modé : scale 0 sur z, y ou x en fonction de la mode
> - fuse : pour merge les points écrasés  
> - Remesh : quad vers triangles
> - Attribute delete : on conserve uniquement la P (position) et normal
> 
> ---
> 
> #### Exemple pour une geo type tube
> 
> *Le workflow qui suit n'est qu'un exemple*
> 
> 
>   ![](https://i.imgur.com/FfckdmR.png)
> 
> 
> 
> - For each connected pieces : Cela crée un attribut class à la valeur différente pour chaque connected piece (c'est à dire un ensemble de faces connectées entre elles)
> 	- add : on transforme la geo en points
> 	- fuse : on cherche à avoir une seule suite de points alignés -> monter un peu le snap distance
> 	- Add2 : polygon -> bygroup : construire une curve à partir des points
> 	- resample : *comme un rebuild dans maya* : lengh : 0.02
> 	- sort : reverse point sort : reverse l'ordre des points pour que le point 0 soit en haut. 
> 	- group expression : appeler le group "pin_rope" et dans le VEXpression : `@ptnum == 0;` : pour avoir un group pour chaque ptnum 0
> 	- Attribute delete : on conserve uniquement la P (position) et normal






</div></div>


---
## Vent Houdini


<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">



## La note 

Il faut rentrer dans le [[3_GARDEN/Notes permanentes/Simulation de tissu dans Houdini|Vellum Solver]] et ajouter un popwind que l'on branche à l'output FORCE

![Pasted image 20251128162221.png](/img/user/Pi%C3%A8ces%20jointes/Pasted%20image%2020251128162221.png)





</div></div>


---

## Hair


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



---

## Proxy to HIGH POLY


<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/3_GARDEN/Notes permanentes/Appliquer une simu Houdini sur un mesh High poly (avec épaisseur etc)/#la-note" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">



## La note 

Pour simuler notamment du cloth dans Houdini, on ne doit pas avoir d'épaisseur, on doit avoir un maillage en triangles, pas d'UVs etc (voir notamment : [[3_GARDEN/Notes permanentes/Import export clean Houdini|Import export clean Houdini]])

On simule donc sur un proxy puis on vient réappliquer la déformation sur le mesh d'origine

---
#### 1. Création du proxy et simulation

1. Importation et préparation du proxy : [[3_GARDEN/Notes permanentes/Import export clean Houdini|Import export clean Houdini]]
2. Simulation : [[3_GARDEN/Notes permanentes/Simulation de tissu dans Houdini|Simulation de tissu dans Houdini]] 

---

#### 2. Déformer le high poly par le proxy
###### Méthode 1 (pas ultra propre mais ça marche)

> [!abstract]+ Le point deform
> 
> ![Pasted image 20251128165654.png](/img/user/Pi%C3%A8ces%20jointes/Pasted%20image%2020251128165654.png)
> 
> Dans le timeshift : On enlève le $F (ctrl + click pour enlever) et on met seulement la frame 1 pour avoir la position de base
> 
> Le point deform vient deformer une geometrie par correspondance entre les points les plus proches de la géométrie déformée et de celle à déformer. Ainsi pas besoin d'avoir la même topo entre les 2 modés. 
> 
> Le point deform reprend donc tous les attributs etc du high poly !

###### Méthode 2 (plus propre, précise et légère)

> [!abstract]+ Node ray + attribute interpolate
> 
> ![Pasted image 20251205151031.png](/img/user/Pi%C3%A8ces%20jointes/Pasted%20image%2020251205151031.png)
> 
> Dans le timeshift : On enlève le $F (ctrl + click pour enlever) et on met seulement la frame 1 pour avoir la position de base
> 
> Node Ray : 
> Il permet de venir projeter sur les UVs la position des points du mesh simulé (c'est plus précis)
> - method : minimal distance
> - output : 
> 	- prim Num Attribute
> 	- Prim UVW Attribute
> 
> Attribute interpolate : 
> - Element Numbers Att : hitprim
> - UVW - Weights Attribute : hitprimuv
> 





</div></div>
