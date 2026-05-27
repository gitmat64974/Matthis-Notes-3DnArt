---
{"dg-publish":true,"permalink":"/3_GARDEN/MOCs/CFX/","tags":["MOC"],"dg-note-properties":{"MOC":["[[HOUDINI]]","[[3D]]"],"source":["[[Cours CFX ESMA]]"],"Projets":null,"tags":["MOC"],"creation date":"2025-11-21","aliases":null}}
---

---

> [!tip]+ Derniers cours CFX : 
> 
>  | File                                                           | Date de création  | Contenu brut |
> | -------------------------------------------------------------- | ----------------- | ------------ |
> | [[3_GARDEN/Notes littéraires/13e cours CFX|13e cours CFX]] | February 13, 2026 | false        |
> | [[3_GARDEN/Notes littéraires/11e cours CFX|11e cours CFX]] | January 23, 2026  | false        |
> | [[3_GARDEN/Notes littéraires/10e cours CFX|10e cours CFX]] | January 16, 2026  | false        |
> | [[3_GARDEN/Notes littéraires/9e cours CFX|9e cours CFX]]   | January 09, 2026  | true         |
> | [[3_GARDEN/Notes littéraires/8e cours CFX|8e cours CFX]]   | December 19, 2025 | false        |
> | [[3_GARDEN/Notes littéraires/7e Cours CFX|7e Cours CFX]]   | December 12, 2025 | false        |
> | [[3_GARDEN/Notes littéraires/6e cours CFX|6e cours CFX]]   | December 05, 2025 | false        |
> | [[3_GARDEN/Notes littéraires/5e cours CFX|5e cours CFX]]   | November 28, 2025 | false        |
> | [[3_GARDEN/Notes littéraires/4e cours CFX|4e cours CFX]]   | November 07, 2025 | false        |
> | [[3_GARDEN/Notes littéraires/3e cours CFX|3e cours CFX]]   | October 24, 2025  | false        |
> | [[3_GARDEN/Notes littéraires/2e cours CFX|2e cours CFX]]   | October 17, 2025  | true         |
> | [[3_GARDEN/Notes littéraires/1er cours CFX|1er cours CFX]] | October 10, 2025  | false        |
> 
{ .block-language-dataview}
> 

# Ressources


# MOC
---

[[3_GARDEN/Notes permanentes/Wrangle d’animation périodique|Wrangle d’animation périodique]]

[[3_GARDEN/Notes permanentes/Node point deform|Node point deform]]
[[3_GARDEN/Notes permanentes/Node group Houdini|Node group Houdini]]
[[3_GARDEN/Notes permanentes/HDA|HDA]]

---
## Workflow simulation de tissu



<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/3_GARDEN/Notes permanentes/Appliquer une simu Houdini sur un mesh High poly (avec épaisseur etc)/#la-note" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">

<div class="markdown-embed-title">

# Setup de simu Houdini proxy to high poly

</div>


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



Voir aussi : 
- [[3_GARDEN/Notes permanentes/File Cache|File Cache]]
- [[3_GARDEN/Notes permanentes/Node Attribute VOP|VOP]]


[[3_GARDEN/Notes permanentes/Simulation de tissu dans Houdini|Simulation de tissu dans Houdini]]
	[[3_GARDEN/Notes permanentes/File Cache|File Cache]]

[[3_GARDEN/Notes permanentes/Node Attribute VOP|Node Attribute VOP]]

---

## Groom 

Voir : [[3_GARDEN/MOCs/GROOM|GROOM]]

---

## Crowd

[[3_GARDEN/Notes permanentes/Crowd|Crowd]]
[[3_GARDEN/Notes permanentes/Crowd Houdini|Crowd Houdini]]