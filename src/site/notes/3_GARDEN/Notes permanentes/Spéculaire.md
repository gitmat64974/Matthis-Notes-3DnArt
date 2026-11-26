---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Spéculaire/","tags":["note_permanente"],"ctime":"2026-03-21T20:44:30.992+01:00","mtime":"2026-04-24T17:43:18.988+02:00","dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/LIGHTING]]","[[3_GARDEN/MOCs/LIGHTING]]","[[3_GARDEN/MOCs/SHADING TEXTURING]]"],"source":null,"Projets":null,"tags":["note_permanente"],"creation date":"2024-11-26","aliases":["specular"],"Source":["[[3_GARDEN/Notes littéraires/Le rendu, google doc début d'année du prof de lighting 3D2]]"]}}
---


## La note

![premium\_photo-1673208484535-66a8f7d05294](https://plus.unsplash.com/premium_photo-1673208484535-66a8f7d05294?q=80&w=1172&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D)

C’est la lumière qui rebondit directement, la réflection découle automatiquement de ce paramètre.

*On préférera le mode physical*

Roughness étale le spéculaire simulant du micro détail (-> [[3_GARDEN/Notes permanentes/4 Niveaux de volume en CG\|4 Niveaux de volume en CG]]).

##### Type de spec : 

Beckman : organique (peau humaine, eau...etc).
Ggx : Industriel (simule des micros rayures)

Réfraction : Coefficient Fresnel. Plus la face d’un objet se trouvera parallèle à l’axe du regard plus la reflection sera net et visible
Un diélectrique tourne autour de 1.5 
Un métal peut aller jusqu’à 3 mais n’a pas de [[3_GARDEN/Notes permanentes/Diffuse\|Diffuse]].
Extinction Coeff : de 1 à 3 pour les métaux.
On peut teindre le spec color pour avoir différent type de métal. La librairie Renderman peut faciliter.

Très important aussi comme paramètre : [[3_GARDEN/Notes permanentes/Indice de réfraction\|Indice de réfraction]]
##### anisotropie

Le spéculaire dépend du “brossage” de la matière, très utilisé pour les objets industriels.  
Fonctionne avec la roughness.  
  
Un PXR tangent field dans L’Input Rotation avec des vector Maps pour brosser dans différentes directions.

##### Clear Coat

Pratique pour ajouter une couche de verni
En artistique il fonctionne comme un spec. Il faut le mettre en physical pour avoir la couche qui apparait.  

Clearcoat Energy Compensation à 1 si besoin pour “nettoyer” les bordures du noir


## Références 

## Liens 
