---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Adjacency Copernicus/","tags":["note_permanente"],"dg-note-properties":{"MOC":["[[HOUDINI]]","[[Copernicus (Houdini)]]"],"source":null,"Projets":null,"tags":["note_permanente"],"creation date":"2026-09-21","aliases":null}}
---

## La note 

> [!summary] Concept Clé
> 
> Dans **Copernicus** (le moteur 2D/3D GPU de texturing et compositing de [[3_GARDEN/MOCs/HOUDINI|Houdini]]), le système d’**Adjacency** résout le problème classique des ==coutures d'UV== (_texture seams_) lors du traitement d'images sur des géométries 3D.
> 
>   

Quand on applique des filtres 2D (flous, distorsions, réactions-diffusions, bruits directionnels) dans l'espace UV classique, le calcul s'arrête brutalement au bord de chaque îlot UV.

Cela crée des ruptures géométriques et visuelles sur le maillage 3D à l'endroit exact des coutures.

**La solution de l'Adjacency :**

Le système calcule et stocke la correspondance topologique entre les pixels situés sur des îlots UV voisins. Les opérations de filtrage peuvent ainsi **traverser les coutures sans interruption visible**, agissant comme si elles opéraient directement à la surface du modèle 3D plutôt qu'en 2D.


#### ⚙️ Fonctionnement concret

Le flux de travail repose sur une connexion réseau spécifique dans Copernicus : le **==Adjacency Cable==**.

- **Génération** : Le nœud `Geometry to Adjacency COP` triangule et rastérise le maillage via son attribut UV pour générer les données topologiques de voisinage.
- **Utilisation** : Ce câble spécifique est ensuite branché dans les nœuds Copernicus compatibles pour propager de manière fluide les valeurs d'un îlot à l'autre.


#### 🧰 Nœuds et applications clés

L'Adjacency Cable débloque l'utilisation de plusieurs nœuds dédiés à la continuité de surface :

- `Distort with Adjacency` : Applique des distorsions ou des écoulements continus à travers les coutures UV.
- `Extrapolate with Adjacency` : Transfère et réoriente les données de pixels (notamment les vecteurs comme les normales ou la vélocité) sur les bordures des îlots voisins.
- `Attribute Sample with Adjacency` : Échantillonne des attributs géométriques (comme la position mondiale _P_) pour générer des textures 100% continues.
- `Space Transform with Adjacency` : Convertit et aligne les vecteurs dans l'espace tangent de manière mathématiquement cohérente à l'échelle du maillage.

> [!example] Cas d'usage : Simulations dans COPs
> 
> Grâce à l'Adjacency, les boucles itératives (comme les effets de _Reaction-Diffusion_, _Ripple_ ou les automates cellulaires) peuvent désormais simuler des dynamiques surfaciques sur l'intégralité de la géométrie **sans aucune discontinuité aux jonctions UV**.
> 
>   


## Références


> [!example]- Flashcards
> ...




## Liens 





