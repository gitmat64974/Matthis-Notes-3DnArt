---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes littéraires/Comfyui video playlist 3d war, la 3d facil/","tags":["note_litteraire"],"dg-note-properties":{"MOC":["[[ComfyUI]]","[[IA]]","[[3D]]"],"source":["https://youtube.com/playlist?list=PLqGABQyVhJJqv3lxSYBYqYh8vQ6_yxZ_g&si=54MBC2lBKA-yVeiu"],"Projets":null,"tags":["note_litteraire"],"creation date":"2025-08-02"}}
---


# Playlist 1 

## Modèle checkpoint

- Il s'agit d'un modèle d’IA qui a été entièrement entraîné sur un type d’image ou un style précis (par exemple, uniquement des images de Star Trek).
- Ce modèle excelle dans la génération d’images selon ce style particulier et produit des résultats très cohérents et fidèles à son « univers ».
- Par contre, il peut être lourd (en taille) et manque de polyvalence : il ne connaît que son style entraîné.

## Modèle Lora

- Un Lora (***Lo**w **RA**nk adapter*) est un « mini-modèle », plus léger, que l’on ajoute par-dessus un gros modèle généraliste.
- Il est entraîné sur un petit set d’images (parfois seulement 50) pour injecter un style ou modifier l’output d’un modèle généraliste.
- Pour activer un Lora dans un prompt, il faut ajouter un « **trigger word** » (mot déclencheur) dans la description pour que ComfyUI applique le style voulu du Lora.
- Les résultats sont plus variables et dépendent fortement de la qualité du Lora utilisé — ils sont parfois moins cohérents qu’avec un modèle spécialisé ([[Modèle checkpoint|Modèle checkpoint]]), surtout si le set d’entraînement du Lora était petit ou peu varié.
- En revanche, les Lora sont rapides à entraîner et à appliquer, ce qui permet de facilement personnaliser ou tester plusieurs styles.

En trouver par exemple sur [Civitai: The Home of Open-Source Generative AI](https://civitai.com/)
#### Utiliser un Lora dans comfyUI

Il faut simplement mettre un load Lora juste après le load checkpoint

![Capture d'écran 2025-08-02 091245.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202025-08-02%20091245.png)

Ici le trigger word (dans le prompt, pour appeler le Lora) est style of 80scartoon

## Controlnet

#### L'image-to-image

L e principe de l’image-to-image : 
on fournit une image de base et l’IA en génère une nouvelle en tenant compte du texte fourni, tout en restant proche (ou non, selon le « denoise ») de la structure d’origine. Plus la valeur de « denoise » est basse (ex : <0,5), plus l’image générée sera fidèle à l’image d’entrée.

Cependant, même en image-to-image, l’ajout d’un Lora peut provoquer une « hallucination », c’est-à-dire des altérations imprévues (ex : des objets modifiés ou déplacés). 

#### ControlNet

Modèle qui va interpréter l'image entrante via des « préprocesseurs » pour en créer des sortes d'"[[3_GARDEN/Notes permanentes/AOV|AOV]]". 

![Capture d'écran 2025-08-02 094522.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202025-08-02%20094522.png)

Exemple : 

| ![Capture d'écran 2025-08-02 100442.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202025-08-02%20100442.png) | ![Capture d'écran 2025-08-02 100424.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202025-08-02%20100424.png) |
| ------------------------------------------ | ------------------------------------------ |
| ![Capture d'écran 2025-08-02 100618.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202025-08-02%20100618.png) | ![Capture d'écran 2025-08-02 100750.png](/img/user/Pi%C3%A8ces%20jointes/Capture%20d'%C3%A9cran%202025-08-02%20100750.png) |

#### Solution la plus simple : ControlNet tout en un avec le model promax

![Pasted image 20250803003308.png](/img/user/Pi%C3%A8ces%20jointes/Pasted%20image%2020250803003308.png)




## Mask dans ComfyUI


![](https://i.imgur.com/26JPP17.png)

Clic droit sur une image : 
- Open in sam detector : detecteur automatique des zones -> clic gauche élément à ajouter, clic droit élément à enlever
- Open in mask editor : peindre le mask à la main, peut s'utiliser en combinaison du sam detector

#### Mask Prompt

<div class="youtube-embed"><iframe src="https://www.youtube.com/embed/FDo3-TqAu2g" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe></div>



## CG to AI avec ComfyUI

Mettre son rendu, layout dans un control net et en latent image pour plus de fidélité
Detect **canny** (pour detect les objets, les ombres donc le lighting etc) et **depth** (on peut aussi mettre sa passe de zdepth, attention à l'inverser): voir [[Controlnet|Controlnet]] 


## Inpainting ComfyUI

![](https://i.imgur.com/8BazTXH.png)

Premièrement installer (depuis le manager) :

- **comfyui_controlnet_aux**
- **ComfyUI-Advanced-ControlNet,** celui ci sert à mieux gérer les controlnetUnion
- **ComfyUI_LayerStyle** : Il peut servir à pas mal de trucs, notamment à travailler en "couches" comme sur photoshop, mais dans notre cas, il va juste servir à retirer la couche alpha de notre image

Workflow classique d'inpainting : 

![Pasted image 20250803003741.png](/img/user/Pi%C3%A8ces%20jointes/Pasted%20image%2020250803003741.png)

Le workflow json : 
![[inpainting.json]]

