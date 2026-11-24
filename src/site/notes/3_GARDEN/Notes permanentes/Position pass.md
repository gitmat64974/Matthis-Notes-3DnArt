---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Position pass/","tags":["note_permanente"],"ctime":"2026-11-11T22:27:45.288+01:00","mtime":"2026-11-11T22:20:40.294+01:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/COMPOSITING]]"],"source":["https://youtu.be/n4YyanHkHEs"],"Projets":["[[1_PROJETS/FFE/02_PROD/RND/Recherches - Stylised rendering - FFE]]"],"tags":["note_permanente"],"creation date":"2026-11-11","aliases":null}}
---

## La note 

### Qu'est ce qu'une position pass

Une **Position Pass** (souvent appelée _World Position Pass_ ou _Point Position Pass_) est une passe de rendu où la couleur de chaque pixel représente ses coordonnées spatiales (X, Y, Z) dans la scène 3D.

Lorsqu'on active le calcule de cette passe, le moteur de rendu encode la position géométrique exacte de la surface visible dans les canaux de couleur de l'image :
- **Canal Rouge (R)** = Position sur l'axe X (gauche / droite)
- **Canal Vert (G)** = Position sur l'axe Y (haut / bas)
- **Canal Bleu (B)** = Position sur l'axe Z (profondeur)

Différents cas d'utilisation : 
- **Masks :** Isoler une zone précise de l'espace 3D (par exemple, créer une sphère de sélection autour d'un personnage) pour lui appliquer une correction colorimétrique, sans avoir besoin de recalculer des masques (ID pass ou Cryptomatte) en 3D.
- **Relighting :** Couplée à une _Normal Pass_ (qui indique l'orientation des surfaces), la Position Pass permet d'ajouter des lumières virtuelles (Point Light, Spot Light) directement au compositing.
- **Fog :** Générer du brouillard volumétrique ou de la brume qui interagit avec le volume réel des objets, offrant un résultat plus précis qu'une simple passe de profondeur (Z-Depth).
- **Projection de textures 3D :** Placer des textures, du texte, du sang ou de la salissure directement sur la géométrie d'un objet après le rendu.

---
### Utiliser une position pass (NUKE)

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




