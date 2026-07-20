---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/KineFX/","tags":["note_permanente"],"dg-note-properties":{"MOC":["[[HOUDINI]]","[[RIG]]","[[ANIMATION]]"],"source":["https://youtu.be/k9i_PqjnQds?si=vm_PH3Fd1EsnKoZ4)"],"Projets":null,"tags":["note_permanente"],"creation date":"2026-03-08","aliases":null}}
---

## La note 

Le principe avec KineFX est qu'un point = un joint

Ce qui est génial avec Houdini de manière générale, c'est que tout est formé à partir des mêmes bases 

Par exemple donc une simple line peut être toutes sortes de choses : 

![Capture d'écran 2026-03-08 142242.png\|401](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202026-03-08%20142242.png)

Ce sont juste des attributs qui définissent comment cette line se comporte

#### Attributs nécessaires pour KineFX

| Name                                                                                                         | P + transform                                                                                                                                                                                    | Vertex order                                                                                                                                                                              |
| ------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ![](https://i.imgur.com/fKXIDXn.png)                                                                         | ![](https://i.imgur.com/xeKJq1x.png)<br>                                                                                                                                                         | ![](https://i.imgur.com/1OC5zqV.png)<br>                                                                                                                                                  |
| Le name est créé automatiquement avec le node skeleton, et sinon peut être créé facilement avec le rigdoctor | Il faut donc que chaque point ait une matrice de transformation (trans, rot, scale). A noter qu'on peut transformer *orient + pscale* ou *N + up + pscale* en *transform matrix* (voir plus bas) | Les vertex ont toujours un ID (numéro d'identification) et c'est cette ID qui définit la hiérarchie des joints. *Normalement ça marche tout seul automatiquement mais c'est bon à savoir* |


> [!tip]+ Orient + pscale to Tmatrix : 
> 
> ![Capture d'écran 2026-03-08 143950.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202026-03-08%20143950.png)
> 
> 1. ***Orient*** est un quaternion -> converti en matrix3
> 2. On multiplie la matrix3 par le ***pscale***
> 3. On sort un nouvel attribut ***transform***
> 
> Alternative en VEX : 
> 
> ```C
> // 1. Convertir le quaternion 'orient' en matrice 3x3
> matrix3 m = qconvert(@orient);
> 
> // 2. Appliquer le vecteur 'scale' à la matrice
> scale(m, @scale);
> 
> // 3. Assigner le résultat à l'attribut 'transform'
> // On convertit en matrix4 car l'attribut transform est généralement une 4x4
> 4@transform = matrix(m);
> ```
> 



## Références

Pour voir comment utiliser KineFX pour prendre le controle ponctuel de simulations, ou pour les driver : [[3_GARDEN/Notes permanentes/KineFX x Simulations|KineFX x Simulations]]

> [!example]- Flashcards
> #rig/KineFX
> 
> ---
> Quelle est la relation fondamentale entre un point et un joint dans KineFX (Houdini) ?
> ;;
> **Réponse**
> Dans KineFX, **un point = un joint**.
> Chaque point d'une géométrie (comme une *line*) peut représenter un joint d'un squelette, et ses attributs (ex: *transform*, *P*, *orient*) définissent son comportement (position, rotation, échelle, hiérarchie).
> <!--SR:!2026-03-20,3,250--> 
> ---
> Quels sont les **3 attributs clés** nécessaires pour qu'une géométrie (ex: une *line*) fonctionne comme un squelette dans KineFX ? Explique brièvement leur rôle.
> ;;
> **Réponse**
> 1. **`name`** :
>    - Identifiant unique du joint (créé automatiquement via *Skeleton Node* ou manuellement avec *Rig Doctor*).
>    - Exemple : `"spine_01"`, `"arm_L"`.
>
> 2. **`P + transform`** :
>    - **`P`** : Position du joint dans l'espace.
>    - **`transform`** : Matrice 4x4 combinant **translation (P)**, **rotation (orient ou N/up)**, et **échelle (pscale)**.
>    - *Alternative* : Si `transform` n'existe pas, on peut le générer à partir de `orient + pscale` (voir tip ci-dessous).
>
> 3. **`vertex order` (ID des points)** :
>    - Détermine la **hiérarchie parent-enfant** des joints.
>    - Exemple : Le point 0 est souvent la racine, le point 1 son enfant, etc.
>    - *Normalement géré automatiquement*, mais vérifiable/modifiable manuellement.
> <!--SR:!2026-03-20,3,250-->
> ---
> **Question**
> Comment convertir un attribut **`orient` (quaternion)** et **`pscale`** en une matrice de transformation (`transform`) dans KineFX ? Donne les étapes *visuelles* (nodes) **ou** le code VEX.
> ;;
> **Réponse**
> **Méthode 1 (Nodes)** :
> 4. Utiliser un **`Convert Quaternion to Matrix3`** (pour `orient`).
> 5. Multiplier par **`pscale`** via un node *Multiply* (ou *Transform Matrix*).
> 6. Sortir un nouvel attribut **`transform`** (matrice 4x4).
>
> **Méthode 2 (VEX)** :
> ```C
> matrix3 m = qconvert(@orient);  // 1. Convertir le quaternion en matrice 3x3
> scale(m, @pscale);              // 2. Appliquer l'échelle
> 4@transform = matrix(m);        // 3. Convertir en matrice 4x4 (ajoute la translation via P)
> ```
> <!--SR:!2026-06-09,1,210-->
> ---
> **Question**
> Pourquoi l'ordre des *vertex* (ID des points) est-il crucial dans un squelette KineFX, et comment est-il généralement géré ?
> ;;
> **Réponse**
> - **Rôle** : L'**ID des points** définit la **hiérarchie parent-enfant** du squelette.
>   - Exemple : Le point `0` est la racine, le point `1` son enfant, etc.
>   - Une erreur d'ordre peut casser la chaîne cinématique (ex: un bras attaché à un pied).
>
> - **Gestion automatique** :
>   - Houdini génère généralement cet ordre correctement via des nodes comme **`Skeleton`** ou **`Rig Doctor`**.
>   - *À vérifier* si la géométrie est modifiée manuellement (ex: suppression/ajout de points).
>
> - **Cas particulier** :
>   - Pour les squelettes complexes, on peut utiliser l'attribut **`parentname`** (nom du parent) pour définir explicitement la hiérarchie.
> <!--SR:!2026-03-18,1,230-->
> ---

## Liens 





