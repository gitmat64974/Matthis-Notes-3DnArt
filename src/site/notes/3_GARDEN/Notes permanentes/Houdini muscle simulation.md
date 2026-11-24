---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Houdini muscle simulation/","tags":["note_permanente","en_cours"],"ctime":"2026-03-22T12:15:22.351+01:00","mtime":"2026-10-12T20:17:55.468+02:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/HOUDINI]]"],"source":["Houdini learning","Houdini doc"],"Projets":null,"tags":["note_permanente","en_cours"],"creation date":"2025-11-18","aliases":["Simulation de muscle dans Houdini"]}}
---

## La note 

*Préparer la géo de muscle pour la simu : [[3_GARDEN/Notes permanentes/Import export clean Houdini\|Import export clean Houdini]]*

On va utiliser le nouveau système de simulation de muscle de Houdini : Otis 
- > [Introduction to muscles and tissues](https://www.sidefx.com/docs/houdini/muscles/overview.html)

> [!abstract]+ 3 nodes appellent des recettes déjà prêtes à l'emploi dans Houdini 21 : 
> 1. ==**Test Geometry: Otto Muscle Transfer**== : permet de transférer tout le rig apex, le setup de muscle, os, tissus etc de la géometrie de test otto vers n'importe quel autre biped pas trop stylisé
> 2. ==**Test Geometry: Otto Muscle and Tissue Simulation**== : simuler les muscles et les tissus avec une configuration minimale en utilisant soit la géométrie musculaire d'Otto, soit les muscles d'Otto transférés à un autre personnage bipède
> 3. ==**Otis Muscle and Tissue Simulation**== : configuration de simulation très flexible. Idéale pour les personnages non humanoïdes ou stylisés où la recette Test Geometry: Otto Muscle and Tissue Simulation n'est pas adaptée


#### Simulation de muscle biped réaliste avec les 2 recettes otto


1. Faire le setup pour sa géo avec le ==**Test Geometry: Otto Muscle Transfer**== 
2. Connecter ensuite avec le ==**Test Geometry: Otto Muscle and Tissue Simulation :**==

![](https://www.sidefx.com/docs/houdini/images/muscles/recipe_ottosim_connectmuscletransfer.jpg)



-> Pour plus de détail voir [Test Geometry: Otto Muscle and Tissue Simulation](https://www.sidefx.com/docs/houdini/muscles/muscle_ottomuscletissuesim.html#learning) sous "Learning and using this example" 


#### Skin post processing

[Skin post-processing](https://www.sidefx.com/docs/houdini/muscles/skinpostprocessing.html)

On peut utiliser principalement 2 nodes : 
- Skin deform : pour ajouter par exemple du skin sliding etc
- Wrinkle deformer : pour ajouter facilement des plis procéduraux

---

Vieille version avec vellum  : 

> [!example]- Setup basic avec un test geo : capybara
> 
> ![](https://i.imgur.com/n2NpwlD.png)
> 



## Références

#### Ressources

Apprendre la simu de muscle avec OTIS : [MUSCLES AND TISSUE H21 - Official course](https://youtube.com/playlist?list=PLXNFA1EysfYmDwFG7GbCAfYzkSIaN-mHy&si=jnfDlvfHHUSVmbaY)

Muscle simulation avec Vellum (vieille version) :
[Muscles Masterclass \| Essentials \| SideFX](https://www.sidefx.com/muscles-masterclass-essentials/)

> [!example]- Flashcards
> 
> #houdini 
> 
> ---
> Qu'est ce que le node stash ?
> ;;
> Il permet de venir save une geo par exemple dans le projet houdini directement (sans ça, ce n'est qu'une recette). Comme un file cache ou un export alembic sauf que le fichier est directement dans le fichier houdini
> 
> ---




## Liens 




