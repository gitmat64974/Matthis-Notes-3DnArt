---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes littéraires/Cours Houdini semaine 10/","tags":["note_litteraire","cours"],"dg-note-properties":{"MOC":["[[HOUDINI]]"],"source":["[[Cours houdini ESMA]]"],"Projets":null,"tags":["note_litteraire","cours"],"creation date":"2026-01-05"}}
---

---

## Houdini tree generation



<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/3_GARDEN/Notes permanentes/Houdini tree generation/#la-note" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">



## La note 

<iframe title="vimeo-player" src="https://player.vimeo.com/video/491376755?h=d47b6dc3e9" width="640" height="360" frameborder="0" referrerpolicy="strict-origin-when-cross-origin" allow="autoplay; fullscreen; picture-in-picture; clipboard-write; encrypted-media; web-share"   allowfullscreen></iframe>


Workflow dans l'ordre : 

- tree controller
- tree trunk generator
- tree branch generator
- tree leaf generator


> [!info]+ Tree controller
> Le tree controller permet de gérer tout un tas de paramètres généraux de l'arbre
> Par exemple le randomize est très utile pour avoir plusieurs versions d'un même arbre
> 
> la doc : [Labs Tree Controller](https://www.sidefx.com/docs/houdini/nodes/sop/labs--tree_controller.html)

### Tree trunk

Le tree trunk est un gros node qui permet de faire pas mal de choses sur le tronc

> [!abstract]+ Quelques paramètres : 
> - General
> 	- Contrôler le radius et le radius en fonction de la hauteur
> - Tropism
> 	- Bend 
> 	- Thigmotropism : Plie et déplace le tronc pour contourner / envelopper une geo
> - Trunk shape : 
> 	- Gérer les racines
> 		- shape ramp : forme
> 		- position ramp : jusqu'à quelle hauteur les racines influencent le tronc
> 		- roll / twist : effets d'enroulement
> - Meshing 
> 	- Gérer notamment les endcaps
> - Resolution : 
> 	- Gérer la résolution
> - Displacement : 
> 	- Utiliser une map de displacement pour ajouter des détails réalistes
> - Visualisation : 
> 	- Appliquer une couleur à des fins de visualisation

> [!tip]+ On peut venir controler le tronc avec une curve : 
> 
> ![Pasted image 20260105205908.png](/img/user/Pi%C3%A8ces%20jointes/Pasted%20image%2020260105205908.png)
> 
> resample : cocher curve U (attribute pour avoir l'information de placement de points sur la courbe)
> attribute noise : 
> - Blend : Use attribute
> - blend attribute : curveu
> - attribute names : P

### Tree branch generator

Quelques paramètres : 

##### Inclinaison : 
- Angle : inclinaison des branches
	- Angle ramp : inclinaison en fonction de la hauteur des branches

##### Longueur : 
- Length
	- Length ramp : longueur en fonction de la hauteur (par défaut le ramp est défini de manière à couper les branches trop proches du sol)

##### Tropism 

**Séries de controles pour gérer la directionnalité des branches :**

- Bend Along Parent : Fait plier la branche le long de l'axe de sa branche parente
- Gravitropism : Fait plier la branche selon l'axe de la direction spécifiée afin de simuler la gravité
- Phototropism : Plie la branche selon l'axe de la direction spécifiée pour simuler la croissance vers la lumière
- Thigmotropism : Plie et déplace les branches pour contourner / envelopper une geo

Plus d'infos dans la doc : [Labs Tree Branch Generator](https://www.sidefx.com/docs/houdini/nodes/sop/labs--tree_branch_generator.html)



---


</div></div>
