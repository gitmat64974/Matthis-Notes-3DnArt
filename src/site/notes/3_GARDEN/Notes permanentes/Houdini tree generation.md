---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Houdini tree generation/","tags":["note_permanente"],"ctime":"2026-03-22T12:15:22.354+01:00","mtime":"2026-01-19T00:22:41.368+01:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/HOUDINI]]","[[3_GARDEN/MOCs/3D ENVIRONNEMENT ART]]"],"source":["[[3_GARDEN/Notes littéraires/Cours houdini ESMA]]"],"Projets":null,"tags":["note_permanente"],"creation date":"2026-01-05","aliases":["Generation d'arbres dans houdini"]}}
---

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

## Références

Playlist de sidefx : [Tree Generator \| SideFX](https://www.sidefx.com/tutorials/tree-generator/)
<div class="rich-link-card-container"><a class="rich-link-card" href="https://www.sidefx.com/tutorials/tree-generator/" target="_blank">
	<div class="rich-link-image-container">
		<div class="rich-link-image" style="background-image: url('https://media.sidefx.com/images/tutorial/tutorials/sidefx-labs-tree-tool/Labs_Tree_Quick_Intro.jpg')">
	</div>
	</div>
	<div class="rich-link-card-text">
		<h1 class="rich-link-card-title">Tree Generator | SideFX</h1>
		<p class="rich-link-card-description">
		The new Tree toolset available as part of SideFX Labs can be used to create many different tree shapes using a procedural workflow. Learn how to use the various nodes and parameters to sculpt your trees adding in variation to give them a natural look. You will also learn how to bake out the tree designs to a single polygon and either using that as a background tree in a video game or as a branch for a 3D tree.
		</p>
		<p class="rich-link-href">
		https://www.sidefx.com/tutorials/tree-generator/
		</p>
	</div>
</a></div>

C'est un peu une solution alternative à [[3_GARDEN/Notes permanentes/Speedtree\|Speedtree]]

> [!example]- Flashcards
> ...




## Liens 




