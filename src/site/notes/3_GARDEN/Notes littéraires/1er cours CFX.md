---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes littéraires/1er cours CFX/","tags":["note_litteraire","cours"],"dg-note-properties":{"MOC":["[[HOUDINI]]","[[CFX]]"],"source":["[[Cours CFX ESMA]]"],"Projets":null,"tags":["note_litteraire","cours"],"creation date":"2025-10-10"}}
---


### Wrangle d’animation périodique 


<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/3_GARDEN/Notes permanentes/Wrangle d’animation périodique/#la-note" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">



## La note 

```C
@P.y += sin(1 + $F * chf("period")) * chf("amplitude") + chf("amplitude");
```

Ce wrangle fait bouger l’objet en entrée de haut en bas selon une fonction sinusoïdale en fonction des paramètres période et amplitude qu’il crée (-> crée donc 2 glissières période et amplitude)



</div></div>
 

### Node point deform


<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/3_GARDEN/Notes permanentes/Node point deform/#la-note" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">



## La note 

Permet de transférer l’anim d’un objet à un autre par exemple

Exemple : On transmet l’anim de la sphère faite avec le wrangle précédent sur la créature gonflable 

![IMG_1292.png](/img/user/Pi%C3%A8ces%20jointes/IMG_1292.png)



</div></div>
 

### Vélum constraint 


<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/3_GARDEN/Notes permanentes/Simulation de tissu dans Houdini/#la-note" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">



## La note 

### Le Vellum Solver

Node pour créer toutes sortes de simulation de tissu

Node velum constraint d'abord pour définir les paramètres physiques de l'objet
Lui attacher un vellum solver juste après

Simu très simple : 

On a un collider : plane + geo de test
Et un drap que l’on met assez haut et que l’on a duppliqué avec un copy and transform (équivalent du shift D dans Maya)

![IMG_1293.png](/img/user/Pi%C3%A8ces%20jointes/IMG_1293.png)


> [!tip] Plusieurs choses à savoir
> Le cloth gère mieux les triangles que les quads 
> 
> Les colider doivent être toujours clean, pas de ngons etc et fermés (pas de trous)

Ajouter du vent : [[3_GARDEN/Notes permanentes/Vent simu cloth Houdini|Vent simu cloth Houdini]]
#### Paramètres

<iframe width="560" height="315" src="https://www.youtube.com/embed/F38QtWoWQ7k?si=z7raFethnOBkT5km" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
Friction : Dans le solver -> Forces -> Friction -> Dynamic scale

### Vellum constraint 

Différents types : cloth, hair, attach, pressure etc
Souvent on les combine (voir plus bas pour le cloth, attach etc)

#### Pressure

![Pasted image 20251205145054.png](/img/user/Pi%C3%A8ces%20jointes/Pasted%20image%2020251205145054.png)

Le pressure va conserver le volume d'air qu'il y a à l'intérieur de la géo : faire des ballons gonflables par exemple

- On peut gérer le rest lenght scale pour faire gonfler ou aspirer par exemple

### Pour avoir plusieurs geo de cloth qui interagissent : 

![Capture d'écran 2025-11-21 212432.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202025-11-21%20212432.png)

### Exemples concrets simples : 
##### Attacher une jupe à un personnage

![IMG_1322.png](/img/user/Pi%C3%A8ces%20jointes/IMG_1322.png)

2 Constraints : une en cloth et une en attach to geometry (rien à mettre de plus)

Dans la contrainte attach : 
Geometry : 
- Group type : points
- Group : pin_jupe (group de points défini plus haut avec une bounding box)

Target geometry : 
- Target group points : points
- Target group : in_body (group de points défini plus haut avec une bounding box)

##### Ajouter une poche sur un tissu

![IMG_1323.png](/img/user/Pi%C3%A8ces%20jointes/IMG_1323.png)

Group : sélectionner des points: 
- Appuyer sur flèche à côté de base group 
- Sélectionner les points
- Touche Entrer

Process : 
On fait 2 grid : une qui simule la veste et une qui sera la poche

On défini les points d’attache de la poche (toutes les bordures sauf celle du haut) avec un group 

Ici pour la veste, on fait 2 group : 
1. Un qui prend seulement la bordure du haut (pour la simu de cloth de cette grid qui fait office de veste)
2. Un qui prend tous les points (pour attacher la poche à la veste)

On a 2 vellum constraints : 
1. Un en cloth avec comme paramètres : 
	1. Pin to animation -> pin points -> pin (bordure du haut de la veste)
2. Un en bleu avec comme paramètres : voir capture d’écran

##### Déchirer la poche


> [!NOTE]+ Animation
> On ajoute : 
> 
> Transform : 
> - Animé, il va faire partir la poche assez loin de la veste (simple translation)
> 
> Group : 
> - Name : pin_anim
> - On sélectionne seulement quelques points sur la partie de haute de la poche pour simuler la main qui tire la poche
> 
> Modification du premier vellum constraint : 
> - Pin points : ajouter pin_anim
> - Cocher match animation 


> [!Abstract]+ Déchirer la poche
> Dans le vellumconstraint glue : 
> Onglet Breaking : 
> - activer
> - Threshold : baisser pour « déchirer » plus
> - Type : stretching distance




</div></div>
 


