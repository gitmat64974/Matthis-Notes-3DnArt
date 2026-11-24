---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Fill layer, masks et filtres (substance painter)/","tags":["note_permanente"],"ctime":"2026-04-06T00:00:57.000+02:00","mtime":"2026-04-24T17:43:18.702+02:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/SUBSTANCE PAINTER]]"],"source":["[[3_GARDEN/Notes littéraires/Substance painter getting started]]"],"Projets":null,"tags":["note_permanente"],"creation date":"2024-08-19","aliases":null}}
---


## La note

---

> [!NOTE] Fill Layers : 

Un fill layer c’est un calque de remplissage. c’est un matériau basique enft (un peu comme un shader). il y a 2 types de calques dans substance : les paint et les fill. On utilise quasiment que les fill car ils sont plus fexibles et non destructifs, combinés à des mask, des filtres etc.

Il sont indiqués par un pot de peinture sur l’icone du calque une fois qu’il est créé.

Dans chaque fill layer se trouvent toutes les propriétés définies dans le shader comme la base color, la height (displacement), la roughness, la metallic etc

On peut glisser déposer une map 2D (perso ou du shell de substance) dans un des paramètres pour que cette map agisse en mask. Ou aussi clic droit sur le paramètre qui va ouvrir un “mini shell”. A savoir que si la projection du mask est en mode uv, la projection se fera selon les seams etc alors que si elle est en triplanar elle se fera de manière uniforme sur tout le modèle (mieux pour tout ce qui est dust, damage etc)

---

> [!abstract] Masks : 

Les masks permettent de venir limiter la zone d’action d’un fill layer ou d’un de ses paramètres comme la roughness ou la height etc. Ce sont des informations de noir et de blanc ou de gris, le blanc venant montrer, le noir venant cacher les informations. On peut utiliser un paint effect layer sur le mask pour avoir plus de possiblité comme peindre directement les uvs shells ou la geometrie ou les polygones etc.
Utiliser un grunge comme mask (map de salissure en noir et blanc) : on glisse dépose la map sur le grayscale (propriétés) d’un calque de remplissage ajouté sur un matériau ou un autre calque de remplissage (pour avoir un matériau ou une couleur de base).

---

> [!NOTE] Filters : 

Les filtres (dans ajouter un effet au calque) permettent eux d’ajouter de l’information directement comme des informations de height ou de roughness. Ce sont des effets de calques (détails, corrections comme les réglages et les filtres sur affinity) etc et on peut avoir des niveaux aussi

---

> [!example] Generators : 

Generator : ce sont des effets qui vont créer un mask (il faut donc ajouter cet effet à un black mask vierge), par exemple pour faire apparaître le calque que sur le contour des edges (type de générateur : métal edge wear), ou comme de la poussière (générateur dirt sur un calque uniforme de couleur de la poussière) etc

---
## Références 


<iframe width="560" height="315" src="https://www.youtube.com/embed/O_0Feo2NqkE?si=a42cSfwjtax8y48k" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

## Liens 

