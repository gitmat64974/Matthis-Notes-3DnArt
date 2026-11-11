---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Position pass/","tags":["note_permanente"],"dg-note-properties":{"MOC":["[[COMPOSITING]]"],"source":["https://youtu.be/n4YyanHkHEs"],"Projets":null,"tags":["note_permanente"],"creation date":"2026-11-11","aliases":null}}
---

## La note 

### Qu'est ce qu'une position pass


---
### Utiliser une position pass

Node position to points : Il va créer un point cloud dans l'espace 3D de Nuke représentant la position de chaque pixel dans l'espace, à partir des données de la position pass
Inputs : 
- Beauty
- Position
- Normal

Ce point cloud va être extrêmement utile pour placer des géométries ou des cards servant à intégrer des éléments 2D correctement dans la scène : 

On pourra rendre ces éléments 2D avec un scanline render puis les ajouter à la scène 
*Dans le node position to points mettre le render en off car on ne veut pas que la position pass se rende au scanline render, seulement les éléments 2D*

<div class="youtube-embed"><iframe src="https://www.youtube.com/embed/n4YyanHkHEs" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe></div>


## Références

#### Ressources

- [How to use the Position Pass in Nuke - YouTube](https://youtu.be/n4YyanHkHEs)

> [!example]- Flashcards
> ...




## Liens 




